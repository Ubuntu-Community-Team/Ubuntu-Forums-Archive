---
title: "New Ubuntu user needs help connecting wireless"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by ibcrusn on 2010-06-09
A little background...I originally installed Xubuntu on my old Toshiba Satellite 2805-S202 laptop. It functioned very well on its own compared to the bloated XP Pro it had previously installed. Despite the ease of use for what came installed being unable to figure out how to setup the wireless card made it more of a boat anchor  than a usable computer. I got frustrated because I don't know code and have little desire to learn (thank you MS for the brainwashing). So it sat for a few months unused. 

Fast forward to a couple weeks ago and I decided it was time to give it a go but make some changes. I decided to go with the standard Ubuntu with the Gnome GUI and I really like it, it functions really well on the old computer. However, as mentioned earlier a computer that's unable to connect to the internet is pretty useless for the average user. I have tried for over a week to figure out the multiple methods found to install Ndiswrapper and the Linksys driver to no avail. 

I'm not remotely into code, I do not see the world through 1's and 0's but I do learn software very easily and become proficient quickly. Which brings me to my current state, a desire to run and learn more about Ubuntu and Linux but I'm in over my head and need some help. I'm not a total dummy, I'm here looking for answers and help and if I get a little hand holding to get me started I'll pick it up. If I can't get this figured out I'll probably stick with XP & 7 for the foreseeable future. Any assistance would be greatly appreciated. 

Thank you much in advance.

---

### Post by cbecker78 on 2010-06-09
With the name of your wireless card (and/or) chipset, we can probably help you get it going.  So what's the make/model, and is it using an old plug-in card, a usb dongle, or a built-in?  Sounds like one of the first two if its a linksys.  The chipset is usually printed on the bottom of the card, but can probably be found via google if necessary with the make and model number of your card...

---

### Post by drpjkurian on 2010-06-09
Hi 
First try to find out what is your wireless card(I mean the make). Browse for the driver and install it.

Please type the command ```
lspci
``` in terminal to know the wireless card.
If it is atheros you can try madwifi drivers..

---

### Post by ibcrusn on 2010-06-09
I knew I left something out. It's a Linksys WPC54G V2 with a TI chipset (104C:9066). 

I have the driver on a USB flash drive as well as the ndiswrapper. I have had zero luck getting the ndiswrapper to load without which from whta I've read I cannot then install the WPC54G V2 driver. I've tried following others steps for the code in the terminal but it doesn't work.

Let me ask another question. Is there a pcmcia wireless card that is natively supported? At this point $10-20 would be better spent on something known to work so I can get my feet wet on something easier as far as installations go.

---

### Post by mastablasta on 2010-06-09
> **ibcrusn said:**
>  
Let me ask another question. Is there a pcmcia wireless card that is natively supported? At this point $10-20 would be better spent on something known to work so I can get my feet wet on something easier as far as installations go.
 
 
I have one. I am not sure but i think it's lynksys. works well with all Ubuntu based distributions i tried.

---

### Post by roger_1960 on 2010-06-09
Hi

I have 2 old laptops running with Belkin PCIMIA cards with RaLink RT2500 chipsets.  These have worked with no messing around with all Ubuntus since 7.04

---

### Post by Peter09 on 2010-06-09
It would be good to see the output of
```
lspci
```
and
```
ifconfig
```
 
You can get this output into a file by using the commands
 
```
lspci >~/Desktop/lpspc.txt
```
and
```
ifconfig >~/Desktop/ifconfig.txt
```
you can then copy to any other machine to put here.
 
By the way, have you connected through a hardwired link and done and update - some drivers are downloaded during this process and you may not get a wireless link working until you do.

---

### Post by ibcrusn on 2010-06-09
I wish it were as simple as getting on the forum with that computer but the 10/100 card was removed some time ago due a defect in the card so the Toshiba currently has no internet access. I'll get the info posted tonight.

---

### Post by bksalt on 2010-06-09
Why don't you contact a local Linux Users Group [lug] and bring your laptop to a meeting they can help you. Wish more people would use there local club.

Bert

---

### Post by cbecker78 on 2010-06-09
Also, in addition to above, look [here ]("http://ubuntuforums.org/showthread.php?t=5645")at post 4.  Though that may already be what you are doing...

---

### Post by ibcrusn on 2010-06-09
bksalt,
 
Thanks for the idea that was what I was looking for, someone local that can run me through the process. Only bad news is the local user group has pretty much dried up but I'll post up and see what happens.

---

### Post by anewguy on 2010-06-09
As far as ndiswrapper goes, there are 2 things to be aware of:

(1) the Windows driver you are using should be the Windows XP driver

