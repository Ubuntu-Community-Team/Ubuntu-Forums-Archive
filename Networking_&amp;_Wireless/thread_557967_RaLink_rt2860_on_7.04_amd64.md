---
title: "RaLink rt2860 on 7.04 amd64"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by timmahcheese on 2007-09-23
Hey guys,

Here's what I'm working with:
Ubuntu Desktop 7.04 amd64
AMD Athlon 64 X2 4800+ Brisbane 2.5 GHz (ADO4800DDBOX)
Edimax EW-7728In a/b/g/n PCI card (RaLink rt2860 chipset)

Initially I decided to go the easy approach, with ndiswrapper, but the Edimax driver cd and Edimax support page contain no actual drivers, just an exe setup utility (which I failed to extract anything with using cabextract, thinking it may be a cab that the drivers are hidden in). I then installed the card on my Windows XP machine, then manually found the .sys and .inf files, but these were useless as they were 32-bit and wouldn't work with ndiswrapper on my 64-bit processor.

At this point discovering that the card had an RaLink chipset, I found what looked to be a godsend in the form of Linux source code for the rt2860 driver at [http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html"). I've successfully compiled the .ko file, but unfortunately that's where the success has stopped. Here are the instruction I followed:

```
$/sbin/insmod rt2860sta.ko
$/sbin/ifconfig ra0 inet YOUR_IP up
```

Which I executed as:

```
sudo /sbin/insmod rt2860sta.ko
sudo /sbin/ifconfig ra0 inet MY_IP up
```

Replacing MY_IP with the desired static ip for the card.

This causes ssid's to populate when I run wifi-radar, but I am unable to connect to any of them. This also makes the Wireless Connection show up in the Network Manager GUI, but I am also unable to connect to a network through that. This also causes my ethernet connection to malfunction until I disable the wireless driver.

I figured maybe the driver would work if it loaded at boot, but the README provided with the code is written for RedHat, and I am not familiar with the Ubuntu equivalents for some of the configuration steps (i.e. /etc/modules.conf and /etc/sysconfig/network-scripts/):

```
If you want for rt2860 driver to auto-load at boot time:
A) choose ra0 for first RT2860 WLAN card, ra1 for second RT2860 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2860sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     

NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
```

The way I see it, I have 2 possible fixes:

1) Somebody out there has run the Edimax installer ([http://www.edimax.com/images/Image/Driver_Utility/Wireless/NIC/EW-7728In/nMAX7728In_Eng_Utility_V1.0.zip]("http://www.edimax.com/images/Image/Driver_Utility/Wireless/NIC/EW-7728In/nMAX7728In_Eng_Utility_V1.0.zip")) on Windows XP 64-bit and can provide the .sys and .inf files for use with ndiswrapper

OR, preferably

2) Somebody can point me in the right direction on getting the RaLink-provided Linux source code for the driver operational and loaded at boot.

Thanks very much in advance for any help or advice!
-Tim

---

### Post by timmahcheese on 2007-09-23
Update (Got it working):

I ended up installing a trial version of Windows XP Professional x64 Edition, installing the card, loading the 64-bit driver files out of C:\Program Files (x86)\Edimax\Driver onto a USB key, switching back to Ubuntu, and loading the driver into ndiswrapper. I then got a wlan0, configured it with iwconfig, and everything seems to be working great.

---

### Post by timmahcheese on 2008-07-07
There's been a lot of private message requests for these files, though I'm not sure I'm able to freely distribute them myself. I will, however, provide this attached zip archive. The archive contains a file with a .mono extension which is in no way statistically related to the driver files. Given the right program, and using a little "standard practice," however, you might find another zip archive with something useful ;)

---

