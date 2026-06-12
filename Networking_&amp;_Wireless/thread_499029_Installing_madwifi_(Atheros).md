---
title: "Installing madwifi (Atheros)"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2007-07-12
Dear ppl,

I am using Ubuntu Freisty 7.04.

I am having problem in installing the Wifi card madwifi (Atheros chipset) uisng Madwifi.

It is do with the **linux-restricted-module**?

But i try uninstalling, but it will download other --> **linux-image-2.6.20-16-generic**

What happen actually? I am really no ideas, what the way for me to install the madwifi?

Please someone assist.

---

### Post by Paris Heng on 2007-07-12
Halo anybody there?

---

### Post by tava0002 on 2007-07-12
Can you install it with Synaptic Package Manager or Add/Remove Programs?

---

### Post by CPImmanuel on 2008-04-28
I too, am having a problem here. Hopefully someone can comment. I have a thinkpad T60p, running Ubuntu, Hardy Heron. I have tried several times to install the Madwifi drivers. I do not get any error messages, but neither do I get the HAL entry on my hardware driver list. iwconfig does not show any wireless extensions. modprobe ath pci gives me the following message:paul@paull-T60Ubuntu:~$ modprobe ath_pci
WARNING: Error inserting ath_hal (/lib/modules/2.6.24-16-386/volatile/ath_hal.ko): Operation not permitted
WARNING: Error inserting wlan (/lib/modules/2.6.24-16-386/madwifi/wlan.ko): Operation not permitted
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-16-386/madwifi/ath_pci.ko): Operation not permitted

Incidently I do get wireless connectivity if I insert an external D-link pcmcia card that i had lying around, but I want to use the internal atheros card that works well with Vista. 

Can anyone help?

Thanks, 
Paul

---

### Post by Paris Heng on 2008-05-04
***[Solved] For MadWifi-0.9.3.1.tar.gz.*** 

> #!/bin/sh
#Name: MadWifi.sh
#This script is for MadWifi driver installation with Ubuntu 7.04
#Prior to installation, you must have Internet connection to proceed
#Please always in the correct path

#Get what is needed to compile the source

sudo apt-get -y install build-essential bin86

#Copy the .tar.gz to the /usr/src/ folder
#Change the MadWifi driver revision if necessary

sudo cp /home/heng/Desktop/MadWifi-0.9.3.1.tar.gz /usr/src/

#Change to the /usr/src folder

cd /usr/src

#Decompress the tarball

sudo tar -xzf MadWifi-0.9.3.1.tar.gz

#Install the sharutils from the package manager

sudo apt-get -y install sharutils

#Change to the folder that the tarball extracted to

cd /usr/src/MadWifi-0.9.3.1

#Make the drivers (during this time the procedure may ask you to remove the older drivers, let it do so)

sudo make clean
sudo make
sudo make install

#You don't need to but as you are going to reboot you can test your work so far

sudo modprobe ath_pci

#Delete the archive which we copy earlier

rm -r MadWifi-0.9.3.1.tar.gz

#You can remove the archive from your directory

rm -r /home/heng/Desktop/MadWifi-0.9.3.1.tar.gz

#You will need to modify the modules file to make this change permanent in /etc/modules

echo "Add ath_pci to  the /etc/modules"
CODE=ath_pci
echo $CODE >> /etc/modules


---

