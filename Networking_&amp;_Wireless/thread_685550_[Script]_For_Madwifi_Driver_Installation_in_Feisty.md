---
title: "[Script] For Madwifi Driver Installation in Feisty"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by Paris Heng on 2008-02-02
Dear,

Below are the shell script for installation of Madwifi driver in Feisty (tested):

> #!/bin/sh
#Name: madwifi.sh by Paris Heng
#This script is for Madwifi driver installation with Ubuntu 7.04
#Prior to installation, you must have Internet connection to proceed and 
#have downloaded madwifi driver, version using in this script is madwifi-0.9.3.1

#Get what is needed to compile the source
sudo apt-get -y install build-essential bin86

#Copy the .tar.gz to the /usr/src/ folder
#Change the Madwifi driver revision if necessary
sudo cp /home/<user>/Desktop/madwifi-0.9.3.1.tar.gz /usr/src/

#Change to the /usr/src folder
cd /usr/src

#Decompress the tarball
sudo tar -xzf madwifi-0.9.3.1.tar.gz

#Install the sharutils from the package manager
sudo apt-get -y install sharutils

#Change to the folder that the tarball extracted to
cd /usr/src/madwifi-0.9.3.1

#Make the drivers (during this time the procedure may ask you to remove the older drivers, let it do so)
sudo make clean
sudo make
sudo make install

#You don't need to but as you are going to reboot you can test your work so far
sudo modprobe ath_pci

#Delete the archive which we copy earlier
rm -r madwifi-0.9.3.1.tar.gz

#You can remove the archive from your directory
rm -r /home/<user>/Desktop/madwifi-0.9.3.1.tar.gz

#You will need to modify the modules file to make this change permanent in /etc/modules
cd /etc
echo "Add ath_pci to the /etc/modules"
CODE=ath_pci
echo $CODE >> /etc/modules


---

