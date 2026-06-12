---
title: "Unable to connect to wifi."
date: 2011-05-25
forum: New to Ubuntu
---

### Post by John Phang on 2011-05-25
Hi there, recently i've migrate from Lubuntu 10.10 to xubuntu 11.04 but after the installation I couldn't connect to the wifi network that i've been using on Lubuntu 10.10. What should I do to make it work? and xubuntu 11.04 is not working very smooth on my laptop but why? My system is Intel celeron 1.66mhz,20gb HD, a trident graphic card and 1gb ram. I'm using Toshiba satellite pro 6000 a very old laptop.
can anyone please help me out?

---

### Post by gandaran on 2011-05-25
> **John Phang said:**
> Hi there, recently i've migrate from Lubuntu 10.10 to xubuntu 11.04 but after the installation I couldn't connect to the wifi network that i've been using on Lubuntu 10.10. What should I do to make it work? and xubuntu 11.04 is not working very smooth on my laptop but why? My system is Intel celeron 1.66mhz,20gb HD, a trident graphic card and 1gb ram. I'm using Toshiba satellite pro 6000 a very old laptop.
can anyone please help me out?
do you remember if you had to install wireless drivers in 10.10?
what brand and model of wireless card do you have?
use this for hardware info
```
lspci
```

---

### Post by John Phang on 2011-05-25
> john@ubuntu:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

this is what it shows after i enter the code you gave me.

---

### Post by gandaran on 2011-05-25
doesn't show any wireless controller, post the output of 
```
lsusb
```

---

### Post by John Phang on 2011-05-25
> john@ubuntu:~$ lsusb
Bus 001 Device 003: ID 0e8f:0023 GreenAsia Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

this is lsusb shows.

---

### Post by gandaran on 2011-05-25
well, your xubuntu 11.04 ins't detecting any wireless/network controller, only detects the ethernet controller, are you sure the card isn't broken or something? sorry I cant help here.

---

### Post by John Phang on 2011-05-25
But it could sense the wireless network, the problem is when i click on the wireless network it didn't do anything it doesn't ask me to insert password to try to connect it. Please, please help me out... you are my only hope...

---

### Post by gandaran on 2011-05-25
> **John Phang said:**
> But it could sense the wireless network, the problem is when i click on the wireless network it didn't do anything it doesn't ask me to insert password to try to connect it. Please, please help me out...
you can see your wireless network (SSID) in the network panel icon?
try making the setup connection manually with the SSID and password and mark the box connect automatically then watch if it connects.
also try this in terminal, post the output if it didn't work.
```
sudo ifup wlan0
```

---

### Post by John Phang on 2011-05-25
Yes i could see the SSID in the network panel icon. i've try to make the setup manually but it still not connecting. and when i enter (sudo ifyp wlan0) it shows :
> john@ubuntu:~$ sudo ifup wlan0
[sudo] password for john: 
Ignoring unknown interface wlan0=wlan0.


---

### Post by rsw1965 on 2011-05-25
Assume that in the user and groups setting under system administration - the user account that you are operating on has had the check box ticked for "connect to wireless and ethernet networks" under the advanced settings and that you are using the main account on the computer? Are you able to connect on that PC via ethernet? You may also want to check the other advanced settings for the user account.

rsw65

---

### Post by gandaran on 2011-05-25
> **John Phang said:**
> Yes i could see the SSID in the network panel icon. i've try to make the setup manually but it still not connecting. and when i enter (sudo ifyp wlan0) it shows :
that is very strange, you can see the SSID network but the wireless interface isn't detected! sorry, you'll have to wait for someone with more experience to help you.

---

### Post by John Phang on 2011-05-25
rsw1965: yes i'm using the main account of this computer, and i'm able to connect to the internet using ethernet. PS: that day i've change my router aztech to a new one and the password and everything remains the same. I'm using TP-LINK_ED37CD. Is it my router that cause all these problems?
Gandaran: Thanks for help... Thank you.. :)

---

### Post by rsw1965 on 2011-05-25
Not sure of the effect of the replacement router unless perhaps you are using the same text password - but the encrypted versions are different? - really guessing at that one. Suggest you may need to close this thread or relocate it to Networking and Wireless Forum as the topic seems to have gone beyond what we can do in this forum.

rsw1965

---

### Post by John Phang on 2011-05-25
rsw1965: I'll try what you say, and i'm so sorry about my english, anyways thank you... for helping me out... :)

---

### Post by Joe of loath on 2011-05-25
The card may be a pcmcia card, in which case lspcmcia will show any devices there may be.

---

