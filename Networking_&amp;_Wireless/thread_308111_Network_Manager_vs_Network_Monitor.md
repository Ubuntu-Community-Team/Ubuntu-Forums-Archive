---
title: "Network Manager vs Network Monitor"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by paparoof on 2006-11-27
I'm running a fresh Edgy Eft install, I need to get to WPA and also I just want some of the advertised features of Network-Manager-Gnome. Network Monitor (2.12.0) was already there after the install and wireless works fine with plain and WEP also.

I followed [this howto]("http://http://www.ubuntuforums.org/showthread.php?t=125150&highlight=wpa+aes") to get Network Manager installed and running and it appears to be successful with one exception. Clicking on the NM icon in the notification area results in "no network devices have been found". The Network Monitor icon is still there, and I am still connected to to my WEP network (that's how I'm typing this!).

I'm guessing that Network Monitor is getting in the way of Network Manager and I need to get it out of the way, but I don't know how to do that. Maybe there's a config file for Network Manager that I need to setup. I don't know. Other than that thread I linked to above, I can't really find any documentation for Network Manager anywhere.

I'm sure I'm looking in the wrong place(s) and it's an easy fix, but I'm stumped. Please help.

BTW - I have the newest IPW2200 drivers installed (ipw2200-1.2.0).

---

### Post by Spin Doctor on 2006-11-27
Checkout this How To, which I find outstanding for the subject:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Did you edit: /etc/network/interfaces 

To get my wpa-psk up running, I had to comment (##) out everything on /etc/network/interfaces except these lines:
```
auto lo
iface lo inet loopback
```And then reboot.

---

### Post by randomnumber on 2006-11-29
Yes, you have to disable the network device in network-monitor. I am guessing that network-monitor is the default option and you can simply go to System-> Administration-> Networking and uncheck it to disable the devise you want to use in network-manager. A reboot may be necessary, I don't remember.

---

### Post by theambitiousbean on 2006-12-16
paparoof, did you ever get you problem solved?  

I am having a similar issue with a fresh install of edgy, where the wireless interface could not be found (in network monitor) until installing network-manager.  Upon installing network-manager the interface was found and successfully connected to a unsecured AP on it's own.  When I try to open network-monitor and configure the card (setup a connection to my secured AP), I can check the "Enable this connection" (no networks are listed in the "Network name" drop-down, though I am connected to one) and click "Save", but when returning to the list of network devices the wireless interface is still unchecked and displayed as "This network interface is not configured".

I have installed and uninstalled network-manager-gnome, which allowed me to view all the networks and their signal strengths, but still cannot configure the wireless interface to connect to one.

I tried commenting out every line except the two Spin Doctor mentions in /etc/network/interfaces and rebooted, but nothing changed.

Is there a way to reinstall/reconfigure network monitor to configure my wireless interface since network-manager was installed?

---

### Post by randomnumber on 2006-12-17
theambitiousbean

You do realize that "network monitor" is an entirely different program from "network manager" and that you config "network manager" with a different GUI than "network monitor"? When you install the "network manger" you should probably  have a additional applet in the top corner of your screen. Most likely when one of the application configuration GUI is not showing network info the way you think it should, it is likely that the other application has that hardware reserved so that the program you are looking at is not able to access it. 

You may also look at the following link. [http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

---

