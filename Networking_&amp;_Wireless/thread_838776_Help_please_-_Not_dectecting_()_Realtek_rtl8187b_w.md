---
title: "Help please - Not dectecting (?) Realtek rtl8187b wireless"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by NewJo on 2008-06-23
Hi All.

First some basic facts. I am a newbie with Ubuntu/Linux (1wk). I am not afraid of command line but know next to nothing about linux command line...

My system is an Asus motherboard P5B wifi, Intel core2 6300@ 1.87Ghz, 2GB Ram,ATi radeon x550card, Realtek rtl8187B on board wireless chip. Dual boot winxp with Ubuntu 8.03LTS

The problem. 
Basically I don't think Hardy is detecting the wireless chip. 'sudo lshw -C network' just gives me the two wired Ethernet ports (unused - this machine only has wireless connection only). The same with the command iwconfig. I only get eth0 and eth1 - no wireless connection.

When I installed the ndiswrapper for the card through GUI (windows wireless driver)it says hardware installed, but the GUI (network) shows no wireless interface. See attached screen grab.

I think I need a way to make to force Ubuntu to detect the card/chip or a way to figure why it is not detecting it (if in fact that is the problem)... Remember I am a Newbie with linux, so English please.

BTW not sure if this has anything to do with it, but I can't find the network manager icon on my system. When I reboot I always get a whole lot of lines about network manager that flashes past me. Don't have time to really read to understand what is going on.

Thanks in advance for any help you can provide.

P.S When I boot to winxp the same realtek chip works perfectly.

---

