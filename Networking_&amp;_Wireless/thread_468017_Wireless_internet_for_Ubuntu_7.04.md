---
title: "Wireless internet for Ubuntu 7.04"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by Bartikky on 2007-06-08
Hey, I successfully installed Ubuntu 7.04 but now I need to somehow get it to use my wireless router, the router's name is BTVOYAGER2091-6B and it's a DSL connection. Before, my internet was working perfectly fine on Ubuntu but lost connection now and again, but I didn't find out till today that Ubuntu was using my neighbour's wirless which hadn't been secured. I need help to get Ubuntu to use my wireless connection, BTVOYAGER2091-6B, how do I go about this? Also I'd like to add that my wireless connection is password protected.

Some guidance wil be much appreciated!
Thanks, Bartikky :p

---

### Post by coffeecat on 2007-06-08
You need to find the Network Manager applet icon near the right end of the upper panel. Hover your mouse icon over it and it should show the ESSID of the wireless network it's connected to. Click on the icon and it will show you a list of the networks it can detect. Click on the ESSID of your network and it will prompt you for the encryption type and passphrase for your wireless router.

If you haven't already gone through this stage it will next prompt you to set up a keyring password. One irritation of Network Manager is that it prompts you for the keyring password every time you boot up before it will connect you to your network.

I'm assuming that your network card is supported in Ubuntu because you are connecting to your neighbour's network OK, so you should be able to connect to your own.

Make sure you haven't disabled broadcast of your ESSID - Network Manager can't cope with hidden ESSIDs (yet).

---

### Post by jabzwnein on 2007-06-08
I love Ubuntu but this wireless stuff is ridiculous.  I just wish I had an .iso of Edgy to reinstall that; this is my third time doing a clean install of Feisty.  My computer recognizes the network, and sometimes will even say it's connected at around 80%, but I can't get online and nothing has worked.

---

### Post by coffeecat on 2007-06-08
And the relevance of this to the OP's question?

I'm posting from Feisty on my laptop at the moment connected wirelessly via Network Manager to my Linksys wireless router. It works flawlessly every time. Seemingly, your mileage is varying.

---

### Post by Bartikky on 2007-06-08
When I hover my mouse over the applet icon, it says 'No Network Connection', it said this aswell when I was using my neighbours wireless router. I clicked the icon, there was an option greyed out at the top, the only option I have is to click 'Manual Settings', I'm assuming this is the Network Manager you are talking about (circled in blue on the image attached).

When I clicked properties, I added the name of the network by type because it didn't seem to always pick it up itself, I'm not quite sure if the Connection settings are correct.

---

### Post by Drifter on 2007-06-08
I have just tried to get online with wireless motorola card, but was not able to what do we need to do to get online with wireless card on a desktop.

---

### Post by coffeecat on 2007-06-09
> **Bartikky said:**
> When I hover my mouse over the applet icon, it says 'No Network Connection', it said this aswell when I was using my neighbours wireless router. I clicked the icon, there was an option greyed out at the top, the only option I have is to click 'Manual Settings', I'm assuming this is the Network Manager you are talking about (circled in blue on the image attached).

When I clicked properties, I added the name of the network by type because it didn't seem to always pick it up itself, I'm not quite sure if the Connection settings are correct.

I'm rather mystified as to why Network Manager was saying 'No Network Connection' when you were connected to your neighbour's router. I thought that it would only say that if it could not detect any networks, either because there are no detectable signals in range, or because the wireless chipset is not supported. But since you were connected to the neighbour's router, both of those must be true. Curious.

OK, let's get a few fundamentals out of the way. First, right-click on that applet icon, then 'About' and check that is Network Manager and not 'Network Monitor'. The icon looks the same in both. Second, when you are connected to the neighbour's network, does the icon change to a blue bar-chart type icon or remain as two little monitors? If it stays the same NM is not doing anything. A word of explanatioin. That screenshot is of the Network Settings app, normally accessed through System > Administration > Network. Seemingly, you've managed to get there through 'Manual Configuration' from the NM applet. They are different apps. In mine Network Settings shows 'Roaming Mode Enabled' under Wireless Connection, and my NM applet is showing five detectable wireless networks at the moment.

Try disabling the Wireless Connection under Network Settings (which I believe over-rides NM) and see if NM then shows you all your detectable networks from the panel applet. Then you should be able to configure your network in NM as I described in my first post.

Lastly, open a terminal and type:

