---
title: "How to for Broadcom 4318"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-03-07
I went through some of the how to's on the forum to try and get my Broadcom wireless card activated. One of the how to's made my wireless card not show up in Network settings. After getting all of the updates from [following the instructions on this page]("https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages") and understanding how ndiswrapper worked, I got my wreless card activated.
[EDIT] after going to the link above click on reload. You should then be propmted for updates[EDIT]

I will try to explain how I did this step by step.

First I checked if I had the Broadcom 4318 card
```
 lspci | grep Broadcom\ Corporation
```

You should have output like this 
```
 Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```


I then listed what drivers were installed with ndiswrapper
```
ndiswrapper -l
```

The output I had at first was
```
bcmwl5         invalid driver!
```
Which of course means that the driver that was installed was invalid. I installed that driver from the instructions on [this page]("http://ubuntuforums.org/showthread.php?t=185174").
The author does say that it may not work for the BCM4318 card

Next I removed the bad driver ( you do not need to do this if nothing is listed)
```
ndiswrapper -e bcmwl5
```
Next I found the device id on[ this page]("http://pci-ids.ucw.cz/iii/?s=1:i=14e44318")
Mine is 1468:0311. I have an Acer Aspire 3000 series

Next I downloaded [this file]("http://compwiz18.blackhole.cx/bcm4318/get.php?file=bcm4318.all.tar.gz") to my desktop
Next I exctracted the driver from the bcm4318.all.tar.gz file by doubel clicking on it. This will open up the compressed file and show two folders and ndiswrapper setup. Next I double clicked on the drivers-32.tar.gz ( because I have the 32 bit version of ubuntu - I have not tried this with the 64 bit version). I clicked on the Extract button. I changed the Extract in folder to Desktop. Open up terminal. Change your directory to desktop
```
cd Desktop
```

Next I installed the driver using ndiswrapper
```
ndiswrapper -i bcmwl5.inf
```
Finally I made my wireless card use this driver using the device id ( remember to use the correct one for yours!)
```
ndiswrapper -d 1468:0311 bcmwl5
```
Reboot!

I am a noob at linux and did not hav any vital information in the ubuntu install. This iis how I got mine to work after a little work.

---

### Post by Irid on 2007-03-07
OK, how do I get ndiswrapper in the first place?

---

### Post by lsutiger on 2007-03-07
I think it was from the updates I got from following the [instructions on this page ]("https://wiki.ubuntu.com/MOTU/Packages?action=show&redirect=UniversePackages")

---

### Post by Irid on 2007-03-10
I have an Acer Aspire 3680 laptop with Broadcom 4318 wireless card and this Howto helped me to bring the wi-fi LED on, but I'm not close to a hot-spot, so I'm not 100% it works, but it better did.
May I add these humble steps from my own.

Install ndiswrapper this way
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8
```

I also found that you don't need driver from the other forums thread (it didn't even work for me, said that it's too old), essentially one must only get bcm4318.all.tar.gz and follow instructions in the Howto.

---

### Post by Irid on 2007-03-13
Damn it, it doesn't work.

I have an orange LED light indicating my wireless status. It should be green, I think. What do I lack for it to work?

---

### Post by lsutiger on 2007-03-13
Hmmm..I will try to help ya. I have an Acer Aspire 3000. My light for wireless is on the front panel and is Solid Orange ( in Windoze it blinks if it is not connected ).  
Are you near a wireless source? If so, is this wireless source open or have WEP,WPA, etc ? If it is protected, go ahead and disable security ( just to test ).
What do you get from ifconfig?
Can you ping the router?

---

### Post by Irid on 2007-03-16
I have a solid orange light, too. I'm near a Wi-Fi source, it requires a password and username, I know them, but I don't know where to enter them. Here's what I get by typing sudo ifconfig.
```

eth0      Link encap:Ethernet  HWaddr 00:16:CF:7C:F8:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Memory:d0100000-d0102000 

eth1      Link encap:Ethernet  HWaddr 00:16:36:90:E7:13  
          inet addr:10.0.0.40  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::216:36ff:fe90:e713/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10975575 (10.4 MiB)  TX bytes:9092877 (8.6 MiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

```

I don't know how to ping router, though.

---

### Post by lsutiger on 2007-03-28
I am sorry for the delayed response. You are connected. If you look under the eth1 listing, you have an ip address.
Where you go to configure the password and ESSID is System, Networking. Choose your Wireless Connection, Properties. Enter the information there.I am not sure if this works with WPA or WPA2.

But what is strange is that your listing in ifconfig is that you have an ip and had packets to and from your computer.

Hope this helps some.

---

