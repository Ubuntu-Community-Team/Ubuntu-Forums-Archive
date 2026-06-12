---
title: "Trendnet TEW-423pi - recognized but no connection"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Moonbuzz on 2007-04-22
Hello all, hope you're enjoying your Feistyness!

I've recently got a new wireless card - Trendnet TEW-423pi, which I managed to install on Feisty using these instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The result is that I now have the wireless card recognised and working, and it even locates the networks in the area, including my own router, but I can't seem to connect. Any ideas/suggestions/tests needed to be run?

---

### Post by patrickfromspain on 2007-04-22
have you tried uninstalling network manager and using the gnome stuff to configure the card? I'd try that.. My ralink chipset card won't connect if network manager is installed.

---

### Post by Moonbuzz on 2007-04-22
> **patrickfromspain said:**
> have you tried uninstalling network manager and using the gnome stuff to configure the card?

Thanks, what do I need to remove/configure exactly?

---

### Post by u-blunt-2 on 2007-04-27
I suppose you are using the x86 distro ?
I had the same problem. I noticed that I could only connect to the wireless networks by manually activating the card using iwconfig.
I ended up creating a shell script that I launch each time I boot. 
```
#!/bin/bash
iwconfig wlan0 key "Insert WEP key here"
iwconfig wlan0 essid "Insert ESSID here"
iwconfig wlan0 commit

```

called it .wlan.sh and launch it with sudo.
[edit]
you can enter all that stuff in /etc/network/interfaces if you dont want to create the script.
[/edit]
ust agree that this is just a temporary fix untill I can get it to work properly. Has anyone tried this card on Fiesty ? What about 64 bit ?

---

### Post by ultima-thule on 2007-12-09
I'm not the original poster with troubles, new to this thread and having problems in this same area.

Not getting a list of access points yet.

I compiled the latest ndiswrapper and then did 

cd Utilitity_Driver_TEW-421PC_423PI/Drivers/WINXP/
ndiswrapper -i net8185.inf
modprobe ndiswrapper
ndiswrapper -m

got a shell script that does this:
======
sudo ifconfig wlan0 up
sudo iwlist wlan0 scanning
sudo iwconfig wlan0 essid black_swan
sudo iwconfig wlan0 key s:mystoopidpassword
sudo iwconfig wlan0 essid my_stoopid_airport
sudo iwconfig wlan0 commit
sudo dhclient
=======
which outputs this:

Listening on LPF/wlan0
Sending on LPF/wlan0
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

:( 

lshw 
gives positive/promising output:
*-pci
*-network:0
description: Wireless interface
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controler

Emphasis: I got no X Windows env.

---

### Post by ultima-thule on 2007-12-09
I just reconfigured my wireless router to use no encryption login. Still could not get access. Then tried the always open Seattle Public Library across the street. Cannot get in it either. 

So I may have levels of failure. Something that does not have to do with logging into the lan,
and then likely may not know how to properly do the
iwconfig wlan0 key xxxxx
command

---

### Post by u-blunt-2 on 2008-01-14
what kind of encryption is your router using ?

---

