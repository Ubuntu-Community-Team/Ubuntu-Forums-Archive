---
title: "Perfect Jaunty - MHOOC"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-10
I moved from Hardy 8.04 to Jaunty 9.04 and documented what I did to configure the OS the way I like it.  


What do you think is the perfect Jaunty?


Here is what I did:




General

This describes how I moved from 32-bit Ubuntu 8.04 Hardy Heron to 64-bit Ubuntu 9.04 Jaunty Jackalope. Below are the configuration changes I make to a virgin instance of Ubuntu to make it into my &#8220;perfect Ubuntu&#8221;.



Initial-1
Get list of packages installed on OLD PC


- On old PC, get a list of all the packages I had installed:
$ dpkg --get-selections | grep -v deinstall > installed-software


- Manually scan through the list of packages and remove any I think I don't need.


- On new PC, reinstall all the packages I installed on the old PC:
$ sudo dpkg --set-selections < installed-software


- Remove orphaned packages:
$ sudo apt-get autoremove
$ sudo apt-get update


Install fresh copy of Ubuntu 9.04

Keep old 8.04 Ubuntu and install new 9.04 in separate partition.

Use the Desktop CDROM.

At the Options boot:

    *

      Press F4 and change to Safe Mode Graphics
    *

      change to NOACPI if you have boot problems (did not have to to do this this time)



Using these Partitions:

I found that having separate partitions for the OS and another for /home makes it much easier when it comes time to upgrade. I have 2 partitions for OS use so that I don't have to overwrite the OS that is working. This way I can boot my old partition until I get things completed.

/dev/sda4 / 33GB Ubuntu 8.04

/dev/sda2 /swap 4GB

/dev/sda3 /home 200GB

/dev/sda1 / 33GB Ubuntu 9..04



Backup

If you want to be super careful, backup everything. I feel confident enough that I don't need to do this anymore:

Backup /home to /HOME-BACKUP

Use Clonezilla to clone the /home partition on the old PC to the new Hard Drive.





Remote Access

Configure to allow for remote access:

System &#8594; Preferences &#8594; Remote Desktop

Check: Allow other users to view your desktop

Allow other users to control your desktop

Require the user to enter this password

Uncheck: Ask for confirmation





Enable Menus:

Rt click Applications &#8594; Edit Menus

Applications &#8594; System Tools

check: Configuration Editor, Root Terminal



Right-Click and get command prompt

Configure to allow one to get the Terminal window by selecting from context menu when you right click in a folder:


sudo apt-get install nautilus-open-terminal



Window Shade roll up effect, Window Movement

Double click on title bar causes window to roll up rather than maximize:

System &#8594; Preferences &#8594; Windows

Titlebar Action: Roll up


Hold down the Alt Key to move a window

Movement Key: Alt



Video Drivers

Configure Screen Resolution, setup for Dual Monitors:

System &#8594; Preferences &#8594; Appearance

Visual Effects

Select Extra


$ sudo nvidia-settings

Set the screen resolution appropriately (1680x1050) and enable &#8220;Twin View&#8221; for dual monitors.




Samba

Configure file sharing for other computers on the network:

sudo apt-get install samba smbfs

sudo smbpasswd -a carl


copy current /etc/samba/smb.conf

sudo gedit /etc/samba/smb.conf

workgroup = myPC-2

netbios name = myPC-2




Applications &#8594; System Tools &#8594; Configuration Editor

System &#8594; smb

Set: workgroup = myPC-2



sudo /etc/init.d/samba restart



Mount Windows Share:

Here is an example on how to mount a windows share:

Places &#8594; Connect to Server

Service type: Windows share

Server: myPC

Share: PUBLIC

Folder: /

User Name: carl

Domain Name: myPC


mkdir /PUBLIC

chmod 4777 /PUBLIC





/etc/hosts

If you have other PC's on your network, put an entry in your hosts file:

192.168.1202 myPC

192.168.1205 myPC-2



/boot/grub/menu.lst

Had to do this for 8.04, not necessary for 9.04

Append the &#8220;kernel&#8221; line with pci=nomsi


Seems to run much faster without &#8220;pci=nomsi&#8221;



Remote Desktop


Synaptic:

rdesktop

tsclient

grdesktop



Networking
Static IP

Configure for Static IP &#8211; if you want to:

$ sudo vi /etc/network/interfaces

# This file is: /etc/network/interfaces

# --------------------------------------

#

