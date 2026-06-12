---
title: "RTL8812AE drivers in 18.04 and 20.04"
date: 2020-11-08
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2020-11-08
I have a PCIe wifi card with the Realtech RTL8812AE chipset. It used to work but recently stopped working. I see a lot of questions about that chip set but for 18.04 I was wondering if it is resolved in 20.04? I was planning on a release upgrade and if that will fix it I can just go ahead and do it now.

I have determined my hardware is identified and the driver rtl8821ae appears loaded. The Wifi is unmanaged but I'm not seeing any networks.

---

### Post by mastablasta on 2020-11-09
have you looked at this: [https://forums.linuxmint.com/viewtopic.php?f=53&t=204172&start=80](https://forums.linuxmint.com/viewtopic.php?f=53&t=204172&start=80)

did you load any realtek drivers? i had to turn off secure boot and patch the kernel to get the chip working. 

i think driver might be in newer kernel, so maybe try using HWE kernel first. here is how to do it: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by rsteinmetz70112 on 2020-11-09
I have not loaded any extra drivers in 18.04.
Your first link is from 2017, so may be obsolete.
There is a references rtl8812au driver in the 20.04 Universe repositories, but it seems to be source.
Some references suggest the rtl8821 driver also works for the 8812AE
It's all very confusing.

---

### Post by rsteinmetz70112 on 2020-11-09
OK 
I've upgraded to 20.04 and still no joy.
I'm almost beginning to think the radio in the card is dead.
I did get a USB dongle to work.

---

### Post by mastablasta on 2020-11-10
mine is meant for 18.04 but i am on 20.04. but driver is a driver. you patch kernel with it and it should work.
what about:
[https://askubuntu.com/questions/1075086/ubuntu-18-04-no-wi-fi-adapter-found-realtek-driver-rtl8821ae](https://askubuntu.com/questions/1075086/ubuntu-18-04-no-wi-fi-adapter-found-realtek-driver-rtl8821ae)

drivers are made and then they need to be checked and all that to be stable before they are added to the kernel. sometimes they are never added.

---

### Post by rsteinmetz70112 on 2020-11-25
OK I followed the instructions in the link. It seems to work, but the card is still not working. I think it's broke. Off to get a new one.

---

### Post by Raffles727 on 2020-11-25
> **rsteinmetz70112 said:**
> OK I followed the instructions in the link. It seems to work, but the card is still not working. I think it's broke. Off to get a new one.

Keep us posted.

---

### Post by rsteinmetz70112 on 2020-11-27
OK I've gotten another card with an IBM chip set. Same problem persists.
I run the wireless info script abut paste bin won't load it. Using pastebinit -i I don't get the file name back.
```
pastebinit -i /home/rob/wireless-info.txt
http://paste.ubuntu.com/
```

---

### Post by rsteinmetz70112 on 2020-11-30
OK I finally got pastebin to work.
Here is the wirelessoinfo-txt
[https://paste.ubuntu.com/p/jvGvJ5JTwT/](https://paste.ubuntu.com/p/jvGvJ5JTwT/)

---

### Post by CelticWarrior on 2020-11-30
> [COLOR=#000000]OK I've gotten another card with an IBM chip set.[/COLOR]
No, you didn't. IBM doesn't do WiFi chipsets. Your new one is clearly identified as:
```
[COLOR=#000000]Intel Corporation Wireless 7265 [8086:095a] (rev 61)[/COLOR]
```
Unlike some Realtek ones and an handful of others from other manufacturers, Intel WiFi just works.

I wonder what's the problem now? The script result shows it's working and connected to "[COLOR=#000000]SBG6700AC-9CBA4".[/COLOR]

---

### Post by rsteinmetz70112 on 2020-11-30
Sorry, I got excited. It's an Intel chip, which I specifically looked for. It also has Bluetooth and that's working.

I agree it looks like the hardware is connecting but somehow it's not sending anything to the operating system.

What is happening now is that the little status icon in the upper left corner shows the wifi is not connected. 
It does show the USB wifi is connected.

No networks are listed in the select a network window.
```
ifconfig -a

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9c:29:76:0c:e2:cf  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

It doesn't show a IPV4 address and shows no traffic.
I now think this is what has been happening all along and may be related to changes in the networking from 18.04 to 20.04.

---

### Post by rsteinmetz70112 on 2020-11-30
I guess I forgot to post the response.

I got excited it is and Intel chip set, which I purchased especially. It has Bluetooth also.
The Bluetooth works.

When I look at my desktop the little drop down shows two wifi adapters, a USB which is connected and the PCIe car with no connections.
If I select  the PCIe and look at available networks I don't get any.
If I do run ifconfig -a The adapter shows up but doesn't have an IPV4 address and shows not traffic in either direction.

---

### Post by rsteinmetz70112 on 2020-12-09
I'm back at this after some time away from the site.

When I originally posted thread I thought the problem was the drivers for a realtek chipset on a PCIe WIFI card. I worked through the various fixed and suggestions related to that card. I decided the card was probably defective and got another card with Intel chipset. It exhibits the same problem.

I cannot connect to a WiFi network with the PCIe card, when I look the GUI does not show any available networks and does not connect although various command line utilities recognize the card, list is options and show it can see various networks but a USB Wifi device connects (I've used 2 different ones with different chipsets).

The issue must be somewhere in the network configurations but I'm not where where to look. It appears to have started with the upgrade from 18.04 to 20.04, but I can't be sure.

---

### Post by CelticWarrior on 2020-12-10
In order to be sure: Boot a live session of Ubuntu 20.04.

---

### Post by rsteinmetz70112 on 2020-12-11
DId that and the PCIe card worked just fine. I simply had to enter the password for the WiFi network.

---

### Post by rsteinmetz70112 on 2020-12-14
Turns out the problem was not hardware realated at all. See my other thread fro a continuation. [https://ubuntuforums.org/showthread.php?t=2455149](https://ubuntuforums.org/showthread.php?t=2455149)
I'm marking this one solved.

---

