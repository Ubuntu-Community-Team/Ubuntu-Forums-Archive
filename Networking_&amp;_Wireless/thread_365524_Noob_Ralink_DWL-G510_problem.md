---
title: "Noob Ralink DWL-G510 problem"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by BeeVee on 2007-02-19
Hello there,

I am a new Ubuntu user and have installed 6.10 on an oldish PC. I have intalled the D-Link DWL-G510 rev. C2 and downloaded the RT61 driver for this. I followed the instructions on how to compile the driver and install the modules etc and everything appeared to work but when I reboot the system there is no change... no signs of any wireless card... no connecting to the internet... any suggestions? Should I try Ndiwrapper [sp?]

Thanks and sorry for noobness!

---

### Post by bvmou on 2007-02-20
I think Ralink is among the better supported wireless manufacturers, you can get binaries and source here:  [http://rt2x00.serialmonkey.com/]("http://rt2x00.serialmonkey.com/"),

although I would be surprised if Ubuntu didn't include them.

Also, try NetworkManager (and/or look into WiFi Radar), which was indispensable for me.  That is available through synaptic (Add/Remove under Applications or System > Administration > Synaptic Package Manager.)

---

### Post by bselmer on 2007-02-24
I did the same as you: Installed Ubuntu 6.10 on a computer with a D-Link DWL-G510 rev. c2. But it seems to me that it detects the card. In the network manager it shows two wireless interfaces, wlan0 and wmaster0.

But when I configure them with my SSID and WEP key I stil get no network connection.

How can I see which driver is installed? Which is the right network interface, wlan0 or wmaster0?

This is the output from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

---

### Post by bselmer on 2007-02-24
I found the solution here: [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

Skip down to where it says "(b) rt61 in Dapper".  It's very simple and took me only a couple of minutes to get it up and running.

---