### Post by chili555 on 2008-06-24
> When I reboot I always get a whole lot of lines about network manager that flashes past me. Don't have time to really read to understand what is going on.Linux has thoughtfully saved those messages for us! You can see them in a terminal with:```
dmesg | less
```The 'less' command will allow you to scroll back and forth in the text with the arrow keys to look for suspicious entries. Please do *not* flood the forum with your entire dmesg. You might also get a closer look with:```
dmesg | grep -i network
```

---

### Post by issih on 2008-06-24
Network Manager doesn't appear in the menu's as such. The program is nmapplet, and its automatically loaded at boot time, and lives in the notification area over in the top right. That little networking icon will give you access to most networking features.

From the main menu you can get to the manual network configuration under administration, but that is also reachable from the applet.

In a terminal what do you get if you do:

"ifconfig -a"

and also "lspci" and "lsusb", if lshw really isn't showing anything useful.

One other thing you might do is:

```
sudo lshw | grep 8187
```

---

### Post by NewJo on 2008-06-24
Thank you for taking an interest chili555.

I ran 'dmesg |less'. Unfortunately it did not give me the lines I see regarding network manager when I shut down the system. But it show me that the ndiswrapper was not intializing the card see below.

 [COLOR="DimGray"] 40.293752] usb 1-3: reset high speed USB device using ehci_hcd and address 2 
[   40.445182] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,07/18/2007,5.1097.0718.2007) loaded 
[   40.447027] ndiswrapper (mp_init:216): couldn't initialize device: C0010006 
[   40.447033] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001) 
[   40.447043] ndiswrapper (mp_halt:259): device dfae9480 is not initialized - not halting 
[   40.447046] ndiswrapper: device eth%d removed 
[   40.447062] ndiswrapper: probe of 1-3:1.0 failed with error -22 
[   40.448474] usbcore: registered new interface driver ndiswrapper[/COLOR] 

[COLOR="Black"]So I removed the ndiswrapper and the lines above disappeared after reboot. But unfortunately I still can't see the wireless card - either with the GUI (System>Administration>Network) or with the lshw command.:(

Anymore ideas... let me know.

P.S. For the sake of brevity I have not mentioned everything that has happened. One thing that might give a clue is that the wireless actualy worked on one install but then 'disappeared' on another installation. Happy to explain in detail if you want.Let me know.  [/COLOR]

P.S.S. 'dmesg | grep -i network' showed nothing. Just when straigt to command prompt.

---

### Post by NewJo on 2008-06-24
Thankyou for your insterest too issih.

sudo lshw | grep 8187 - gave nothing. Straight back to the prompt.

But 'lsusb' gave me the following;

jo@Asus-Comp:~$ sudo lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 045e:009d Microsoft Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 04a9:1712 Canon, Inc. 
Bus 004 Device 001: ID 0000:0000  
**Bus 003 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.** 
Bus 003 Device 001: ID 0000:0000  

You can see the realtek card showing up.But what does it mean? Any suggestion as to what I can do from here...?

---

### Post by issih on 2008-06-24
Hmmn, this wiki claims to be about your card:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b?highlight=(WifiDocs)|(AND)|(ManufacturerModel](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b?highlight=(WifiDocs)|(AND)|(ManufacturerModel))

But it says that the kernel misidentifies the card as an 8197, which yours isn't doing. Its entirely possible this is just because the kernel has been fixed and is now identifying correctly. There is at least one other person having the same issues:

[http://ubuntuforums.org/showthread.php?t=695327](http://ubuntuforums.org/showthread.php?t=695327)

so it might be worth a pm to them to see if they got anywhere.

your only hope for using ndiswrapper is to try using a few different drivers, but which to use is going to be fun:

have a look on:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by AisDeck on 2008-07-01
I am also having the same problem with Ubuntu 8.04 Hardy 64bit
I am dual booting with Vista and on Vista the card works fine.

My network manager is working properly, but Ubuntu just doesn't seem to find the wireless card.

Also, like NewJo, I am also a newbie in Ubuntu/Linux, so I really don't know what to do. I did the steps in this thread but all I got were the same results as NewJo.

If anyone has a solution for this, I would be very glad to hear it. :confused:

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by sputnikkk on 2008-07-20
As with most all of the so called SOLUTIONS ive come across whilst struggling with this problem, there always seems to be some kind of caveat...

> This is a guide to help you get the Realtek RTL8187b Wi-Fi card operational.

Before you begin, you should be aware of the limitations of using this method.

    * WPA/WPA2 are not supported. only non-encrypted and WEP encrypted networks function.

They all seem to either work ...

Only in DHCP
Not with RaLink Drivers
Not with WAP/WAP2
Not with Static IP's
Not with the Network Manager GUI
or ... by installing WINDOWS drivers - LMFAO.

SOLVED!  it worked once in a blue moon on grandma's other machine before she thru it out the window on the 2nd tuesday of every other month when Pluto aligned with Uranus.

Arrrghhh ...

---

### Post by onewithnature83 on 2008-07-20
> 
Only in DHCP
Not with RaLink Drivers
Not with WAP/WAP2
Not with Static IP's
Not with the Network Manager GUI
or ... by installing WINDOWS drivers - LMFAO.


Only in DHCP / Not with static IP's are the same logic and static IP's work fine.

Yes its true WAP/WAP2 is not an option..but most of could live with WEP fine. 

Network Manager works fine.

Not sure about RaLink Drivers.

I didn't say it was the Holy grail of a fix. But for those who don't want anything from windows ever again (me), I would simply prefer native linux drivers, with the limitations we speak of.

--TJ 

blue pill or red pill?

---

### Post by NewJo on 2008-07-22
Thanks Guys. I had tried this solution before - [https://help.ubuntu.com/community/Wi...ealtekRTL8187b](https://help.ubuntu.com/community/Wi...ealtekRTL8187b) - and it did not work for me. 

So I have given up with this wireless card. I am going to buy a new (hopefully supported) wireless card and install it. A this point this is the most cost effective solution (time wise anyway) for me.

Again thanks to all who responded.

---

### Post by dodge78 on 2008-08-01
Hi NewJo,

> **NewJo said:**
> Thanks Guys. I had tried this solution before - [https://help.ubuntu.com/community/Wi...ealtekRTL8187b](https://help.ubuntu.com/community/Wi...ealtekRTL8187b) - and it did not work for me. 

So I have given up with this wireless card. I am going to buy a new (hopefully supported) wireless card and install it. A this point this is the most cost effective solution (time wise anyway) for me.

Again thanks to all who responded.

did you use the 2007 or the 2008  modified tar?  Because i had the same problem with my wifi, and i tried the 2008 modified tar and it didn't work. So i rm the tar and all dir and files that were created. Then downloaded the 2007 modified tar and started from the beginning again. After that every thing worked and i was able to connect to my wifi network.

---