# This file describes the network interfaces available on your system

# and how to activate them. For more information, see interfaces(5).


# The loopback network interface

auto lo

iface lo inet loopback



# This is a list of hotpluggable network interfaces.

# They will be activated automatically by the hotplug subsystem.

mapping hotplug

script grep

map eth0



# The primary network interface

auto eth0

iface eth0 inet static

address 192.168.1.101

netmask 255.255.255.0

network 192.168.1.0

broadcast 192.168.1.255

gateway 192.168.1.1

#




# ------------------------------------------------

# Then do this:

# sudo /etc/init.d/networking restart

# ------------------------------------------------





DNS

If you want to use Open DNS, do this:


$ sudo vi /etc/resolv.conf


# generated by NetworkManager, do not edit!

nameserver 208.67.222.222

nameserver 208.67.220.220




VPN Networking:

Synaptic:

pptpd

pptp-linux

pppdcapiplugin

kvpnc


Network Manager

If you want to configure a VPN connection:


sudo apt-get install network-manager-pptp

sudo apt-get install network-manager-gnome


Connection Tab:

Connection Name: <your company name>

Type: Windows VPN (PPTP)

Gateway: xx.xx.xx.xx


Authentication:

Check: Refuse EAP

Refuse CHAP


Compression & Encryption:

Check: Require MPPE encryption

Require 128 bit MPPE encryption

Enable stateful MPPE


PPP Options:

Check: Use Peer DNS

Exclusive device access (UUCP-style lock)

Debug Output

MTU: 1416 MRU: 1416

Connect-delay 0

Icp-echo-failure: 10

Icp-echo-interval: 10


Routing:

Check: Only use VPN connection for these addresses

192.168.103.0 / 24




Kvpnc

Another VPN example:


sudo apt-get install kvpnc


Profile &#8594; new profile (Wizard)

Next

Select: Microsoft PPTP

Next

Check: Require MPPE

Allow MPPE stateful mode

Refuse EAP

Do not use BSD compression

Do not use MPPC compression

Do not use deflate method

Get DNS server from peer

Authorization method: CHAP

Next

Username: carl

Password: xxxx

Check: Save user password

Next

Next

Next

Next

Profile name: <your company name>

Description: xxxx

VPN gateway: xx.xx.xx.xx

Next

Finish



NXServer

Setup NOMachine for very quick GUI remote access &#8211; this is great:
SSH, SSHD



Sudo apt-get install ssh



Copy to new PC the following:

/etc/ssh/ssh_config

/etc/ssh/sshd_config


sudo /etc/init.d/ssh restart


NXServer

Follow process: NoMachine NX/NXServer.odt



-----------------------
Step 0 &#8211; Setup ssh
-----------------------

Install the open ssh package using Synaptic Package Manager


Load up your /etc/ssh/sshd_config file into an editor:
sudo vi /etc/ssh/sshd_config

Add the following line & save the file:
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2


NOTE: The sshd_config file contains other settings that need to be setup properly &#8211; see the example file.

Restart sshd by typing:
sudo /etc/init.d/ssh restart


-----------------------
Step 1 - Download
-----------------------

