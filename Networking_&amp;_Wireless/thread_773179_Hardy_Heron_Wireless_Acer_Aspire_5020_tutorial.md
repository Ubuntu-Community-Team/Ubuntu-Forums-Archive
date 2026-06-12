---
title: "Hardy Heron Wireless Acer Aspire 5020 tutorial"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by *g!t5^_)*(H on 2008-04-28
[COLOR="Navy"]This is a tutorial, to make Wireless cards BCM43XX work for Acer Aspire 5020 computers. I've tried to write this tutorial at the 'wiki', but I can't log in, so please if this is successful for somebody write it with pictures at 'wiki', I hope it will help someone. Thanks

Albert[/COLOR]

---------------------------------------

The goal of this tutorial is to set up wireless for ACER Aspire 5020 computers.

Introduction:

For several years has been difficult to set up Wireless for ACER Aspire 5020 series, still now with Hardy Heron is not an easy task. This tutorial will help you to set up your Wireless driver, and is recommendable for people without connection (other than wireless one).

[COLOR="Green"]1 - Download necessary files from Internet:[/COLOR]

(You can do this step from another computer, of course)

[http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Save all these three files into a folder (for Example 'bcm43xx' at your desktop)

[COLOR="Green"]2 - Install 'fwcutter' :[/COLOR]

Double click 'b43-fwcutter_011-1_i386.deb' file, a window will open and then click 'Install package'. When it asks you 'Fetch and install firmware?' you can skip this step if there's no Internet connection available, otherwise the last step of the installation will fail (needs Internet), but what's important is to have 'fwcutter' installed, because we will use the downloaded 'firmware installation files'.

(If there's a Wired Internet connection working properly, check 'Fetch and install firmware' and skip step number 3)

[COLOR="Green"]3 - Install 'broadcom firmware' :[/COLOR]

a ) Open a Terminal, go to Applications>Accessories>Terminal

b ) Go to the folder where the files are located (for example ~/Desktop/bcm43xx)

c ) Get super user control, type : sudo bash and press intro, then write your password

d ) Type : gedit installBCM43xxFirmwareLocal.sh

A new window will open, copy and paste next lines (as they are) into this file:

[I]#!/bin/sh

b43-fwcutter -w /lib/firmware ./wl_apsta-3.130.20.0.o
tar xfvj ./broadcom-wl-4.80.53.0.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
rm -rf "$dir"
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy[/I]

Then save the file and close the window, you will be able to write into the 'Terminal' again.

e ) Make this file executable typing : chmod 777 installBCM43xxFirmwareLocal.sh

f ) Execute this file to install the firmware, type : ./installBCM43xxFirmwareLocal.sh

[COLOR="Green"]4 - Make 'Acer Hot Key' available :[/COLOR]

a ) Open a Terminal, go to Applications>Accessories>Terminal

b ) Go to the folder where the files are located (for example ~/Desktop/bcm43xx)

c ) Get super user control, type : sudo bash and press intro, then write your password

d ) Type :  gedit installAcerHKSwitcher.sh

A new window will open, copy and paste next lines (as they are) into this file:

[I]#!/bin/bash

modprobe acerhk
echo acerhk >> /etc/modules

echo "#!/bin/bash" > /etc/acpi/acerhkWOnOff.sh
echo " " >> /etc/acpi/acerhkWOnOff.sh
echo ". /etc/acpi/acerhkWState" >> /etc/acpi/acerhkWOnOff.sh
echo " " >> /etc/acpi/acerhkWOnOff.sh
echo "if [ \$variable -eq '0' ]" >> /etc/acpi/acerhkWOnOff.sh
echo "then" >> /etc/acpi/acerhkWOnOff.sh
echo "echo \"variable=1\" > /etc/acpi/acerhkWState" >> /etc/acpi/acerhkWOnOff.sh
echo "echo on > /proc/driver/acerhk/wirelessled" >> /etc/acpi/acerhkWOnOff.sh
echo "else" >> /etc/acpi/acerhkWOnOff.sh
echo "echo \"variable=0\" > /etc/acpi/acerhkWState" >> /etc/acpi/acerhkWOnOff.sh
echo "echo off > /proc/driver/acerhk/wirelessled" >> /etc/acpi/acerhkWOnOff.sh
echo "fi" >> /etc/acpi/acerhkWOnOff.sh
echo "variable=0" > /etc/acpi/acerhkWState
chmod 755 /etc/acpi/acerhkWOnOff.sh
chmod 777 /etc/acpi/acerhkWState[/I]

