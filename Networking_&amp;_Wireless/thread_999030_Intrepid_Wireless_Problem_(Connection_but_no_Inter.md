---
title: "Intrepid Wireless Problem (Connection but no Internet)"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by SanderLewis on 2008-12-01
After installing 8.10 and hoping to finally abandon XP as my main OS, I'm again encountering the wonderful world of wireless. This version of Ubuntu is almost there, but here's my problem.

For the first time, a distro has automatically recognized my wireless cards. 

I have a USB Netgear WG311v2 and a USRobotics5417.

Network Manager picks up various signals for the Netgear device and CAN CONNECT!

I have connected to my home network unsecured, WPA, and WEP.

Even though connected however, no internet service will work (Firefox, Evolution, Pidgin, Synaptic, etc.) This is so frustrating.

I'm a half n00b, so if anyone has any kind of advice, please let me know. I read somewhere that someone's problem was solved by updating after install, however, I just downloaded the OS the yesterday. Thanks all for your help.

---

### Post by IanW on 2008-12-01
It sounds like you have no DNS servers listed.
You should have a list of them from your ISP - groups of 4 numbers in the format aaa.bbb.ccc.ddd
You need to enter these into Network Manager.

---

### Post by SanderLewis on 2008-12-01
Thanks Ian, I'll get the comcast DNS settings and see if it works tonight. I assumed Network Manager would automatically find them, is this not the case?

---

### Post by Plodder on 2008-12-02
I have the same problem.  I have a Netgear WGR614V9 router, a Dell Inspiron laptop (dual boot Ubuntu 8.10 & XP), an old laptop (Xubuntu) and a Nokia N800.  The Nokia, Xubuntu laptop and Dell laptop running XP all talk to the router no problem and give good Internet access.  However I cannot connect to the Internet using the Dell Inspiron laptop running Ubuntu 8.10.  Network manager finds the router and reports a good signal (98% strength) but the Netgear software does not show the laptop as an attached device.  Any help would be much appreciated.

---

### Post by ussndmac on 2008-12-02
I have the same issue with a 3945 in hardy and intrepid.

It appears the driver doesn't like to connect to a WAP with 802.11b.

But I see the node, I have signal, etc. but it won't actually connect.

---

### Post by Ichido on 2008-12-03
My Dell inspiron 1525n ran 7.10, 8.04 and now runs 8.04.1 great.
It's using the Intel iw3945.
I'm now 'test' running 8.10 from a CD and it is working fine.
My Wireless is 802.11g using WPA and NetworkManager Applet 0.7.0.
When I Left-Click the NM Applet Icon, a drop-down menu shows my network's ESSID and Signal Strength.
I just click the Radio Button by my Network and a box pops up asking for my Password (WPA), then a second box asking for a Keyring Password (anything I type works, I think due to running from the CD), and then I'm on-line!
Is there information I can supply to help?

---

### Post by Plodder on 2008-12-04
Thanks for your offer of help, Ichido.  I have booted up into a live cd (Xubuntu) and it all works fine.  I rebooted into Ubuntu and nothing.

I connected wired to update Ubuntu (I believe there was a network manager update a couple of days ago).  I have got online wired no problem but for some reason cannot log on to the repositories.

I wonder if these problems are related.  I also wonder if the problem is with the keyring applet.

I must away to work now but will try to resolve this later.  I may be back for help then!

---

### Post by Plodder on 2008-12-06
I have re-installed network manager and this has had no effect - I can connect to the router but the router does not see the laptop and I cannot get onto the internet.

I burned an Ubuntu 8.10 live cd and booted from that.  No problems - I can see the router and the router can see me.  I am allowed a connection to the internet.  (Bear in mind it is Ubuntu 8.10 installed on the laptop).

'Tis a curious thing.  If anyone can offer help, suggestions I would be most appreciative.

---

### Post by Ichido on 2008-12-06
Get your system up and running with the CD (which I believe works with the Wireless Router) and then check and write down (on paper) all the details from your PC and also including the details from your Wireless Router's settings.
Now run the PC's installed version and check & compare all the details.
This is where I'd start first.

Keep this list handy:
ifconfig - lists IP address (similar to ipconfig in Windows)
iwlist scan - shows wireless networks that are available in the area along with basic encryption information
lshw -C network - Shows interface and driver associated with each networking device
lspci -nn - Shows hardware connected to the pci bus
lsusb - Shows USB connected hardware
lshw -C usb - Additional info on USB related hardware (good for USB dongles)
cat /etc/modprobe.d/blacklist - List modules that will not be loaded by the Operating System at boot time
lsmod - lists currently loaded kernel modules. (Example usage - lsmod | grep ndiswrapper)
route -n - Lists kernel IP routing table -- Good for troubleshooting problems with the gateway (netstat -rn = equivalent command)
sudo route add default gw 192.168.1.1 - Example of how to set the default gateway to 192.168.1.1 
sudo route del default gw 192.168.1.1 - Example of how to delete the default gateway setting
sudo modprobe ***** - Loads the kernel module **** . (Example usage - sudo modprobe ndiswrapper, sudo modprobe r818x, sudo modprobe ath_pci)
sudo modprobe -r **** - Unloades the kernel module ****. (Example usage - sudo modprobe -r ndiswrapper)
sudo ifup/ifdown <interface> - Brings up/down the interface and clears the routing table for the specified interface
sudo ifconfig <interface> up/down - Brings up/down the interface for the specified interface 
sudo dhclient <interface> - Request IP address from DNS server for specified interface
sudo dhclient -r <interface> - Release IP address associated with specified interface
sudo iptables -L - Lists firewall rules 
dmesg | more - Lists boot log -- good for troubleshooting problems with modules/drivers not being loaded
uname -r - Displays kernel version
/etc/iftab (Feisty and pre-releases (Edgy, etc)) - /etc/udev/rules.d/70-persistent-net.rules (Gutsy) - File which assigns logical names (eth0, wlan0, etc) to MAC addresses
cat /etc/resolv.conf - Lists DNS servers associated with network connections (Network Manager)
/etc/dhcp3/dhclient.conf - File which sets or modifies dns (domain name servers) settings
# Ubuntu version & kernel >> uname -a 
# Root file access >> alt F2 then 'gksudo nautilus' in cli
# Get IP Address or Renew >> sudo dhclient wlan0 [or whatever your wl adapter is]
# Get wireless info >> iwconfig
# Routes if wlan0 working >> route
# DNS resolving via eth1 >> cat /etc/resolv.conf
# List devices/modules >> lspci, lsusb, lshw, lsmod
# Restart network >> sudo /etc/init.d/networking restart
# Kill NWM >> sudo killall NetworkManager 
# Events from your wl >> iwevent 
# Restart all daemons >> sudo /etc/init.d/dbus restart 
# Restart network >> sudo /etc/init.d/networking restart

---

### Post by Plodder on 2008-12-07
Thanks Ichido 

I do not have any time to work on this problem today as I'm off to visit my aged Aunt for the day.  I will try to work my way through this list tomorrow.

Plodder

---

