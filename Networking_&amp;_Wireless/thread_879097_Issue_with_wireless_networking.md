---
title: "Issue with wireless networking"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by zjagannatha on 2008-08-03
I have been having trouble with my laptop connecting to the internet. I have no Ethernet card, so Wireless is the only internet source for this computer. The wireless card is a BCM4306 Wireless LAN Controller from Broadcom Corp. I have been unable to get the wireless to work. ](*,)

I have tried the [Troubleshooting Page]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html") and done everything it says to do. I get caught up at "Check for a connection to the router."

I have tried looking at the [WPA Page]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29") as well. I don't know if there is something wrong with my driver, or if I need to install ndiswrapper, or if it's some incompatability with the network I'm trying to connect to (I'm in a Library so I can't access or edit the network). :confused:

I like Linux, but if I can't get this fixed before school starts in August, I'm going to have to go back to Windows XP.

---

### Post by cpetercarter on 2008-08-03
Have a look at [http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/]("http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/")

---

### Post by zjagannatha on 2008-08-07
Thanks, but I can't install "b43-fwcutter". I've looked on the forum for how to install it and none of the methods work. How do I install "b43-fwcutter".

---

### Post by lwfinger on 2008-08-10
Open a terminal and run the two commands that follow. Please post the output:

(1) dmesg | grep b43
(2) /sbin/lspci -nnv        (Only the section that describes your wireless)

---