(2) installing ndisgtk provides a GUI'd front-end to ndiswrapper.  You won't have to do all of the command line stuff.  Just start up ndisgtk, remove any existing connections, then add a connection and point it at your Windows driver and you're done.

Dave ;)

---

### Post by ibcrusn on 2010-06-10
Okay here goes. The last two didn't do anything. I didn't have time tonight to find ndisgtk and try to install it, maybe tomorrow or the weekend. I hope this helps. If there is anything else let me know. Thanks.

lspci

```
kris@kris-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 20)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```ifconfig

```
kris@kris-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```lspci >~/desktop/lpspc.txt

```
kris@kris-laptop:~$ lspci >~/desktop/lpspc.txt
bash: /home/kris/desktop/lpspc.txt: No such file or directory
```ifconfig >~/desktop/ifconfig.txt

```
kris@kris-laptop:~$ ifconfig >~/desktop/ifconfig.txt
bash: /home/kris/desktop/ifconfig.txt: No such file or directory
```

---

### Post by steveneddy on 2010-06-10
It may be easier if you copied that driver to your /home folder that keeping it on the USB drive.

That would solve one of your issues. Otherwise you would have to use that USB stick every time you needed to use the driver - I think.

Better to put it in /home anyway.

---

### Post by 3rdalbum on 2010-06-10
Buying a $200 copy of Windows 7 is more expensive than buying a $22 high-signal-strength wifi card that is Linux-compatible.

At the bottom-right of this page: [http://www.chrislees.info/ubuntu/index.shtml](http://www.chrislees.info/ubuntu/index.shtml)

Most of us have bought cards (or had already owned them) that work out-of-the-box; it just makes things easier.

---

### Post by mastablasta on 2010-06-10
Just an update. I don't have lynksys as i wrote before but TP-LINK card. Model is TL-WN610G (108Mbps)

---

### Post by ibcrusn on 2010-06-10
> **steveneddy said:**
> It may be easier if you copied that driver to your /home folder that keeping it on the USB drive.

That would solve one of your issues. Otherwise you would have to use that USB stick every time you needed to use the driver - I think.

Better to put it in /home anyway.

I have a copy on the desktop, it's still on the usb stick because that's the easiest way to transfer files at this point. I will move the copies of the driver and ndiswraper to the home folder though as you mentioned.

> **3rdalbum said:**
> Buying a $200 copy of Windows 7 is more expensive than buying a $22 high-signal-strength wifi card that is Linux-compatible.

At the bottom-right of this page: [http://www.chrislees.info/ubuntu/index.shtml](http://www.chrislees.info/ubuntu/index.shtml)

Most of us have bought cards (or had already owned them) that work out-of-the-box; it just makes things easier.

My 64bit desktop machine has been upgraded to 7 for a while. The Toshiba is more of an experiment to become accustomed to Ubuntu before I migrate the wife's laptop and the desktop.

Good point on the wi-fi card. I would like to figure this out though, it has more to do with the learning and principal of it all.

---

### Post by Peter09 on 2010-06-10
Here is a thread where someone seems to have had some success getting and ACX11 card working
 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1130064](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1130064)

---

### Post by ibcrusn on 2010-06-10
Although I do want to learn how to make the Linksys card function I have ordered a Trendnet TEW-441PC card for $20 shipped which has Linux drivers readily available.
 
The desire to make the Linksys card work goes more to understanding the Ubuntu Linux thing as a whole and it's quickly becoming a principal thing.

---

### Post by ibcrusn on 2010-06-11
> **steveneddy said:**
> It may be easier if you copied that driver to your /home folder that keeping it on the USB drive.

That would solve one of your issues. Otherwise you would have to use that USB stick every time you needed to use the driver - I think.

Better to put it in /home anyway.

I'm at a loss here. I know where my \home folder is but should there be a specific folder I save the files to? 

Secondly, per anewguy's recommendation I have tried to install ndisgtk but have not had any luck. The guides I have found seem to assume you already have internet access to directly download what you want from a repository using the synaptic package manager. I even tried giving the command line a try for the installation but that's still over my head. Is there a step by step process to install software from a USB device or a folder located in the file system?

---

### Post by ibcrusn on 2010-06-14
Any advice on the two questions above?

---

### Post by ibcrusn on 2010-06-14
Well I won't say the issue is 100% solved because I'm still going to work to make the Linksys card work but  I do have have good news though...the Trendnet TEW-441PC wireless card is plug and play. I inserted the card and started the computer and low and behold the card powered up and showed the available networks. Set the security and here I am. I would say the $15 was well worth it. I think now my experience will change for the better. I'll keep you posted with the progress on the WPC54Gv2 card. Thank you to those that put up with me.

---

