---
title: "[SOLVED] ltsp server with 2 nic cards"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by SpiritIsReality on 2007-11-01
howdy
All of the following information is available here:
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)

The LTSP server in this case is a Ubuntu 7.10 Desktop Edition, used as a desktop, with keyboard,monitor,mouse.
Please see Ubuntu Server Edition page, before you decide, here [http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)
Changes to LTSP in Gutsy [https://help.ubuntu.com/community/UbuntuLTSP/LTSPWithoutNFS](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWithoutNFS)
This network has a default gateway (the router to the internet) of 192.168.0.1
The router is set to dhcp addresses from 192.168.0.100 to 192.168.0.120
(see your router manual) to a 192.168.0.0 network.
The server is one of several computers on the 192.168.0.0 network.(other computers not shown in  image attachment)
The server needs a static eth0 address outside the range of the router's dhcp addresses.
The server has a static eth0 address of 192.168.0.140 , the cable going to the router.
The server has a static eth1 address of 192.168.1.1 , the cable leading to the switch -> to the client
______________________________________________
Preparing the Server
1.
please see attachments
2 nic cards in server
eth0 connected to router, to internet
eth1 connected to switch, to clients
eth1 closer to the edge of the motherboard, closer to the bottom of case.(reference: [http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm) )
--------------------
2.
7.10 Desktop Edition alternate install cd.
chose eth0 as nic card to use for install.

When the install starts to configure the network dhcp, cancel, or go back, and select 
manual configuration.
In this case, I entered the server address as 192.168.0.140 , and then accepted the default
netmask, gateway, and dns.
After the install,
I edited the /etc/apt/sources.list file by adding a # in front of the cdrom line.
Press and hold the ALT key, type the F2 key, release all.
Type, or cut and paste, in the run box,
```
gksudo gedit /etc/apt/sources.list
```# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
-------------
save and close file.(click File -> Save, and click File -> Quit)

 run any updates.(update icon in top panel)
System -> Help and Support -> Advanced Topics -> Installing Server Applications 
or [https://help.ubuntu.com/](https://help.ubuntu.com/)
---------------------
3.
install ltsp 
from here [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
> 
You need to set up one static interface where you will attach the thin clients, install two packages and run one command.
Configure your spare interface for the thin clients to have the IP 192.168.0.1, then follow the instructions below.
```
sudo apt-get install ltsp-server-standalone openssh-server
```
[https://wiki.ubuntu.com/EnableLTSP5LocalDevices](https://wiki.ubuntu.com/EnableLTSP5LocalDevices)
> 
To generally enable local device access you need to make sure the ltpfs package is installed on the ltsp server and the ltspfsd package is installed in the Thin client environment (usually in /opt/ltsp/i386).
(I have not done the ltpfs and ltspfsd yet)

[http://ubuntuforums.org/showthread.php?t=479555](http://ubuntuforums.org/showthread.php?t=479555)

ltsp-manager is listed in Synaptic Package Manager 
(System -> Administration -> Synaptic Package Manager)
click search, in the Search box type, ltsp and click search.  
> 
Ubuntu LTSP server management GUI
This is the LTSP GUI management tool to set up, modify and manage an
Ubuntu LTSP server Thin Client installation. It guides you through
the Thin Client chroot installation and enables you to adjust dhcp
settings on the server. It also allows you to tweak specific settings
for the Thin Clients.
I installed the recommended and suggested packages
Suggested packages:
  pulseaudio sdm audiooss nfs-kernel-server rssh molly-guard squashfs-source
Recommended packages:
  pulseaudio-esound-compat

 dh-make curl debian-keyring cvs gettext-doc nas build-essential diff-doc
  pulseaudio-utils paprefs pavumeter pavucontrol padevchooser paman
  libgstreamer-plugins-pulse0.10-0 libao-pulse rdist wmanager selectwm
Recommended packages:
  fakeroot patchutils libmail-sendmail-perl libcompress-zlib-perl
  pulseaudio-module-hal pulseaudio-module-x11 xdialog
---------------------
4.
before building the ltsp environment,
I edited the /etc/network/interfaces file like so [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
press and hold ALT key, type F2 key, release (or written as Hit ALT-F2)
type (or copy and paste)
```
gksudo "gedit /etc/network/interfaces"
```here is what I changed the file to read, and then saved the file.(click File -> Save)
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.140
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet static
    address 192.168.1.1
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
     # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1
--------------
5.
Then in terminal (click Applications -> Accessories -> Terminal) type
```
sudo /etc/init.d/networking restart
```to restart networking and create an address of 192.168.1.1 for eth1 nic card, the card that
leads to the ltsp clients. 
-------------------
6.
then I went to 
[https://help.ubuntu.com/community/LTSPServerSetup](https://help.ubuntu.com/community/LTSPServerSetup)
> 
Log in on the server with the username you created during install
Hit ALT-F2 and type (or copy and paste) the following command:```
gksudo "gedit /etc/ltsp/dhcpd.conf"
```I changed the dhcpd.conf file to look like this:
fred@piii:~$ cat /etc/ltsp/dhcpd.conf
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.5 192.168.1.20;
    option domain-name "*";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.0.254;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
---------
saved the file and closed.
----------------------------
7.
[https://help.ubuntu.com/community/LTSPServerSetup](https://help.ubuntu.com/community/LTSPServerSetup)
> 
Make sure the lines for domain-name-servers and routers match your network setup if you want to give the thin clients Internet access.
If you think all your settings are right, save the file.
Open a Terminal window (Applications->Accessories->Terminal) and run:
```
sudo /etc/init.d/dhcp3-server start
```If you made no mistakes in the above file, this command should exit with a OK message.----------------------------
and I ran > If you change the IP data after you have done the initial setup, please run the command sudo ltsp-update-sshkeys to make the ssh server aware of the change.(maybe not necessary yet)
------------------------------
from [https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)
> 
At any time that changes are made to your dhcpd.conf file, restart the server - sudo /etc/init.d/dhcp3-server restart will do it. Alternatively, every time you run the sudo dpkg-reconfigure dhcp3-server, at the end, your server will restart.
-----------------------------
8.
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
> 
Now create your Thin Client environment on the server with.

```
sudo ltsp-build-client
```------------------------------
9.
[https://wiki.edubuntu.org/ThinClientHowtoNAT](https://wiki.edubuntu.org/ThinClientHowtoNAT)
I did this much of the instructions. Your mileage may vary.
[quote]
Getting Started
*Verify that both the interfaces are configured in /etc/network/interfaces
* Check with ifconfig that both the interfaces are up.
*Verify that the server can go to the internet.

NOTE: the steps above are important! be sure to verify that everything is as it should be. It will save a lot of headaches later on. If you are not sure about the network settings, please consult your local network administrator.
*Edit /etc/network/options and enable ip_forward. The result would look like:

      ip_forward=yes
      spoofprotect=yes
      syncookies=no
and execute:
```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
```to enable the kernel ip forwarding functionality immediatly.I had to create the file /etc/network/options
```
sudo touch /etc/network/options
```If I encounter any problems, the instructions on this page will need more attention.
----------------------------------
10.
I think this is a good time for this 
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)
> 
**This workstation isn't authorized to connect to server** error message on client, please run commands **sudo ltsp-update-sshkeys** and **sudo ltsp-update-image** (in this order) 
reference: [https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/144296)(I ran it after getting the error message when trying to log into the server from an ltsp client)
--------------------------------------
11.
[https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement](https://help.ubuntu.com/community/HowToCookEdubuntu/Chapters/LTSPManagement)
I followed the chapter under the heading:
Updating your LTSP clients NFS root
> 
At some point in the future, updates will become available for your LTSP server. You must remember that altough you may have applied all the updates to the server itself, as in the instructions....HERE it is likely that the LTSP chroot will also need updating. To do this you must open up a terminal and use the following commands.
First make sure the Client environment has the same Package lists as the Server, to achieve that, you will copy the sources.list file from the Server to the Client environment.
```
sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/
```Now issue the command below.
```
sudo chroot /opt/ltsp/i386
```This will change your root directory to be the LTSP clients root directory. In essence, anything you now do inside here, will be applied to the LTSP clients NFS root. This is a seperate small set of files that are used to boot the clients into a usable, and enable them to contact the LTSP server. Once inside this shell, we must type the following command to obtain the latest list of packages from the apt servers.
```
apt-get update
```Once this has completed you will have to upgrade the software in the chroot by running the following command
```
apt-get upgrade
```Once all upgrades have finished, you must leave the chroot by either typing 'exit' or by using the key combination Ctrl+D. This will return you to the root of the server.

If your kernal has been upgraded you must run the ltsp kernel upgrade script, to ensure that your ltsp root uses the latest version. This is performed by running the command below
---------------------------------

Preparing the Client
A.
Making the Boot Floppy
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)
In this case the ltsp client will not run a ubuntu live cd.
( [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards) )
[http://www.rom-o-matic.net/5.4.1/](http://www.rom-o-matic.net/5.4.1/) for step 2.
For a boot floppy disk image select .zdsk, (To make a boot floppy)
Realtek 8139 = rtl8139:rtl8139
> 
Next select configure.
Make sure PXELOADER_KEEP_ALL is ticked, and it is a good idea to also tick POWERSAVE, ALLMULTI, MULTICAST_LEVEL1, MULTICAST_LEVEL2, and DOWNLOAD_PROTO_TFTM
When done, click get rom. 
This last step reverted the file to a previous version, but it works. If you wanted to try the latest version,
maybe skip the "configure" step, I'm not sure yet.

[http://tldp.org/LDP/Pocket-Linux-Guide/html/x185.html#AEN190](http://tldp.org/LDP/Pocket-Linux-Guide/html/x185.html#AEN190)
> 
Prepare the boot disk media
Insert a blank diskette labeled "boot disk".
Note    It may be necessary to erase the "blank" diskette if it comes factory pre-formatted for another, non-Linux operating system. This can be done using the command dd if=/dev/zero of=/dev/fd0 bs=1k count=1440
bash# mke2fs -m0 /dev/fd0
that will be
dd if=/dev/zero of=/dev/fd0 bs=1k count=1440 
sudo mke2fs -m0 /dev/fd0
(don't do the mount command)

( [http://linuxcommand.org](http://linuxcommand.org) for terminal commands )
( [https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/) )

in terminal, cd to where the floppy image is saved, then
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)
> 
The .zdsk file is a raw floppy image - on Linux you can copy it to a floppy like this:
dd if=etherboot.zdsk of=/dev/fd0
or
[http://www.rom-o-matic.net/5.4.1/](http://www.rom-o-matic.net/5.4.1/)
> 
To make a bootable floppy on a GNU/Linux system, put a formatted floppy in your floppy drive and do:
$ cat eb-5.4.1-yournic.zdsk > /dev/fd0 
where "eb-5.4.1-yournic.zdsk" is where you stored your downloaded ROM image.
(Once again, it could need the sudo in front of the commands. I try it without, and if it
doesn't like it, I run it with sudo)
--------------------------
B.
With the boot floppy in the ltsp client, and the ltsp server running, 
start the ltsp client.
---------------------

Server Configuration
12.
Customizing thin client behavior
[http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html](http://doc.ubuntu.com/edubuntu/handbook/C/ltsp-client.html)
[http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo/NetworkClients](http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo/NetworkClients)
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)
When the thin client booted, it would get to where it was trying to graphics user interface
but the xserver was too much for it, so it would quit, and try again.
I had to customize the x server to the client,
but instead of using /opt/ltsp/i386/etc/lts.conf the /opt/ltsp/i386/etc/lts.conf
file told me to: read the lts.conf file here
fred@piii:~$ cat /opt/ltsp/i386/etc/lts.conf
# This is the default lts.conf file for ltsp 5.
# For more information about valid options please see:
# /usr/share/doc/ltsp-client/examples/lts-parameters.txt.gz
# in the client environment.
#
# Note that things like sound and local device support are
# auto-enabled if the corresponding packages are installed,
# there is no need to manually set these options anymore.
#
# **** THIS FILE SHOULD NO LONGER BE USED FROM HERE !!! ****
#
# With the introduction of the nbd/unionfs/squashfs structure
# the lts.conf file moved to the tftp root please create:
# /var/lib/tftpboot/ltsp/i386/lts.conf instead for your changes
#
# In case you want to use the lts.conf here, this still works,
# but you need to run ltsp-update-image after every change.
[default]
LTSP_VERSION=5.0.39
_________________________
so I did this:
cd /var/lib/tftpboot/ltsp/i386/
sudo touch lts.conf
gksudo gedit /var/lib/tftpboot/ltsp/i386/lts.conf and added the HWADDR of the clients nic card

[00:40:f4:51:66:66]
XSERVER = ati
X_MODE_0 = 600X800
X_HORZSYNC = "30-70"
X_VERTREFRESH = "50-130"
------------------------------
it still needs some work, but it works.
_______________________
added user2 to server's root
System -> Administration -> Users and Groups
+Add User

login from ltsp client
user user2
passwd *******
login to server from ltsp client succes
----------------------
Ubuntu Server Edition [http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)
> 
Ubuntu Server edition includes thin client support using LTSP (Linux Terminal Server Project). LTSP-5, the latest release, offers a simple installation and easy maintenance. All the data is stored on the server, which will substantially diminish the cost of updating individual workstations and help to ensure their security. Notable benefits of Ubuntu's thin client support are:

    * Simplified management: manage all clients from one system. Install new software, change their configuration, or even upgrade to a new version on the server, and all clients are instantly up to date. There is only one backup to take for all clients.
    * Fully automatic installation and setup: installing a thin client server is as easy as installing a single desktop system, and once it's finished, new clients can be added with no additional administration on the server
    * Lower TCO through shared resources: Common high-powered desktop workstations sit idle most of the day consuming power and costing your organization money. With a high-powered server and low-cost thin clients, you can get great performance and save money. Need higher performance? Just upgrade the server, and all clients instantly benefit.
    * Quick failure recovery: If a client system fails, simply swap in a new one and continue working. No configuration is required, and all of the user's data and settings are intact.
    * Locally attached devices: Users can access printers, cameras, iPods, USB sticks and other devices connected directly to the thin client.
---------------------
Is there an LTSP forum anywhere? thread here: [http://ubuntuforums.org/showthread.php?t=603151&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=603151&highlight=ltsp)
links
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)
[https://wiki.ubuntu.com/EnableLTSP5LocalDevices](https://wiki.ubuntu.com/EnableLTSP5LocalDevices)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

[http://forum.freespire.org/showthread.php?t=10932](http://forum.freespire.org/showthread.php?t=10932) 
from here [http://ubuntuforums.org/showthread.php?t=603151&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=603151&highlight=ltsp)

[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition) and
[http://www.skolelinux.no/~klaus/newnotater/index.html]("http://www.skolelinux.no/%7Eklaus/newnotater/index.html")
from here [http://ubuntuforums.org/showthread.php?t=479555](http://ubuntuforums.org/showthread.php?t=479555)

[http://www.ltsp.org/](http://www.ltsp.org/)
[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
[http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo](http://wiki.skolelinux.no/DebianEdu/Documentation/Etch/HowTo)
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian)
[http://wiki.debian.org/LTSP/Howto](http://wiki.debian.org/LTSP/Howto)
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

---