```
sudo lspci
```(that's a lower-case L) and look for the line with 'wireless' and/or '802.11' in it. That will give you the chipset of the wireless device you are using. It will be useful information if we can't get NM working because, although wireless is much better in Linux than it was, a few chipsets are a pain, mainly because of the unco-operativeness of the manufacturers.

---

### Post by Bartikky on 2007-06-09
OK, I'm not quite sure how to disable the wireless connection, I've unticked the box next to the wireless connection icon, is that right what I've done? Anyways, when I type in 'sudo lspci' in the terminal it asked me for a password, I'm assuming that the password is the same for my ubuntu account log in, but it just won't let me type any character in,  only thing that seems to work is enter, then it says words to the effect of incorrect password.

Oh yeah, when I untick the box next to the wireless icon, nothing changes in the applet, and I'm sure from what I can remember that the icon still had 2 computers even when I was connected to my neighbours wireless, it doesn't seem to connect to my neighbours wireless anymore, or find it now, but my Dad thinks they could have turned it off. XP on my computer seems to find it and never lose sight of it though. Also in administration menu under system, there is Network and Network Tools. I have checked that the icon in the top right corner says NetworkManager Applet 6.(something).

---

### Post by coffeecat on 2007-06-09
> **Bartikky said:**
> Anyways, when I type in 'sudo lspci' in the terminal it asked me for a password, I'm assuming that the password is the same for my ubuntu account log in, but it just won't let me type any character in,  only thing that seems to work is enter, then it says words to the effect of incorrect password.

Yes, type in your ordinary password. The first created user can get temporary administrative privileges with 'sudo'. For more info, see [this link]("https://help.ubuntu.com/community/RootSudo"). When you type in your password you get no feedback at all, no stars or anything. It's a bit unnerving if you're not used to it, but it is accepting the password. Post the output of the appropriate line from 'sudo lspci' and then we can go from there. In the meantime I'll have a think about everything else you've posted and I'll see if I can add anything. Perhaps someone else might have something constructive to add rather than vague moans about wireless in Linux. :wink:

---

### Post by Bartikky on 2007-06-09
I'm sorry but, I don't know if I'm just too impatient or just can't see well but I can't the things you asked me to look for, I'll just post the outcome of 'sudo lspci'...

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
02:02.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thanks for helping me by the way, I almost requested for this thread to be deleted, thanks for your patience so far.

---

### Post by coffeecat on 2007-06-09
> **Bartikky said:**
> I can't the things you asked me to look for, I'll just post the outcome of 'sudo lspci'...

Neither can I, which stumped me for a few minutes until the penny dropped. You're using a usb wireless dongle, aren't you? :lol: I should not have assumed you would be using a PCI card or inbuilt wireless card. I should have asked first. For some reason I assumed you were using a laptop. A completely unreasonable assumption. Sorry about that. :)

OK. Let's try again. Instead of lspci, make sure the usb wireless device is connected, open a terminal again and do:

```
sudo lsusb
```and look for the output I suggested before.

A word of explanation. As you may have gathered, support for wireless can be spotty in Linux. It largely depends on how much the manufacturers have co-operated. Some do; many don't. Many of the drivers have to be reverse-engineered. Another problem is that saying that you have - for example - a D-Link model number so-and-so doesn't really help because manufacturers have a habit of using different chipsets at different times or on different continents in the same model number. The commands lspci (for pci cards) or lsusb (for usb devices) will reveal the chipset type. If we can determine that information for your setup we can then see if your chipset is problematic or quite straightforward. Without knowing what your chipset is I'm puzzled why you managed to connect to your neighbour's network almost without trying yet Network Manager doesn't seem to be playing ball with you.

By the way. Happy to help. I just hope we get somewhere for you. :wink:

---

### Post by Bartikky on 2007-06-09
Haha sorry I should've said aswell, yeah it is usb, i'll be back in a few minutes to post the outcome...

---

### Post by Bartikky on 2007-06-09
Well this looks more promising, I'm sure this is the thing we've been looking for...

Bus 003 Device 002: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter

This is supported by Linux Ubuntu... well from the research I've done I'm sure it is. Feels like we're getting somewhere now :D... (hopefully I didn't just jinx it)

---

### Post by coffeecat on 2007-06-09
That's the one. I've done a quick forum search and I came up with [this thread]("http://ubuntuforums.org/showthread.php?t=449456&highlight=Linksys+WUSB11+V2.6+802.11b"), among others.

To be honest, I have no experience of this adapter so I don't know how easy or otherwise it is to get it going, but I should think that thread is a good start. In fact it doesn't look too bad at all. Once you've installed the driver and ndiswrapper you should be OK to configure the network in Network Settings. It seems that Network Manager won't be able to help you so you might as well forget everything I said about NM.

One thing I don't understand. According to that thread you need to download the driver before you can get the card working. Yet you seem to have connected to your neighbour's network without it. Am I understanding you correctly?

Anyway - best of luck. Sorry I can't help further but, as I said, I have no experience of that device but from my forum search it seems that plenty of people have. :)

---

### Post by Bartikky on 2007-06-09
Yeah this is right, well I got onto this online game, runescape, but i found a needed a java (linux version) to play it, so yeah it did connect to the neighbours wireless, it picked up 1 or 2 other wireless networks aswell, which none were mine but they were secured networks. I got to go now, bed time for me *yawns*... zzzZZZ

