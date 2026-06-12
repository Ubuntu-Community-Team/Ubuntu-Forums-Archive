---
title: "How to install a Intel 2011B Lan card on Hoary"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by danfan521 on 2005-11-07
I have a Hoary installation on my Latitude that works really great. I notice however that during the install it only installed drivers for my built in 3Com NIC and not the Intel Pro/Wireless 2011B LAN PC Card inserted into the PCMCIA slot. How do I get the system to use my wireless card?  

dmesg says:

orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: failed to initialize firmware (err = -16)
orinoco_cs: register_netdev() failed
orinoco_lock() called with hw_unavailable (dev=dd5c1000)

Are there some clear steps on how to install this card??

---

### Post by Teroedni on 2005-11-07
This card uses a firmware only found in windows driver. Therefore you most install via ndiswrapper
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

here is the windows driver
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=763&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=763&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21)


try it and post here if you get into truble or have more questions
Good luck:)

---

### Post by danfan521 on 2005-11-07
[QUOTE=Teroedni]

here is the windows driver
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=763&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=763&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21)


try it and post here if you get into truble or have more questions
Good luck:)[/QUOTE]

The files on the intel site are in a .exe format. Do I need to uncompress them on another PC to get the proper files??

---

### Post by danfan521 on 2005-11-07
So I unpacked everything on a Windows system (NetWLan5.inf and NetWLan5.sys) and moved it onto the system. Then executed the rest of the commands that were in the tutorial: 

root@ubuntu-fly:~# ndiswrapper -i NetWLan5.Inf
Installing netwlan5
root@ubuntu-fly:~# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
root@ubuntu-fly:~# modprobe ndiswrapper
root@ubuntu-fly:~# ndiswrapper -l
Installed ndis drivers:
netwlan5        driver present
root@ubuntu-fly:~# 

It appears that it doesn't find the hardware. dmesg now says

orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: failed to initialize firmware (err = -16)
orinoco_cs: register_netdev() failed
orinoco_lock() called with hw_unavailable (dev=dd08c800)
root@ubuntu-fly:~#

I'll keep debugging. Thanks for your help.

---

### Post by Teroedni on 2005-11-08
did you do the last task 
5. You also need to add the ndiswrapper module to the startup modules so Ubuntu can setup the device when your machine starts. You need to add ndiswrapper to the end of the /etc/modules file. You can do this by:

sudo gedit /etc/modules

Add ndiswrapper to the end of this, save and close. When your machine reboots, it will find the Wireless Adaptor and start it up.

---

### Post by Teroedni on 2005-11-08
also you need to foolow this guide
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

