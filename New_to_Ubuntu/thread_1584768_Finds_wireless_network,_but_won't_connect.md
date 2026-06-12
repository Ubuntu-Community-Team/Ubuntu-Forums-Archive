---
title: "Finds wireless network, but won't connect"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by totallybeachin on 2010-09-29
I am new to Linux, so I thought I would start in the Absolute Beginner section. If there is a different thread I should post in, please let me know.
I am trying to run Ubuntu 10.04 Lucid Lynx through the Wubi download. I have been trying to get my wireless to work, but can't figure out what's going on. I installed the proper driver, (or so I think, anyway) and my network shows up, but when I try to connect, it looks like it is connecting, lights flashing on the little radar thing, but I always get a pop up message that says "Wireless Network Disconnected you are now offline " 
I have tried different commands from other posts that I was able to find while searching, but nothing ever addressed my situation and nothing has worked so far. 
Anyone have any suggestions?

---

### Post by totallybeachin on 2010-09-29
Wow! No one? Nothing? Is there anything else I can post that would help? I apologize if this is posted in the wrong spot. Just tell me where to go and I will gladly oblige. 
This is driving me nuts!!!!

---

### Post by Miljet on 2010-09-29
You are in the right place. Most of the people who post on here, myself included, do not use WUBI and therefore are not familiar with it. You will just have to be patient until someone who knows something about both WUBI and wireless networking sees your post.

This post will bump your thread back to the top. Keep bumping it about every 24 hours until someone sees it who can help.

---

### Post by Hippytaff on 2010-09-30
What are you using to connect - usb dongle, wireless card?
 
can you connect with other os?

---

### Post by totallybeachin on 2010-09-30
> **Hippytaff said:**
> What are you using to connect - usb dongle, wireless card?
 
can you connect with other os?
I don't know what usb dongle is..lol...sorry. So I guess I will have to say my wireless card. It is a Broadcom 1325 or something like that. I downloaded the "appropiate" driver for Unbuntu.....I think. I have that little green radar antenna looking thing along the top, right hand side, that I can click on and see my wireless network. I click on it to connect, but it fails. 
As far as other OS, well, yes. Windows connects just find. No problems at all there. 

And thank you for replying. I was starting to think no one out there could/would help me!

---

### Post by Hippytaff on 2010-09-30
I'm not expert, but if you post the results to these commands, then someone with a bit more know how might be able to work out what the problem is (assuming you ahve the right driver-  
 
 Check the interface with
 
```
 
iwconfig

```
 
network scan
 
```
 
iwlist scan

```
 
wireless brand etc
 
```
 
 
lspci -nn

```

---

### Post by Hippytaff on 2010-09-30
...and maybe the output for this too
 
```
 
dmesg | grep -e ndis -e wlan

```
 
...and (the more info the more people have to go on to help diagnose the problem)
PC manufacturer etc

---

### Post by totallybeachin on 2010-09-30
> **Hippytaff said:**
> ...and maybe the output for this too
 
```
 
dmesg | grep -e ndis -e wlan

```...and (the more info the more people have to go on to help diagnose the problem)
PC manufacturer etc

this is going to sound silly, but how do I type that straight up/down line?

---

### Post by totallybeachin on 2010-09-30
Also, I just want to add, that I will add the reports as best I can. 
As it stands right now, the only internet I have is a wireless connection, and 2 laptops. 
I  have Ubuntu open on the one I am trying to troubleshoot, and the one I  am using to connect to this forum. I have to type the command results  back in here, rather than being able to copy and paste. 
May take a while. Or I may just have to go to my in-laws house and hard wire the Ubuntu computer into the internet. 
Either way, I will post the results!

---

### Post by totallybeachin on 2010-09-30
ok, here are a few reports:

> iwconfig
lo          no wireless extensions

eth0     no wireless extensions


eth1     IEEE 802.11   Access Point: Not- Associated
            Link Quality:5  Signal Level:0 Noise Level: 168
            RX invalid nwid:0   invalid crypt:0   invaild misc:0
> iwlist san

lo       Interface doesn't support scanning

eth0   Interface doesn't support scanning

eth1   Interface doesn't support scanning

As for the "lspci -nn" command, well that will take a while to post, but I will get it here as soon as possible.

---

### Post by Hippytaff on 2010-09-30
Bit of a potch for you, haven't you got a usb pen drive...could copy them over to the online box then!?

---

### Post by Hippytaff on 2010-09-30
Is wireless on? the up and down line is on the left of 1 key on my keyboard

