---
title: "Can't get network mannager to configure wireless network after ndiswrapper installed"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by BryceHarding on 2007-11-24
I have an inspiron 1720 using a Dell wireless 1505 draft 802.11n wlan card and am unable to get it to work with my WLAN. I have installed other linux distros on other computers and have had nothing but frustration as I am a little bit of a newb.

This is my first attempt at installing linux on this laptop and i had breifly succeeded on getting wireless working. I installed ndiswrapper and the windows driver. The wirless option appeared in network manager and i was able to setup wpa and access my router but i think I moved some files arround that i shouldn't have and it is no longer opperating.

I deleted my Ubuntu partions and have reinstalled in the hope that a clean install will allow me to do whatever it was i did before.I have had to use ndiswrapper and have installed the correct dell driver for windows and it appears that the everything is setup correctly. When I do an ndiswrapper -l i get the following output: 

[INDENT]bcmwl5 : driver installed
        device (14E4:4328) present[/INDENT]

 Although ndiswrapper and the driver appear to have been installed I do not get a have a wireless option in network manager.

When i try iwconfig i get the following: 


[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.[/INDENT]

I hope someone can help me with this as this is the first time I have had any success with wlan and linux and it seems a little crazy i can't repeat my earlier success. Wireless is the main application that prevents me from using ubuntu as my primary OS. Im frustrated at the learning curve when it comes to wireless networking with linux but i am still anxious to get it up and running so i can tell Microsoft where to stick it.

---

### Post by kevdog on 2007-11-24
Please post lshw -C network -- I didnt know that the bcmw5 driver -- the standard 32bit broadcom driver -- supported the wireless n standard.

---

### Post by BryceHarding on 2007-11-29
have played arround with different drivers and have had some sucess using the inf file found in R151517.EXE driver. I can get it to install at terminal but System> Administration> Network does not come up automaticaly. 

Started using ndiswrapper GUI tool from the package manager and when i use it to uninstall and reinstalll the driver the Network Manager displays my wireless connection and allows me to select my network and login.

Main prob now is that i have to do this every time i reboot. That is use the System> Administration> Windows Wireless Drivers utility to manualy uninstall and then reinstall the driver after boot. I do not have to re-enter my wpa key it just connects up on it's own.

Can anyone tell me what i can do to fix this? Perhaps make a script and have it run on boot? If i have to do it that way can someone tell me how it is done?

output of  lshw -C network:

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 03
       serial: 00:1c:26:92:5d:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.50+Broadcom,10/12/2006, 4.100. ip=192.168.1.103 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a1:2e:7f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no module=b44 multicast=yes port=twisted pair speed=10MB/s

---

### Post by BryceHarding on 2007-11-29
managed to get it to work by doing editing /home/etc/modules and adding ndiswrapper.

---

