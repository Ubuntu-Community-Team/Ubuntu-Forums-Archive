---
title: "getting linux to let me connect wirelessly?"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by brianheard on 2009-02-18
Just downloaded Ubuntu from Wubi and was trying to go online. When I click on the wireless network icon at top of screen it tells me Im disconnected. So I was reading here alittle and went and downloaded Wicd. When I rebooted back into linux I did as I was instructed, I think, but I got an error message,"ERROR:CONFLICT WITH THE INSTALLLED PACKAGE NETWORK MANAGER". So before I go and cause real damage is there something I should be doing to make linux run that program? I also downloaded Compat so I have that file also and dont have a clue as to what I should do with it.

---

### Post by mikewhatever on 2009-02-19
I strongly suspect that the problem is not in the network managing program, so that installing wicd or another probably wouldn't help. You should post some info about your hardware, for example the output of the following command from Terminal: **sudo lshw -C network**.

As for the error, when wicd is installed, it removes the default network manager, since only one such program is allowed.

---

### Post by brianheard on 2009-02-19
Ok, thanks for the not windows page, that was very interesting and kinda gives me a clue as what to expect on this Quest for  Linux Understanding and Application. 
Now heres the info you requested about my network stuff. I see that it says my wireless interface is disabled but the light on my laptop that has the symbol for wifi is lit up. So how can I go and inable it in Linux?

*-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:f8:a6:e9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:6c:b5:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 66:5a:7f:ca:f9:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by abn91c on 2009-02-19
try this drivers

---

### Post by sailthesea on 2009-02-19
I just got to the bottom of a similar problem myself, though my solution will not work for you.
 I found it through good advice and some good luck. As you say you are about to embark on a quest. Someone, somewhere has had the same problem as you and solved it and they will tell you what to do, you just have to find that person! 
 The forums are a great source of help but you need to look in the right places and follow up any links the admin moderators give you. Be patient, you will get there!
 Good Luck Friend

---

### Post by brianheard on 2009-02-19
Thanks for the encouragement friend! Ok I saved the driver and I will have to leave from here for a minute because I gotta boot into Linux and I dont have internet there, but I guess you already know that or we wouldnt be having this conversation.:p
When I get to Linux with the new driver what do I do with it? Do I just double click on it or something?

---

### Post by abn91c on 2009-02-19
> **brianheard said:**
> Thanks for the encouragement friend! Ok I saved the driver and I will have to leave from here for a minute because I gotta boot into Linux and I dont have internet there, but I guess you already know that or we wouldnt be having this conversation.:p
When I get to Linux with the new driver what do I do with it? Do I just double click on it or something?
It's a deb file so yes click on it and install, not sure if it works with WICD, I would remove it first, I only know it works with knetworkmanager. I have the same BCM card on my laptop

---

### Post by brianheard on 2009-02-19
Well it did something but Im not sure what. It didnt seem to help me connect in Linux but then when I came back to windows it had somehow affected my wireless on Windows. It was no big deal, all I had to do was hit repair and it reconnected.
So I still dont have internet in Linux. Should I go to the site of the manufacturer of my wireless card and download a driver then go back to Linux and try the same thing? If its not a deb file then will it still work like the driver you gave me? Is there a certain place where I should put the drivers or do I just let the manager do the work?

---

### Post by brianheard on 2009-02-19
Do you think maybe I should disable my wireless card in windows and then try it in Linux? Could there be a conflict there?

---

### Post by sailthesea on 2009-02-19
That looks like it might be what you need so try it on for size. If you fail,ask for help and try again. Most likely you'll need to do some really weird stuff in Terminal while someone looks over your shoulder. It doesn't feel right but you're actually going to tell your machine to do what you want it to instead of accepting what it thinks you want AKA Windows mindset. Ubuntu is is a way of doing things. Look around and learn
 I got frustrated with this sort of thing before but others will learn from your experience and you will learn from them.
 Which is the point
You will find the way

---

### Post by brianheard on 2009-02-20
Nope it didnt work disabling it in Windows. Is there something like Devise Manager in Linux where I can go and see all the devices on the computer and what there status is? 
I did go to hardware test and my wireless card was listed along with my ethernet card, so it does see it, it just wont turn it on. Is there a way I can configure it manually? I right click on the network icon at the top of the screen and it says that the network is enabled and then i go in and try to set it up manually but that hasnt worked either.

---

### Post by Nixie Pixel on 2009-02-20
Have you tried booting from a Live CD and see if wireless works there?

Sorry, I am not familiar with using Wubi, so I couldn't tell you if there may be a conflict - using an Ubuntu Live CD can tell you if your wireless card will be supported without further drivers or any potential conflict with Windows.

---

### Post by brianheard on 2009-02-20
where do i put new drivers when i download them or what program do i use to install them? do i need to do it from the terminal window? is there something like device manager in ubuntu?

---

### Post by brianheard on 2009-02-20
Hey, no i didn't try booting from a CD. why would that be any different from what I'm doing already. i have Linux installed already from wubi. when i boot into Linux everything is there, i just dint know how to get Linux to see my wireless card i guess cause it wont see my router. i downloaded some drivers for my card and they are suppose to be for Linux but all they do when i open them is show me some files, i have no idea where to put the files to make them work. sorry I'm really new to this. maybe i should just uninstall ubuntu and then start again from scratch with a CD like you said, if i do that do you think you can help?

---

### Post by sailthesea on 2009-02-20
If you have the drivers on cd you should be able to install them using NDSWrapper Open the help and goto Using windows wireless drivers and follow the commands First thing to try anyway If this doesn't work there are other ways This is a common problem
 Diff'rent strokes for diff'rent folks

---

### Post by sailthesea on 2009-02-20
By the way

 I wouldn't bother using the live cd to test your wireless connection it simply doesn't work A Wubi install should find everything but you need to configure manually to get the best connection I know it can get very frustrating booting in and out of platforms and trying different paths , but you have to I was close to giving up but someone came to my rescue in the end!
 Let me know how you go!

---

### Post by brianheard on 2009-02-20
ok lets try something else first. I downloaded ndiswrapper 1.54. Now that I have that file I go to Linux and do what with it?

---

### Post by sailthesea on 2009-02-21
I'm not sure because in the end I got things going from terminal. Try starting a new thread in Wireless and Networking because you've gone cold here. I think I put the fix I used earlier in this thread so look back  Its way past bed time in my part of the world so am afraid I have to leave you. Will be here for a few more minutes

---