Download "NX Desktop Server DEB for Linux" from:
[http://www.nomachine.com/select-pack...?os=linux&id=1](http://www.nomachine.com/select-pack...?os=linux&id=1)

Download "NX Node DEB for Linux" from:
[http://www.nomachine.com/download-node.php?os=linux](http://www.nomachine.com/download-node.php?os=linux)

Download "NX Client DEB for Linux" from:
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)

-----------------------
Step 2 - Install
-----------------------

Install the DEB files in this order:

nxclient
nxnode
nxserver

I just right-clicked on them and installed them...use apt-get if you prefer.


-----------------------
Step 3 - Configure
-----------------------

Verify nxserver is configured properly by typing:
sudo /usr/NX/bin/nxserver --status


This should return:

NX> 900 Connecting to server ..
NX> 110 NX Server is running.
NX> 999 Bye.

If you get any errors here, then something is wrong with your configuration. If not, then NX Desktop Server should be installed.

Before anyone complains, yes, I'm using the NoMachine server key just because it's easy. If you want to generate your own key, you can. These instructions worked for me on Dapper....YMMV. Let me know if you have trouble.....hopefully my notes were correct.





NXServer &#8211; useful commands:


sudo vi /usr/NX/etc/server.cfg

sudo vi /usr/NX/etc/node.cfg


sudo /usr/NX/bin/nxserver --restart

sudo /usr/NX/bin/nxserver --stop

sudo /usr/NX/bin/nxserver &#8211;start


sudo /usr/NX/bin/nxserver --useradd <username> --system

sudo /usr/NX/bin/nxserver --userdel <username> --system


sudo /usr/NX/bin/nxserver --userlist


sudo ./nxserver --usercheck <username>



sudo /usr/NX/bin/nxserver --status sudo vi /



Start the Client, configure insuring that you select Unix and Gnome.



Edit: /usr/NX/etc/node.cfg and set the log on greeting:

NODE_FIRST_LOGIN_GREETING = &#8220;xxx&#8221;

NODE_LOGIN_GREETING = &#8220;yyy&#8221;



Open Office 3.0


9.04 has Open Office 3.0 in the distribution:

Synaptic, remove old version Open Office 2.4

OpenOffice.org-common


Copy to new PC: Ooo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz


cd ./DEBS

sudo dpkg -i *.deb


cd desktop-integration

sudo dpkg -i openoffice*.deb



Make Open Office faster:


Start Open Office Writer

Tools &#8594; Options &#8594; Java

Uncheck: Use a Java runtime environment




Performance Tweaks

This will improve performance:

sudo apt-get install preload




Turn off IP6

sudo vi /etc/modprobe.d/aliases


alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

IPV6 slows down the IPV4 environment if the router out the door does not understand IPV6 and for most people IPV6 is not needed.


A reboot is required.



Swappiness

This will improve performance:


sudo vi /etc/sysctl.conf


# PERFORMANCE: cut down on swapping

vm.swappiness=5




Firefox:

browse to about:config

set: network.dns.disableIPv6 to true




To check IPv6 state open terminal and execute:

Code:

ip a | grep inet6

If this command shows some lines - IPv6 is enabled. If output is empty - IPv6 disabled.





Enable Ctrl + Alt + Backspace to reboot X-windows:

sudo aptitude install dontzap





Reboot keyboard sequence

Safely reboot your system:

Alt+PrintScreen + R, E, I, S, U, B



As can be remembered through the following phrase:

Raising Elephants Is So Utterly Boring



Alt + Prnt Scrn + R, S, E, I, N, U, B will safely reboot your system. Hold Alt + Prnt Scrn then press each of the letters one by one.


Quicken and QuickBooks

Install CrossOver software.

Install patch for Quicken and Quickbooks

	sudo gedit /etc/sysctl.conf

and change the line that reads:

	vm.mmap_min_addr = 65536

to:

	vm.mmap_min_addr = 0



Did not have to install Quickbooks and Quicken because I now have them on my /home partition:

Install Quicken

Install Quickbooks





Synaptic - Install Miscellaneous Software:



Below are all the packages I like to install on a virgin instance of Ubuntu:

alsa

audacious

audacity

beast

bluefish

bplay

build-essential

console-tools

csh

fping

miro

ntfs-xonfig

ntfsprogs

p7zip

p7zip-rar

p7zip-full

pmount

psutils

rar

unrar

rhino

rosegarden

rpm

sane

sbackup

scummvm

squashfs-tools

stops

traceroute

ubuntu-restricted-extras

unixodbc

unrar

vim-gnome

vim

vlc

wine

youtube-dl

bplay

bottlerocket





Vmware Player 2.5.2

If you already have a VM, then Vmware Player is the way to go:

Download Vmware-Player-2.5.2-156735.x86_64.bundle

$ sudo sh ./Vmware-Player-2.5.2-156735.x86_64.bundle





Vmware Server 1.06

Or if you prefer Vmware Server:

After I got a VM of Windows XP created, I instead used Vmware Player to run it.

I had more success with Vmware Server 1.06 rather than the web-oriented 2.x versions.

Make sure you have the needed build environment and tools to compile the vmware modules for the kernel:

sudo apt-get install build-essential linux-headers-`uname -r` xinetd

sudo apt-get install xinetd



sudo vmware-install.pl

Defaults for all setting.

Errors like: `GCC_3.4' not found


Solution:

$ sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/
$ sudo cp /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1



sudo runme.pl

Watch for prompt about GCC compiler being wrong version, select YES

Watch for prompt about entering Serial Number, select YES

XXXXX-XXXXX-XXXXX-XXXXX







Setup Printers

Run web admin interface to setup printers:

[http://localhost:631](http://localhost:631)



HP 2420 Printer

Device URI: parallel:/dev/lp0


CUPS:

Add Printer &#8594; Administration

Name: HP-2420

Continue

Device: hp LaserJet 2420 LPT#1 (hp LaserJet 2420)

Continue

Model: HP LaserJet 2420 &#8211; CUPS+Gutenprint v5.2.0-rc1(en)

Add Printer

Username: carl

Password: xxxx



Brother MFC-440CN

Device URI: socket://192.168.1212:9100

In Synaptic, install the brother-cups-wrapper-extra package.

In FireFox, go to [http://localhost:631/](http://localhost:631/) and Add Printer

There is no driver for the MFC-440CN, choose the MFC-465CN driver.


Download Printer Drivers from [www.Brother.com](www.Brother.com)


    *

      mfc440cnlpr-1.0.1-1.i386.deb
    *

      mfc440cncupswrapper-1.0.1-1.i386.deb
    *

      brscan2-0.2.4-0.i386.deb



Install csh &#8211; this is required:

sudo apt-get install csh



Install LPR Driver:


TURN PRINTER OFF


cd /usr/share/cups

sudo mkdir model


sudo mkdir /var/spool/lpd

sudo mkdir /var/spool/lpd/MFC440CN

sudo dpkg -i ./mfc440cnlpr-1.0.1-1.i386.deb



Install the CUPS Wrapper:

sudo ln -s /etc/init.d/cupsys /etc/init.d/cups

sudo dpkg -i ./mfc440cncupswrapper-1.0.1-1.i386.deb


cp /usr/share/cups/model/brmfc440cn.ppd /usr/share/ppd/

ln -s /u/share/cups/model/brmfc440cn.ppd /usr/share/ppd/brmfc210c_cups.ppd

chmod g+w /tmp

chmod o+w /tmp



TURN PRINTER ON


Final setup and Print Test Page:


System -> Administration -> Printing


Right-click the MFC210C and click &#8220;Properties&#8221;


* Connection Tab: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)

* General Tab: Here I rename 'MFC210C' to 'Brother Printer'. Let's the whole family know the printer they're selecting.

* Paper Tab: Ensure your local paper size is selected.

* Advanced Tab: Review the choices and make appropriate adjustments.

* From any tab: Click "Print a test page" to confirm all works well.





Install Scanner:


      1. Install the Brother scanner driver

      $ dpkg -i brscan2-0.2.4-0.i386.deb

      2. To use your machine as a network scanner, you need to set the friendly name, model name and IP address or node name in the driver using the commands below:

      brsaneconfig2 -a name=SCANNER model=MFC-440CN ip=192.168.1212

 

      3. You can check the result by running the command:

      brsaneconfig2 -q

      If the setting is done correctly, you will see the result as below:
      0 SCANNER1 "MFC-440CN" I:192.168.1212




PDF

Device URI: cups-pdf:/



Connect external backup drives:

Cd /media

sudo mkdir BACKUP

sudo chmod 777 BACKUP or sudo chmod go+w BACKUP







Configure Video for Dual Monitors

Important files:

/etc/X11/xorg.conf

~/.nvidia-settings.rc



cd ~home/Ubuntu Linux/Support/nVidia Drivers

sudo sh ./NVIDIA-Linux-x86-177.82-pkg1.run

Be sure a allow this to modify your xorg.conf file.

startx



nvidia-settings







Configure Router to port forward these ports:

22 = NXServer





Scummvm

Old school game virtual machine:

sudo apt-get install scummvm



If sound does not work:

Synaptic - select: libsdl alsa



Scummvm &#8594; Start &#8594; Add Game &#8594; puttputt.exe





DOSBOX

If you like to play with MSDOS:

sudo apt-get install dosbox





View Your Mind &#8211; VYM

Mind mapping software &#8211; great!!

Synaptic: vym





MonoDevelop

Program in C# - GUI-based IDE &#8211; great!!

Synaptic:

Monodevelop

Mono

mono-mcs

libmono-cairo



If your MonoDevelop project will not run, do the following:

In MonoDevelop, Project -> Options -> Build -> General
Changed Runtime version to: Mono / .NET 2.0



Summary:

Cannot get the following to function on 9.04 64-bit edition:

    *

      MFC-440CN Scanner, printer works using the MFC-465CN driver (64-bit)



Page: 21 Of 21

Carl

---

### Post by blueridgedog on 2009-05-10
Bravo...come by tomorrow and repeat on my system!

---

