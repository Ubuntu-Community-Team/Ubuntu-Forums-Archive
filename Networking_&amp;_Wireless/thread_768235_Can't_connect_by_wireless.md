---
title: "Can't connect by wireless"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Kazoo2k on 2008-04-26
Hey everybody, I'm new to the forum!

My name is Joe, nice to meet you all! To get to the point, here's my problem;

I recently installed Ubuntu and everything works perfectly, except the one thing I would really like access to; the internet!

Now, my current wireless network was sensed by previous Windows network connection, and I could connect to it successfully. My Playstation 3 also senses it and connects to it successfully.

Ubuntu *can* sense my wireless network, but *cannot* connect to it. On the desktop drop down list (top right) I click on my wireless network, it asks me for the WEP key, which I have double checked a million times, and still no luck. The connecting icon comes up (the two grey spheres with the blue tadpole shaped object flowing through them), but after that, it either;

A) Asks me for my WEP key again (this is usually after the first attempt)

B) Just goes back to the "not connected" state, meaning the icon of the PC with the red X on it.

The WEP key isn't the problem. I have tried numerous times to connect through the Terminal by a tutorial as well, but no luck.

Any ideas, people? I would be exceptionally grateful if somebody could shed some light on this problem.

Thank you for your time in advance!

Joe

---

### Post by kai60 on 2008-04-26
Hi mate,

can you give us a bit more information about your wireless card, more specifically the chipset, you can get this through
```
lspci
```

If you want to post that back, we'll see how we go...

---

### Post by Kazoo2k on 2008-04-26
Hey Kai,

Just typed in lscpi into the terminal, and this is what came back, I'm not sure what it is specifically you need to see but I'm sure you can locate it here somewhere;


00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:0a.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter

Thanks!

---

### Post by kai60 on 2008-04-26
That doesn't list the wireless card, which means that if you have a laptop, you might have a pcmcia card. 

However something that might also help is to do a search on your model card in google and your distro version.

---

### Post by Kazoo2k on 2008-04-26
Nah, it's not a laptop, just a regular desktop PC. 

One thing I should note is that there are two PC's; the computer I use senses the signal from the PC in the other room so the main wire *isn't* connected to my PC. Don't know if that makes any difference.

Any idea what I should search for to locate this model card and distro version? Would there be any information on the main wireless box sending out the signals?

Eagerly awaiting your reply, thanks for your help so far!

---

### Post by kai60 on 2008-04-26
Hi mate,

I guess that the first thing that you should is to tell me whether you are running Ubuntu 7.10 or 8.04.

As some cards are not displayed in 8.04 at all for some reason, but I am a bit worried that you haven't got it listed as a PCI card in the list.

We'll take it from there. Also, you could open the box and then physically check the card.

Good luck.

---

### Post by Kazoo2k on 2008-04-26
Haha, didn't know there was an 8.04, is it beta or something?

Anyway, I'm 7.10.

---

### Post by kai60 on 2008-04-26
Alright, now you said that you have had it working before? Who made your wireless card? Without this, there is not much that I can do to help you. You may have to actually open up the box and have a look. Even a brand is somewhere to start.

Cheers

P.S.: 8.04 is about 1 day old and it is a good release, but lets work on getting your wireless set up first. Then we'll worry about any more distro updates...

---

### Post by Kazoo2k on 2008-04-26
Hey again!

I have been speaking to my brother who is very computer literate in terms of Windows, but when it comes to Linux he says he wouldn't know where to start; however he told me to check the USB stick that senses the signal from the main box, and on the stick is proclaims that;

Netgear WG111v2 is the make.

Does that help at all?

---

### Post by kai60 on 2008-04-26
Hi mate,

had a bit of a search and I came up with this link for you to see if you can get on and get some more information in regards to getting it set up.

[http://ge.ubuntuforums.com/showthread.php?t=51993](http://ge.ubuntuforums.com/showthread.php?t=51993)

I am sorry, but I actually know nothing about the Netgear dongle. I agree with a lot of the posts though that it should work out of the box for you.

A command that might help you is 
```

lsusb
lsmod

```

Good luck and let me know if I can do anything else to help you mate.

---

### Post by Kazoo2k on 2008-04-26
Hey Kai, trying all I can do get this working...

I just found some sort of chipset name;

Realtek 8187 

Any idea?

---

### Post by kai60 on 2008-04-26
Hi mate,

try this

[http://ubuntuforums.org/showpost.php?p=3945998&postcount=13](http://ubuntuforums.org/showpost.php?p=3945998&postcount=13)

I hope that you have some joy. :)

---

