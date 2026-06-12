---
title: "HP Pavilion dv2125nr Turion64"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by lankforddl on 2007-01-09
Hello,

I have an HP Pavilion dv2125nr laptop. Specs are: 
AMD Turion64 x2
Nvidia 6150 graphics/ Broadcom 4311 (i think?)

I finished the new install and can't get built-in wireless chip to work. Broadcom 4311. Wired connection works fine. I de-select the wired connection in gui util and select wireless connection, establish the connection setting. essid, etc... and nothing. when i run a iwconfig it looks like the setting are not sticking from the gui to the config file. 

see screen shot for more details. Any advice? 
Thanks
Danny

---

### Post by teaker1s on 2007-01-09
save yourself some major grief and follow these links
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by lankforddl on 2007-01-09
I'm working on the first link right now. Folowing the steps as i speak. thx

---

### Post by lankforddl on 2007-01-09
thanks teaker. I finally got it working:p . now it's on to the Do you know of a better network manager that i could install?  I used a lot of different wireless access point (ie starbucks, airports, etc..) 

Thanks again.
Danny

now it's on to the nvidia graphics chipset ugh!

---

### Post by teaker1s on 2007-01-09
okay you want to  have an ethernet connection
then in terminal
[COLOR="Red"]sudo apt-get install network-manager-gnome[/COLOR]

now on your desktop panel you want to click
system
administration
networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them-see screenshot attached
shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key

nvidia drivers you want to look at the dv6000 page I started, there have been reports of problems with wireless and nvidia-unless you need open gl it may be wise not to install nvidia open gl drivers

---

