---
title: "LinSSID finds no wireless interface"
date: 2017-07-23
forum: Networking &amp; Wireless
---

### Post by col48 on 2017-07-23
Running 16.04 Xenial 64-bit (& software updater tells me my system is up to date).
The computer has a wired connection to the router.

Recently we updated the OS on an Android device linked wirelessly to the network after which the signal seems to be much weaker to that device.  So have added a Range extender (no convenient sockets to use a powerline option) which has improved things a little.

I want to look at the network, so installed linssid using the commands at the end of post #2 to this thread:
[HTML]https://ubuntuforums.org/showthread.php?t=2324016[/HTML]

Synaptic says this gives me version 2.9 (in place of 2.7.3 without the specific ppa).

But both the 2.7.3 and the 2.9 versions (run as root) quit almost instantly with a popup:
```
Unable to continue
No wireless interfaces found

```

Is this what I should expect, given that ***the computer itself*** is not connected wirelessly?

I would prefer to investigate from this computer rather than from the other device if I can, because it is not my device and I am not really at home with it - also the owner can be a bit sensitive....

Any advice would be appreciated.

---

### Post by Hadaka on 2017-07-24
.

---

### Post by chili555 on 2017-07-25
> The computer has a wired connection to the router.And then:> Unable to continue
No wireless interfaces foundThat implies that there is either no wireless device installed on the computer or, if there is, it lacks a corresponding driver. Let's see what you have. Please run and post:```
lspci -nnk | grep 0280 -A3
```I am assuming that you don't have a USB wireless device, but let's make sure; run and post:```
lsusb
```You probably can get all the information you want about signal strength from Network Manager once you have a working wireless:```
sudo nmcli dev wifi list

```Here is a sample from my machine:```
*  SSID        MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
   GBR1        Infra  6     54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2      
*  GBR5        Infra  149   54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA2      
   nx2.4       Infra  1     54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 
   MC5         Infra  149   54 Mbit/s  40      &#9602;&#9604;__  WPA2      
   MC1         Infra  11    54 Mbit/s  39      &#9602;&#9604;__  WPA2      
   Portal      Infra  11    54 Mbit/s  29      &#9602;___  WPA2      
   MAHB Wi-Fi  Infra  6     54 Mbit/s  20      &#9602;___  WPA2      
   nx5g        Infra  36    54 Mbit/s  19      &#9602;___  WPA1 WPA2 
   --          Infra  11    54 Mbit/s  17      &#9602;___            
   MAHB Wi-Fi  Infra  6     54 Mbit/s  12      &#9602;___  WPA2      

```

---

### Post by col48 on 2017-07-25
Hi chili555

The lspci command produces no output at all (in zero time)

lsusb:
```
Bus 002 Device 004: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 003: ID 13ee:0001 MosArt Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I guess that means I don't have a wireless device...
But I do have a free usb port, so could I get something to plug in to enable me to get the info I want?
I am not at home with hardware, so don't want to open the box if I can avoid it.
The sample output you posted is exactly the kind of thing I would like ideally.

---

### Post by chili555 on 2017-07-25
> I guess that means I don't have a wireless device...Correct.> But I do have a free usb port, so could I get something to plug in to enable me to get the info I want?Yes you can. Be sure to get a device that is fully supported by default or, as they call it in other places, plug-n-play. This post may be helpful to you in finding one.

[https://ubuntuforums.org/showthread.php?t=2359573&p=13639455#post13639455](https://ubuntuforums.org/showthread.php?t=2359573&p=13639455#post13639455)

---

### Post by col48 on 2017-07-26
Many thanks.

I'll marked this as 'solved', although 'question answered' might describe it better!

---

