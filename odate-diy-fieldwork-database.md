# Overview
Archaeology is an inherently collaborative process that happens in various places simulataneously. It is therefore often challening to ensure that archaeological databases, which serve to store and organize inter-related information obtained through various methods and practices, are kept up to date and syncronized across research environments. In order to deal with these challenges it might be necessary to set up a database hosted on a network, which would enable multiple users to simultaneously engage with the database while ensuring that the data remains orderly and complete.

In order to implement such a system we need to set up a network, set up a server, set up a database along with user-friendly interfaces, and ensure that the system is aligned with and contributes positively to the goals of the overall project.

The system that we're going to build will look something like this:
![DIY Fieldwork Database Diagram](https://github.com/zackbatist/DIYFieldworkDatabase/raw/master/DIYDatabaseDiagram.png)

It consists of:
- a local network generated and managed by a wireless router
- a Raspberri Pi mini-computer upon which the database will reside and be served to other devices across the network
- the software configured to host the database and ensure that the data is secured and backed up
- user interfaces that talk to the database and that encourage desired user behaviour
- other useful services such as a file sharing server and data visualization portal that may help encourage collaborative and informed research

The system that we're going to build may be suitable for some, but not for others. It is therefore important to remember that this all requires some degree of flexibility so that what you make suits the overall goals of the project you're contributing to. So you may copy these instructions directly or tinker around to suit your needs!

## Some Notes on Hardware
This is meant to be a very portable, low energy use and inexpensive setup. While I recommend that you use a dedicated server - a computer that is configured to run the database server, and only the database server - you can actually host the database on a regular laptop that you also serves as the client. I will be including notes on how to configure this to work all on one device, but I recommend that you use this kind of setup for educational and testing purposes only, and not in a production environment.

Raspberry Pi is available online for around 45$ CAD at https://www.raspberrypi.org/products/, but your local makerspace will likely be happy to lend you one to play with. You will also need a SD card with a capacity of at least 8GB and with adequate read/write speeds (see https://www.raspberrypi.org/documentation/installation/sd-cards.md for more info), a wireless router (this one is 40$ and tiny - perfect for portability! https://amzn.to/2HoOM6W), a power source that is capabale of high-ampage output of at least 2.4A (a wall socket will suffice, but in the field I recommend an external battery pack to be used, to allow for increased portability and as a safeguard against power failures - I use this one at 43$: https://amzn.to/2Ht8quv) and a couple USB flash drives with varying storage capacities that suit your needs.

This guide is designed with unix-users in mind - so those who use MacOS or Linux. Sorry Windows users :(

# Networking Basics
The goal of this project is to enable multiple computers to communicate with a database on a central server. In order to accomplish this we first need to set up a network, which enables this communication to happen. **A network is a set of interconnected computers, which communicate with each other using cables or wireless connections as well as protocols that manage the connections.**

The internet is one kind of network that relies on immense cabling infrastructure and DNS protocols that have global reach (DNS, or Domain Name Servers, distribute codes to every computer on the internet, which are comparable to phone numbers in a phone network). However in our case we are going to set up a local network (also known as a local area network, LAN or intranet) that has a limited scope and range. **A local network distributes IP addresses to connected devices that enable them to communicate with each other, but it does not necessarily connect these computers to the outside world of the internet.** It can be imagined as a neighbourhood with roads and walkways of its own that serve the local community; the neighbourhood may be connected to the rest of the world via a regional or national highway. **The local network is managed by a router, which is a specialized computer that assigns local IP addresses and also helps direct traffic to and from the broader internet.** You can think of the router as a local post office, which receives mail directed to the town and distributes the mail to every household.

Other kinds of specialized buildings might exist in the town as well. You might do all sorts of things in your home, such as cook, water the garden, wash the dog, or host a party, which each consume varying degrees of food and water (including some waste) but services like grocery store or water reclamation plants need to be streamlined and focused in order to keep up with the inflow and outflow of material that they need to process, which is immense because they engage with each and every household in town. These represent specialized computers on a network called servers (also referred to as hosts, clusters or 'the cloud'). **Servers are centralized computers that manage and distribute information to and from clients across the network. They are designed to be as lightweight and efficient as possible,** such as by minimizing flare in user interfaces to enable more effective use of computing resources directed towards the task at hand, or by keeping the temperature cool to prevent shutdowns and slowdowns due to overheating. The hardware places hard limits on how efficient a computer may operate, but configuring the software can go a long way in stretching a computer's capabilities.

Finally, **a user (also referred to as a client, terminal or workstation) is any other computer on the network that is served information or passes along information to be served to others.** The things that they do on their own computer are local relative to other computers on the network. The terms 'local' and 'remote' are therefore commonly used to designate things that occur close to home base, and things that occur further away, respectively.

# Raspberry Pi and Raspbian
- Raspberry Pi has its own Linux Distribution designed to be lightweight and consume less power
- it is often run headless, or without an external monitor, keyboard and mouse
- encourage them to use the command line
- Raspbian is extremely easy to install and reinstall
- the operating system resides on a SD card
- show how the OS is set up, including ssh and wpa_supplicant setup
- show them how to install updates
- show them how to install new software (use tightvnc as an example maybe)
- show them how to SSH
- show them how to configure a static IP address
- include or reference a cheat sheet with basic terminal commands
- show them around certain directories (/etc) and encourage them to ask the community for help
- show them how to shut down the Raspberry Pi

# Multi-User Databases
- I mentioned how servers have both hardware and software components, now is the time to configure the software
- explain how MariaDB is a fork of MySQL, but pretty much everything is the same
- explain that the database resides on the SD card, and that users can connect to it remotely with the following information: the server's IP address, the port that is used by MariaDB, the name of the database, and login credentials
- so let's install MariaDB Server
- let's login as root
- let's create a database
- let's create a user and grant permissions
- let's create tables
- explain indexes and primary keys
- let's insert data to the tables
- let's select data from tables
- let's update data from tables
- let's make relationships among tables
- let's join data from multiple tables
- let's delete data from tables
- do all this from the command line but show how it can also be done from a GUI like Sequel Pro or SQL Workbench, which actually shows the queries being run

# Client side stuff
- explain ODBC (it's a driver that translates across database management systems (DBMSs))
- show how they would connect to the database from MS Access (setup ODBC and DSN, Linked Table Manager, creating forms in Access, etc)
- show that in certain cases ODBC is not necessary, such as when using R Shiny since the data is being entered directly rather than passed along through an intermediary DBMS such as MS Access
- link down to a permalink explaining the R Shiny app in more detail

# Other bits and bobs
- automatic scheduled backups
- SMB file sharing
- R Shiny frontends

# Tinkering and Improvising in the Field
- working in multiple locations without any internet connection (and sqldump workaround)
- ensure that people, especially higher up, understand the constraints and limitations you face
- show people rather than tell
- be respectful of their data and devices
- power outages and working off-grid
- migrating to the cloud and back
- keep notes, watch your posture, etc

# Discussion

# Takeaways

# Excercises

# Further Reading

## Installing Raspbian
Insert microSD card into the adapter and insert into a laptop.

Format the microSD card as FAT32 using an SD Card Formatter tool (https://www.sdcard.org/downloads/formatter_4/).

Etch the Rasbian disk image to the SD card using Etcher (https://etcher.io/). Raspbian is available at the Rasoberry Pi downloads page (https://www.raspberrypi.org/downloads/raspbian/).

Configure the OS to enable SSH on first boot.
```
touch /Volumes/boot/ssh
```

Add network info to enable immediate connection to the network.
```
touch /Volumes/boot/wpa_supplicant.conf
cd /Volumes/boot
nano wpa_supplicant.conf
```

Paste this in to ```wpa_supplicant.conf```, changing the country code, network SSID and network password to suit the situation:
```
country=CA
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="<network name>"
    psk="<network password>"
}
```

These last three steps are crucial for working headless!

Eject the microSD card, place it in the Raspberry Pi and boot it up. Wait a couple minutes for it to finish booting up. [Then SSH in](https://gist.github.com/zackbatist/48d944e73c2acf9c9e15908202cabcbf#ssh).

### Download updates
Once you SSH into the pi, update all software packages (requires internet connection).
```
sudo apt-get update -y
sudo apt-get upgrade -y
```
It is apparently not necessary to update the kernel or firmware. The most up-to-date versions are included in the raspbian disk images, and using ```sudo rpi-update``` may install bleeding-edge updates or untested firmware.

#### More info:
* https://www.raspberrypi.org/documentation/raspbian/updating.md

### Shutting down (VERY IMPORTANT!)
__NOTE: IT IS EXTREMELY IMPORTANT THAT YOU DON'T YANK THE POWER CHORD TO POWER OFF!!! THAT CAN CORRUPT THE SD CARD AND YOU'LL HAVE TO RE-IMAGE IT OVER AND OVER AGAIN! I KNOW THIS FROM MY OWN PAINFUL AND STUPID EXPERIENCE SO DON'T EVEN DARE! USE THE FOLLOWING SHUTDOWN COMMANDS INSTEAD.

TO SHUTDOWN:
```
sudo shutdown -h now
```

### More info:
* https://www.raspberrypi.org/forums/viewtopic.php?t=191061

## Setting up static IP addresses
It is necessary to set static IP addresses as fallbacks in case ```wpa_supplicant.conf``` fails. We need to do this for both wireless and ethernet interfaces.

First we need to get the Raspberry Pi's IP address on each interface:
```
pi@raspberrypi:~ $ ip -4 addr show | grep global
```

The output should look something like this:
```
    inet 169.254.39.157/16 brd 169.254.255.255 scope global eth0
    inet 192.168.0.198/24 brd 192.168.0.255 scope global wlan0
```

```eth0``` refers to the ethernet interface, and ```wlan0``` refers to the wireless interface.

Then we need to determine the router's gateway:
```
pi@raspberrypi:~ $ ip route | grep default | awk '{print $3}'
```

Should look something like this:
```
192.168.0.1
```

Then we need to determine the DNS server or namespace, which is often the same as the router's gateway:
```
pi@raspberrypi:~ $ nano /etc/resolv.conf
```

Should look something like this:
```
# Generated by resolvconf
nameserver 192.168.0.1
```

Next we have to add this information to ```/etc/dhcpcd.conf```:
```
sudo nano /etc/dhcpcd.conf
```

Add the following, substituting the IP address values for the one's that were just determined above.
```
interface eth0
static ip_address=169.254.39.157/16
static routers=192.168.0.1
static domain_name_servers=192.168.0.1

interface wlan0
static ip_address=192.168.0.198/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```

__Pro-tip:__ You may need to make a direct connection with your computer to download updates (I tend to tether my cullular connection to my laptop and share the connection over ethernet). In such cases, you will need to edit ```dhcpcd.conf``` and comment out the ```eth0``` specifications to enable an alternative ethernet interface with your laptop that is not specific to the router that it is normally connected to. You may not even need an ```eth0``` static IP, but it helps to have that direct ethernet connection in place if you are using the Pi as a network attached storage (NAS) device, i.e. sharing files over the network, as this gives a significant speed boost to file transfers.

## SSH
SSH enables you to control the raspberry pi over the local network via the command line.

In Terminal.app run the following command:
```
ssh pi@<ip address>
```

This terminal window should now be considered a remote client to the raspberry pi. Everything you do here occurs on the raspberry pi.

If you get the following warning, just go and edit ```~/.ssh/known_hosts``` and delete the key for the corresponding SSH connection. This might happen when trying to connect to a fresh install of the Raspbian OS.

Default password is raspberry.

The pi's IP address can be found in the router control panel, which can be accessed by entering the router's IP address into the browser's address bar, and entering the default username and password when prompted.

The pi's IP address, along with IP addresses for all devices connected to the network, will be listed under a page titled simething like 'DHCP client list'.

__Pro tip:__ In your router settings, under the DHCP menu, you should be able to reserve an IP address for the Raspberry Pi. Find the Pi's MAC address by running ```ifconfig``` (it's after ```ether``` under the ```wlan0``` heading), and assign it an IP towards the upper end of the range allocated to the local network. This helps keep things consistent and makes for a more efficient headless setup.

### More info:
* https://www.routerdefaults.org/tp-link/tl-wr802n
```
Router's IP address: 192.168.0.254
Username: admin
Password: admin
```

### SSH via direct ethernet connection (MacOS)
Raspbian is configured by default to receive an IP address from a DHCP server, a role that is typically fulfilled by a wireless router. This can be done without a router by configuring the sharing options in MacOS.

From System Preferences, go to the Sharing window.

From the box on the left, enable 'Internet Sharing'. You may have to select a 'Thunderbolt Ethernet' under the Wi-Fi dropdown before checking off the 'Internet Sharing' box.

In Terminal, use ```ifconfig```. Under ```bridge100```, note the IP address in the ```inet``` field, most likely ```192.168.2.1```. Add one to the final digit to determine the likely IP address of the Raspberry Pi (```192.168.2.2``` in this case).

__Note:__ This will not work if the wireless network is secured by a 802.1x firewall, which are commonly implemented by most university, hospital and government networks.

### More info:
* https://medium.com/@tzhenghao/how-to-ssh-into-your-raspberry-pi-with-a-mac-and-ethernet-cable-636a197d055
* https://www.jeffgeerling.com/blog/2016/ssh-raspberry-pi-only-network-cable-using-os-xs-internet-sharing

## Mounting a USB drive
While Raspberry Pi does support auto USB mounting when starting the machine, it can be a bit flaky. Therefore we will use the device ID to ensure that there is more certainty of a proper mount. So we need to determine the UUID of the USB device by running this command:
```
ls -al /dev/disk/by-uuid
```

and cross checking it with the devices listed after entering:
```
lsblk
```

Infer the correct UUID based on the drive's capacity and through elimination of other possibilities, and note it down somewhere.

Now create the directory where we want to mount the drive:
```
sudo mkdir /media/backup
```

Give the directory adequate permissions:
```
sudo chmod -R 777 /media/TrenchData
```

__Note:__ This command gives unrestricted read, write and execute permissions to all users! Configure your permissions to suit your needs!

Open the ```fstab``` file:
```
sudo nano /etc/fstab
```

At the end of that file, add the following command, replacing the UUID with the one pertaining to the specific device and the directory with the intended mount point:
```
UUID=783A-120B /media/backup auto noatime,nofail,umask=000 0 0
```

__Note:__ This is the correct code for FAT32 formatted drives only. FAT32 handles permissions is a slightly different way than NTFS and linux-based filesystems (i.e. ext4) and you will need to configure them accordingly. However, I recommend the use of FAT32 in general, since it is interoperable between virtually all operating systems, whereas others are not.

Now the USB drive will be auto mounted and ready to use. Don’t forget to restart your Raspberry Pi to test it out.
```
sudo shutdown -h now
```

## File sharing on a local network
Install Samba:
```
sudo apt-get install samba samba-common-bin
```
Create your shared directory:
If your intent is to share the files from an external USB storage drive, follow the instructions above to mount it.

Edit the Samba configuration file:
```
sudo nano /etc/samba/smb.conf
```

and add the following:
```
[TrenchData]
Comment = Pi shared folder
Path = /media/TrenchData
Browseable = yes
Writeable = Yes
only guest = no
create mask = 0777
directory mask = 0777
Public = yes
Guest ok = yes
```

Ensure that ```Path = ``` the directory you want to share, such as the mount point of an external drive.

This configuration allows anyone to read, write, and execute files in a volume named ```share```, either by logging in as a Samba user or as a guest. If you don’t want to allow guest users, omit the guest ok = yes line.

To set up users and passwords:
```
sudo s smbpasswd -a pi
```

I'm not certain if it is necessary for the samba user to be a user on the Raspberry Pi's filesystem.

### Then, restart Samba:
```
sudo /etc/init.d/samba restart
```

From now on, Samba will start automatically whenever you power on your Pi.

### Find your Pi on the network
You’ll now be able to find your Raspberry Pi file server (named RASPBERRYPI by default) from any device on your local network.

### More info:
https://www.raspberrypi.org/magpi/samba-file-server/

## Remote desktop
### Install TightVNC
```
sudo apt-get install tightvncserver
```

### Set up a TightVNC server
```
tightvncserver :1
```

When prompted for a password, just use the default (raspberry). It will be truncated to raspberr (8 characters) but that's fine.

When prompted if you want to set a view-only password, input 'n' for no.

### Connect to the TightVNC server remotely
MacOS has a remote desktop client built in called 'Screen Sharing.app'. Search for it using spotlight (Command + Space) or by opening a finder window and then hitting Command + K.
On Windows, you must install RealVNC (it is also available on MacOS, but I prefer the built-in app).
In either 'Screen Sharing.app' or RealVNC, paste the TightVNC server info in the address bar, formatted like this:
```
vnc://<raspberry pi IP address>:5901
```

The Raspberry Pi's IP address can be determined by SSH-ing into it and running the command ```ifconfig```, or by checking the DHCP client list on the router's control panel. It should appear as ```192.168.0.10x```, x being a replacable digit. The '1' in '5901' refers to the port to be connected to, which corresponds with the ```:1``` when setting up the vnc server.

### More info:
* http://www.penguintutor.com/linux/tightvnc

## Automated backups of MariaDB databases
### Scripting the backup
Here is a script that exports the complete data of our database and saves it as a compressed gzip file. The script also automatically affixes the archive file with the date and time of the backup (UTC time zone).

The script will be created in the home directory for simplicity’s sake:
```
cd ~
sudo nano dbbackup.sh
```
Here is the content of ```dbbackup.sh```:
```
#!/bin/bash
$OUTPUT_FILE = /media/backup/mysqldump/SNAP_$(date +"%Y%m%d_%H%M%S").gzip
$USERNAME = <MySQL username>
$PASSWORD = <MySQL password>
$DATABASE_NAME = <Database name>

sudo mysqldump -u$USERNAME -p$PASSWORD $DATABASE_NAME | gzip > $OUTPUT_FILE
```

Replace the username, password, database name and file path according to your situation. Ensure that the permissions are properly set to allow you to write to the specified directory.

Finally, we need to set the script to be executable:
```
sudo chmod 755 dbbackup.sh
```

### Making it automatic
```cron``` is a time-based scheduling utility in Unix/Linux operating systems such as Raspbian. It reads a configure file, commonly referred to as ```crontab``` where jobs are scheduled using a special syntax. To access the crontab simply enter ```crontab -e``` and add a line at the end of the file to schedule a job.

To run dbbackup.sh every 30 minutes, add the following line at the end of the crontab:
```
*/30 * * * * /home/pi/dbbackup.sh
```

### More info:
* https://www.codingepiphany.com/2013/06/12/raspberry-pi-lamp-server-tuning-and-automated-db-backup/

## MariaDB
MariaDB is essentially the same thing as MySQL. MariaDB was forked from MySQL after Oracle bought Sun Microsystems, who maintains MySQL, and there was some worry about licensing issues due to Oracle's poor reputation with regards to the maintenance and development of open source software (LibreOffice is a similar fork of OpenOffice, which was also bought by Oracle around the same time). All tutorials and online resources for MySQL are also applicable for MariaDB.

### Installing and configuring MariaDB
```
sudo apt-get install mariadb-server
```

The MariaDB configuration file needs to be modified to enable remote access to the database across the network. Access the config file:
```
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
```
Replace the ```bind-address``` from ```127.0.0.1``` to ```0.0.0.0```.

This changes the local address(es) that MySQL/MariaDB will listen to for connections on. The Raspberry Pi default is ```127.0.0.1``` for localhost only.

Save the file and restart the MySQL service:
```
sudo service mysql restart
```

#### Installing and running MariaDB locally on a MacOS
MariaDB can be installed via homebrew using the following command:
```
brew install mariadb
```

Then update homebrew, refresh the index of retrievable packages, and upgrade any installed packages:
```
brew update
brew upgrade
```

##### Starting and stopping the MariaDB server on MacOS
To start the MariaDB server:
```
mysql.server start
```

To stop the MariaDB server:
```
mysql.server stop
```

To install homebrew:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Creating a database:
```
CREATE DATABASE MY_DATABASE_NAME;
```

### Adding and configuring users
Gotta do this as the root user:
```
sudo mysql
```

Create the new user:
```
CREATE USER 'MY_USERNAME'@'localhost' IDENTIFIED BY 'MY_PASSWORD';
```

Grant the user remote access from any IP address:
```
GRANT ALL PRIVILEGES ON MY_DATABASE_NAME.* TO 'MY_USERNAME'@'%' IDENTIFIED BY 'MY_PASSWORD';
FLUSH PRIVILEGES;
```

To allow access from a fixed IP address:
```
GRANT ALL PRIVILEGES ON MY_DATABASE_NAME.* TO 'MY_USERNAME'@'12.34.56.78' IDENTIFIED BY 'MY_PASSWORD';
FLUSH PRIVILEGES;
```

#### To login as a specific user:
```
mysql -u MY_USERNAME -p
```

Input your password as prompted.

### Copy database to / from a remote server

#### Insecure method
If you have direct access to the remote server and aren't worried about security:
```
mysqldump -h [server] -u [user] -p[password] [databasename] | mysql -h [server] -u [user] -p[password] [databasename]
```

#### Secure method (SSH)
If you can SSH into the remote server you can use this:
```
mysqldump -h [server] -u [user] -p[password] [databasename] | ssh [ssh_username]@remote_domain.com mysql -u [user] -p[password] [databasename]
```

You will then be promoted for the ssh password of the remote server.

#### Copying a single table
If you want to copy only a single table, specify the tablename after the 'from' database name. If the table already exists it is overwritten.
```
mysqldump -h [server] -u [user] -p[password] [databasename] [tablename] | mysql -h [server] -u [user] -p[password] [databasename]
```

__NOTE:__ The left side is the 'from', the right side is the 'to'.  [server] can be localhost on either side.

__NOTE:__ There is NO space between -p and [password].

## Setting up MS Access as a front-end for a MariaDB backend
Download and install the Visual C++ Redistributable for Visual Studio 2015 from https://www.microsoft.com/en-ca/download/details.aspx?id=48145.

Download and install the MySQL ODBC Connector from https://dev.mysql.com/downloads/connector/odbc/.

Open the ODBC Data Source Administrator, and add a new data source under the 'User DSN' tab.

Select the MySQL ODBC Unicode Driver from the list of available drivers and include the information needed to connect to the remote database. You may need to set up a SSH tunnel using PuTTY (see below).

Give the connection a name and close both the MySQL ODBC Connector window and the ODBC Data Source Administrator.

Open a blank MS Access database. Under the 'Import & Link' subsection of the 'External Data' ribbon section, select 'ODBC Database' and choose to 'link to the data source by creating a linked table', then hit next.

In the Select Data Source window, go to the Machine Data Source tab and select the connection that was just made. Then select all the tables that you want to link with.

Linked tables have a globe icon next to their names, and all modifications to these tables are implemented on the remote server.

### Setting up a SSH tunnel using PuTTY

## Migrating from MS Access to MariaDB using MySQL Workbench

__NOTE: THIS SECTION IS STILL INCOMPLETE AND HAS EFFECTIVELY BEEN ABANDONED. ALTHOUGH FRAGMETARY, IT MAY INCLUDE SOME USEFUL INFORMATION. USE AT YOUR OWN RISK.__

### Setting up the source database
Open the database in Access. Under Database Tools, select Visual Basic. In the Immediate window type the following and then hit enter to verify whether you are Admin:
```
? CurrentUser
```

Then on the next line include the following:
```
CurrentProject.Connection.Execute "GRANT SELECT ON MSysRelationships TO Admin"
```

Close the database.

### Setting up the ODBC connection
Ensure that the MS Access drivers are installed from https://www.microsoft.com/en-us/download/details.aspx?id=54920. Ensure that the architecture is consistent with your setup.

Start the MySQL Workbench Migration Wizard, then press ```Open ODBC Administrator```.

Navigate to the 'Drivers' tab and ensure that ```Microsoft Access Driver (*.mdb, *.accdb)``` is available and installed.

Navigate to the 'User DSN' tab to create a DSN for the database file to be migrated. Press 'Add', select ```Microsoft Access Driver (*.mdb, *.accdb)```, hit 'Select' and then find the database in the directory (you may need to collapse the ```c:/``` directory by double clicking it and going into ```/Users/``` in order to find it). Give the DSN a name and then press OK to close the ODBC Data Source Administrator.

### Setting up source parameters
Select 'Start Migration' in the Migration Wizard.

The Source Selection page is where you provide the information about the Access database you are migrating from, the ODBC driver to use, and the parameters for the MS Access connection

For Database System select 'Microsoft Access'.

Connection Method should be 'ODBC Data Source'.

For DSN select the ODBC Data Source that we just created in the ODBC Data Source Administrator.

Keep the default character set.

Test the connection, and then hit 'Next'.

### Setting up target parameters
The Source Selection page is where you provide the information about the MySQL/MariaDB target database.

Under the Stored Connection dropdown select Manage Stored Collections, which should open a new window to create a new database connection.

Select 'New' and give the connection a name.

Under 'Connection Method' select ```Standard TCP/IP over SSH```.

The SSH Hostname, SSH Username and SSH Password should be the same IP address that you use to connect to the Raspberry Pi remotely. Append ```:22``` to the end of the hostname to specify the port to be used for this connection.

Keep the default MySQL Hostname and MySQL Server Port. Username and Password pertain to the specific database users doing the migration (access as root in most cases).

Then hit Test Connection.
```
SSH Hostname: <IP address>:22
SSH Username: pi
SSH Password: raspberry
MySQL Hostname: 127.0.0.1
MySQL Server Port: 3306
Username: root
Password: <root password>
```

### More info:
* https://dev.mysql.com/doc/workbench/en/wb-migration-database-access.html

## Splitting MS Access databases for shared use