Then save the file and close the window, you will be able to write into the 'Terminal' again.

e ) Make this file executable typing : chmod 777 installAcerHKSwitcher.sh

f ) Execute this file to install the switcher, type : ./installAcerHKSwitcher.sh

g ) Press the 'Right button' of your mouse on the 'Top bar', and select 'Add to Panel...'

h ) Select 'Custom application launcher' and then '+Add'

i ) At 'Name' field write: AcerHK switcher

j ) At 'Command' field write: /etc/acpi/acerhkWOnOff.sh

k ) At 'Comment' field write: Enables or disables Wireless card

l ) Press at the icon and write : /usr/share/icons/gnome/scalable/devices/network-wireless.svg , then accept with 'OK'

m ) Press 'OK'

This new 'button launcher' will Enable or Disable wireless availability, probably you will have to press a couple of times at 'StartUp time' to enable wireless, then the 'Wireless light' will shine and after some seconds 'Network Manager Applet' (near the volume) will start working... 

(Probably there's a better way to perform this action, but this way results very comfortable to me :P)

[COLOR="Green"]5 - Enable the driver :[/COLOR]

a ) Go to : System>Administration>Hardware drivers

b ) Enable 'Broadcom B43 Wireless driver', probably you will have to restart your computer.
[COLOR="Green"]
6 - Enjoy Ubuntu Hardy Heron[/COLOR]

---

### Post by ksauber on 2008-04-28
Thanks!

However, I ran into a slight problem.  

First off, I'm attempting to use this for an Acer Aspire 5000, with an AMD64 processor.

I downloaded and installed the correct fwcutter from: **[http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/](http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/)**

When executing:  ./installAcerHKSwitcher.sh I receive an error.

Further checking show that the command "modprobe acerhk" returns an error as follows:

**FATAL: Module acerhk not found.**

Do you know offhand what I'm doing wrong?

Thanks!
Kirk

---

### Post by *g!t5^_)*(H on 2008-04-29
Probably there's no 'Acer Hot Key' driver for 64 installation, are you using 64 bits Ubuntu? 

Otherwise there's no reason to receive an error, if you execute 'sudo ./installAcerHKSwitcher.sh', because 'acerhk' comes (for sure) installed by default with Hardy Heron.

---

### Post by playfarmer on 2010-03-20
I am absolutely new to ubuntu and linux.  I'm having same problem getting my acer aspire 5000 with the 4318 card to work also.  I've tried downloading the prescribed files and when clicking on the file to load 'b43-fwcutter_011-1_i386.deb' i get error "wrong architecture 'i386'.  what else can i try?

---

### Post by bkratz on 2010-03-20
> **playfarmer said:**
> I am absolutely new to ubuntu and linux.  I'm having same problem getting my acer aspire 5000 with the 4318 card to work also.  I've tried downloading the prescribed files and when clicking on the file to load 'b43-fwcutter_011-1_i386.deb' i get error "wrong architecture 'i386'.  what else can i try?

That is a pretty old thread you are following, things have changed since then.  See this site.

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

Find yours then look at the section labeled ( Ubuntu/Debian)

---

### Post by playfarmer on 2010-03-20
i'm new to ubuntu.  when reading all these post with command lines, how do i execute them?  how is a "terminal" opened?

---