---

### Post by Bartikky on 2007-06-10
It looks to me like that thread only works if you have internet on ubuntu, it seems to be looking for a website when I use the command 'sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common'. It stays on 0% with a website something like 'gb.ubuntu.' I can't remember the rest.

Is there any other way that you know of to get ndiswrapper?

I found this link but it doesn't make sense to me really,
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/94685-wireless-lan-linux.html)

EDIT: OK, I found an alernate place to get hold of it using the internet on XP,

[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9) 

How do I know which 'Architecture' I have to choose?  amd64 or i386?

EDIT2: Do I need to install ndiswrapper-common aswell as ndiswrapper-utils-1.9?

---

### Post by coffeecat on 2007-06-10
> **Bartikky said:**
> It looks to me like that thread only works if you have internet on ubuntu, it seems to be looking for a website when I use the command 'sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common'. It stays on 0% with a website something like 'gb.ubuntu.' I can't remember the rest.

Yes, you have to have a working internet connection to use apt-get (or Synaptic).

> **Bartikky said:**
> How do I know which 'Architecture' I have to choose?

If you used the standard desktop install CD, choose i386 or x86 - can't remember which they call it. If you used the 64-bit install CD, use AMD64.

> **Bartikky said:**
> Do I need to install ndiswrapper-common aswell as ndiswrapper-utils-1.9?

Yes, it's a dependency. No, I didn't know that off the top of my head. I just did a check in Synaptic. :wink: (Synaptic, by the way, is the graphical package manager - a GUI front-end for apt-get.)

Before you get going, a thought. Can you connect your computer to the wireless router with an ethernet cable - even if you have to move the computer temporarily to do so? All routers have ethernet ports. Ubuntu should autodetect the ethernet connection as it boots up (if it doesn't just have a fiddle in Network Connections) and then you won't have to muck around with Windows. Everything will get installed for you this way.

---

### Post by Bartikky on 2007-06-10
Erm, unfortunately thats not really possible to move the computer, the router is upstairs and there no near enough modem port to plug the router into downstairs. Also where the router is there isn't enough plug sockets to plug the computer in and I just don't think its worth moving the whole computer.   We initially setup the wireless in the previous house and when we moved here there was no need to change any details or reinstall anything. I done everything in that thread, still no luck...   Is there nothing in Network Tools than can help me?

EDIT: I don't know if this helps, but this is the output I got from iwconfig

> brandon@brandon-ubuntu:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



---

### Post by Bartikky on 2007-06-10
Alright, is there any way I can reset all the settings on Ubuntu to the defualts? I think I need to start right from the beginning, only thing I can think of is a fresh reinstall...

---

### Post by coffeecat on 2007-06-11
Sorry I didn't get back to you before. It probably isn't necessary to re-install. I have one suggestion. You need to attract the attention of forum members who have experience of your Linksys usb dongle. I see from a forum search that there are several versions of this and nothing beats hands-on experience, but the people you need may not notice this thread.

Suggest you start a new thread. Put 'Linksys WUSB11 V2.6' in the title and describe what you've done so far. Hopefully, someone with experience of this will pick it up.

You're unlucky. Remember what I said about wireless chipsets and manufacturers? This is one where there is no native Linux support. (I still don't understand how you could connect to your neighbour's network :(. ) Ndiswrapper is a utility that 'wraps' the Windows driver so that it can do its stuff in a Linux environment. Network Manager (which I mentioned before) only works with proper Linux drivers.

You're probably getting a dim view of Linux's ability to work with hardware. Believe me, generally speaking, Linux works **better** with most hardware than Windows. Where it fails is generally down to manufacturer indifference.

I guess you probably can't afford £100, but [this]("http://www.devolo.co.uk/uk_EN/produkte/dLAN/mldlanhsstarterkit.html") is a better alternative to wireless. Yes better. Just plug in and go. You get faster transfer speeds and it's more reliable. I've seen them stocked in Maplins, PCWorld and Staples and they may be slightly cheaper on internet sites. And, yes, I use them myself for my desktop machines. I only use wireless on my laptop.

---

### Post by Bartikky on 2007-06-11
That wireless looks excellent, well I certainly can't afford that lol but my Dad might if he sees the advantages of it, especially that it has a Linux installation and configuratioin software, he plans to set-up all the computers to Linux Ubuntu, he's struggling with my sister's to get the wireless to work for her too. I still find it strange how I was already connecting to my neighbours wireless even when messing around with Ubuntu before installation.

Anyways that wireless looks fantastic, it'll be great for once I get my PS2 internet connected aswell. I'm sure I'll easily be able to persuade my Dad to buy it ;)

Thanks for your help and thread suggestion, I'm never good at naming threads lol, I've only really been introduced to these type of forums ever since I've been having trouble with Windows, this is why I've decided to make the leap to Ubuntu aswell. :D Anyways, thanks again!

---

