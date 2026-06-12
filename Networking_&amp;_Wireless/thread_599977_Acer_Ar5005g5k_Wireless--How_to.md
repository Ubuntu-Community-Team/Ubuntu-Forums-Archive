---
title: "Acer Ar5005g/5k Wireless--How to"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by casaduana on 2007-11-01
After having my Acer 3050 laptop with no wireless networking on Xandros4.1 and Ubuntu 7.04, I found the following solution that is currently working very nicely and loads with every reboot.

I cannot take much credit since I pieced together the code from several different threads, p=2731459 by "benanzo" and one entitled "Installing the wireless driver in Terminal. My contribution is having found an updated version of the Madwifi driver----madwifi-0.9.3.3.tar.gz (10-17-2007) that is application specific for the ar5000 series Atheros wireless for recent (2006-7) Acer laptops.

Download the driver from this link: [http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz?modtime=1192683135&big_mirror=0](http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz?modtime=1192683135&big_mirror=0)

Extract the file to a new folder: madwifi-0.9.3.3

Open Terminal

Write the following Code:

sudo apt-get install subversion build-essential linux-headers-$(uname -r)
cd $(HOME)/Desktop
cd $(HOME)/Desktop/madwifi-0.9.3.3

(do not write this---This command will show you the extracted contents of madwifi-0.9.3.3)

make

sudo make install

sudo modprobe ath_pci

sudo iwlist ath0 scan

(do not write this---This command shows what networks it sees)

sudo modprobe ath_pci

sudo modprobe wlan_scan_sta

sudo wlanconfig ath0  list scan

sudo iwconfig ath0 essid "your router/network name"

sudo dhclient ath0

(do not write---These last 3 commands scan for AP's, tell ath0 to open your network, and get the DHCP Address for your connection.)

At this point your should already see the signal bars in the upper right of the screen and a confirmation message of "connected to..."
Close Terminal and enjoy! After tearing out much hair and cursing everyone in sight, I am enjoying wireless networking/internet in Ubuntu on my Acer Aspire!

Hope this helps you all!

Casaduana

---