---

### Post by debasishg on 2010-09-30
what is the make of your wifi.. 
```
lspci | grep -i network
```

i had the same with my broadcom which was rectified thru hunting google.

---

### Post by totallybeachin on 2010-09-30
> **Hippytaff said:**
> Bit of a potch for you, haven't you got a usb pen drive...could copy them over to the online box then!?
Absolute genius!! It's the simplest things that escape me sometimes when I am focusing on something else!!
Ok, so I was going to try it. Was able to copy and past the results into an OpenOffice Word doc., but when I put the pendrive in my other comp. I couldn't open it. Even tried to rename it .doc. 
It was then recognized as  a word doc, but word failed to open it. Any other suggestions??

Also, the button to the left of my 1 looks like these:
`      without shift
~      with shift

Yes, the wireless is on. Had just been playing around the web through windows on that comp. when I seen your post about the pendrive. Switched it back over to Ubuntu to get the results copied......and well, here we are now. 

Going to mother in-laws house in about 10 minutes time. Will hard wire into internet as soon as I get there. 
Maybe I will then be able to just copy/paste that command with the straight up/down line.

---

### Post by totallybeachin on 2010-09-30
> **debasishg said:**
> what is the make of your wifi.. 
```
lspci | grep -i network
```i had the same with my broadcom which was rectified thru hunting google.
I hunted on google for days. And every thing I found always brought me to this website. But none of the suggestions I had found fixed my situation. 
I will try to post the results of the command you are requesting as soon as I can get hard wired into the internet and can copy/paste the command. I don't know how to type the straight up/down line.:confused:

---

### Post by totallybeachin on 2010-09-30
ok, here the results from lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)


I am working on the other command. It will not allow me to copy/paste.
Well, it will, but when I paste it into the terminal, it doesn't do anything. Just goes back to waiting for a command

---

### Post by migs73 on 2010-09-30
for the | sign try shift+backslash (to the left of the z), that is where it is on my keyboard. If not try the same button as last time but press AltGr at the same time.

---

### Post by totallybeachin on 2010-09-30
ok...for what it's worth, I got the | figured out..........lol...............now for the result of that command:
lspci | grep -i network
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

As for the other command, dmesg | grep -e ndis -e wlan,
I don't get anything
Should I be getting something?

---

### Post by totallybeachin on 2010-09-30
Ok, so here's where I am now.
I was able to get my wireless working.....at my mother in-laws house, connecting to her wireless network.
I followed the step outlined here:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Kinda good news, however, MY wireless network is through WMWifiRouter and it is not connecting?????

Any ideas at all. This is the only internet connection I have at my house and I REALLY need to be able to connect that way. It's my only option.

---

### Post by totallybeachin on 2010-09-30
I found this, but I don't know what any of it means, and I am afraid to do it because I am scared that it will undo all the things I did from the previous post that finally got it to connect to anything!!
What are your thoughts on this?

try this.. may work.. first try to find out which interface is your wifi  interface. then set it to adhoc mode first by typing the following
1)sudo ifconfig eth1 down
2)sudo iwconfig eth1 mode ad-hoc
3)sudo iwconfig eth1 essid 'wifinetworkname' 
4)sudo ifconfig eth1 up

---

### Post by totallybeachin on 2010-09-30
Ok, well, for lack of patience, I went ahead and tried the commands in the previous post.
Did a system restart, and waited to see if it would connect. 
It didn't.
But, I right clicked on the wifi antenna thing and went into edit connections. I found my WMWifiRouter connection, clicked edit, went to IPv6 settings. This was on automatic. I changed it to ignore, and Voila! I am currently connected through my wifi network. 
Not sure if I will still be able to connect on any other connection, as it appears to me that I have changed the setting to only connect through ad-hoc. Don't know if that is the case or not. 
Seeing as how I usually only connect through my own network, don't think it will really matter to me. 
I can find out later when I go to the library if I am able to connect there.
Thanks for any/all help.

If nothing else, at least by having me type those commands, it gave me ideas on what specific things to google!!! 

Now, I just have to have fun learning all about linux. So far, I am liking what I see.

Thanks again.

---

### Post by debasishg on 2010-09-30
gr8 .. i am having the same network pci mate and was not able to get connected ... though my problem was resolved while activating **STA** driver in restricted hardware section.

happy surfing.

---

### Post by Hippytaff on 2010-09-30
Perseverance will succeed :-) (usually)

a job well done!

---

