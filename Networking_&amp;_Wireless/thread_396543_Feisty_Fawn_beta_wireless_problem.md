---
title: "Feisty Fawn beta wireless problem"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by bcollignon on 2007-03-29
I have a Realtek RTL8180 wireless card which worked flawlessly under Edgy, but isn't even in the list under Feisty beta.  I have no wireless networking as a result and my Ubuntu computer isn't connected via CAT5.  What am I doing wrong or what is the os doing wrong?

---

### Post by bobswat on 2007-03-29
I have a Linksys WUSB54Gv2 and I'm having the exact same problem.

I did:

```

sudo ndiswrapper -i /linksys/drivers/wusb54gv2.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```

I did ndiswrapper -l and it says:

wusb54gv2 **Driver present, Hardware present**


Then I looked in my network and the wireless card doesn't even show up
I'm not sure what I did wrong.  Any help would be appreciated, thank you.

---

### Post by mpmc on 2007-03-29
I'm having the same problem aswell..

---

### Post by chili555 on 2007-03-29
Feisty installs NetworkManager by default. NM controls all network devices. Click on the little icon and select an access point to connect to, fill in a blank or two and it should connect.

---

### Post by bobswat on 2007-03-30
So there's no need to use Networking thing?  Because wlan0 isn't even showing up..

---

### Post by wushuFreak on 2007-03-30
I installed the beta on my inspiron 1501 and followed paperDiesel's tut on installing the driver and had total success. Network Manager worked great and I had no problem connecting at all. Everything was beautiful at first, but on the 3rd or 4th boot, wlan0 disappeared alltogether. My card was not even detected. During the very next boot, Feisty hung on configuring network settings(?) and froze.

I was hoping maybe a fluke, but I did 3 more fresh installs with exactly the same results.

---

### Post by chili555 on 2007-03-30
wushu-
On your next fresh install, you might uninstall NetworkManager and configure your wireless the old way. Worked perfectly for me.

Synaptic said some scary stuff was going to be removed; I ignored it and everything works well for me now.

---

### Post by bcollignon on 2007-03-30
> **chili555 said:**
> Feisty installs NetworkManager by default. NM controls all network devices. Click on the little icon and select an access point to connect to, fill in a blank or two and it should connect.

Where is NetworkManager located in the scheme of things?  My problem is that my wireless device isn't even recognized anywhere, but shows up in the hardware profile.  I can't activate it anywhere that I'm aware of, although I'm sure there's a CLI command I can type or something.  Anyway, any help would be apprecieated.

---

### Post by alicemoon on 2007-03-30
I have loaded feisty and have tried to connect with an edimax EW-7318UG  and with a belkin dongle both sticks can see  the network through network manager and try to connect but cannot get in. I have removed all encryption but still no luck!

---

### Post by bcollignon on 2007-03-30
But where is NetworkManager in the Ubuntu menus?  By the way, thanks for replying so quickly!

---

### Post by alicemoon on 2007-03-30
The Networking tool can be found by choosing from the menus System-->Administration-->Networking

---

### Post by thetruth on 2007-03-30
Hi
I have the Pci Am772 and it never worked before so i bought belking usb and  edgy recognised it but refused to connect to even though everything was ok. so i installed fresh Feisty and removed USb it refused to detect my pci Am772 so i installed Ndiswrapper successfully  and it founds the network  and correctly allow me to use WPA  to connect but no connection. same thing with USB belkin. Now i wasted my £20 for nothing and i am still without a wireless even if i disable Encryption

---

### Post by alicemoon on 2007-03-30
yes this is my experience - it recognises both my wireless usb's when I connect them but  it cannot connect through the network with or without security. I have looked through the forums and there seem to be lots of people struggling with this problem - I am assuming it is something to do with drivers but I know nothing - is there an expert out there who can shed some light for those of us who are basic users?

---

### Post by wushuFreak on 2007-03-31
> **chili555 said:**
> wushu-
On your next fresh install, you might uninstall NetworkManager and configure your wireless the old way. Worked perfectly for me.

Synaptic said some scary stuff was going to be removed; I ignored it and everything works well for me now.


I will certainly keep that in mind. I was just so excited when everything worked so well at first. I had quite a time getting wifi in edgy and was just pleased things clicked right away in feisty. However, I've gone back to edgy for now until the final release of feisty. Last few weeks of school and all....just don't have the time to invest. Will definitely do away with NM next time, though. I have read about numerous issues with it this release (possibly fixed in the final?).

---

### Post by IsaacJ on 2007-03-31
Don't know if this helps any one (I'm still a noob) but my adapter works in Edgy and Fawn without using ndiswrapper.  But it doesn't show up as Wlan at all.  It's rausb0.

I just went to terminal and typed


sudo dhclient rausb0


Soon as this cleared, I could surf the web and everything.  Right now, I can't get WPA going in Fawn yet--it doesn't even show up as an option.  WEP is the only security it offers me.  Also, after getting my updates, the Network Manager icon seems broken, but I don't think that's anything to do with the driver.  The manual command above still works, though.  Like I said, I didn't even need ndiswrapper after that to get online.

IsaacJ

---

### Post by keith.burgoyne on 2007-04-01
I have a Linksys wpc11 v. 4 PCMCIA wireless card -- which shows up in lspci as a Realtek  RTL8180L 802.11b wireless card -- and it doesn't work.  Wlan0 doesn't exist, and there is no option in network manager to configure, or even manage, my wireless adapter.

I tried updating, and I tried a fresh install. The problem persists.

Any ideas, anyone?

--Keith

---

### Post by wushuFreak on 2007-04-01
> **keith.burgoyne said:**
> I have a Linksys wpc11 v. 4 PCMCIA wireless card -- which shows up in lspci as a Realtek  RTL8180L 802.11b wireless card -- and it doesn't work.  Wlan0 doesn't exist, and there is no option in network manager to configure, or even manage, my wireless adapter.

I tried updating, and I tried a fresh install. The problem persists.

Any ideas, anyone?

--Keith

Have you tried installing the windows driver using ndiswrapper ?

---

### Post by keith.burgoyne on 2007-04-01
Yes, I just did.  That appears to have solved it!

Too bad it didn't work out of the box.

---

### Post by ts2000 on 2007-04-01
Feisty doesn't have drivers for Beliin F5D6001 whereas previous versions did.  What a back step because this is a popular card here in Australia.   Now I have to reinstalled Dapper.  I'm not doing the ndiswrapper thing because there are 2 versions of F5D6001 from belkin and it's a dog to get things working.  Thanks god for windows backup OS.

---

### Post by keith.burgoyne on 2007-04-01
There really isn't any reason to revert back to dapper (unless of course, that is your personal preference). Ndiswrapper does work quite well. A good rule of thumb is to use whatever Windows driver you normally would, so if there are multiple "kinds" of drivers available you won't find yourself guessing. 

I know what you mean though, not having support for wireless right out of the box is a shame, but with a couple of steps, your wireless will run just fine!

Also, I am quite impressed with the wireless support through ndiswrapper -- previous versions had no noise/signal strength measurements. At least for me.

---

### Post by wushuFreak on 2007-04-01
I had to revert to Dapper due to the problems I stated earlier. I am hopeful the issues will be corrected in the final release. 

It *is *a shame that wireless does not work out of the box. I am certain it will in Ubuntu in due time. This OS has come a long way and I think (my non-professional opinion) wifi has not necessarily been a great priority in the past but seems to be becomming more important recently.

Thank the stars for ndiswrapper!

---

### Post by bcollignon on 2007-04-01
> **alicemoon said:**
> The Networking tool can be found by choosing from the menus System-->Administration-->Networking

Ah, yes.  I have listed a WIRED CONNECTION and MODEM, neither of which is in use on my particular computer.  In Edgy, my WIRELESS connection was listed and, as I remember, all I had to do was to click a checkbox to activate it.  It worked flawlessly from that point forward.  For some reason (lack of drivers perhaps) Feisty doesn't acknowledge the wireless card's existence in Network Manager.  As I've stated, it's listed as a hardware device, but nowhere else.  I'm sure a command-line or two would help, but I'm not a command-line savvy person -- at least where Linux is concerned.  Any help would be appreciated from the ranks of gurus.

---

### Post by sabi on 2007-04-01
Some things to keep in mind.

1. Feisty is beta software, it is under going daily changes. If you are looking for stability, Edgy might be a better choice.
2. Most wireless cards can be used with Feisty, using either linux drivers or vendor drivers. There are some cards that simply will not work with Feisty or any distribution of linux.
3. A step-by-step approach to problem solving will provide others with information to help you.

With that said, the first step is to determine the status of your wireless card.
In Feisty, from the menu bar in the upper left select 

Applications>Accessories>Terminal

In the terminal window, at the prompt type

```
sudo lshw
```

This command will produce a detailed listing of all the hardware in your system. You need to find the section

 *-network
          description: Wireless interface

This will tell us if your wireless card is recognized, what driver is in use and the vendor. If you have a PC card (PCMCIA) use this command

```
sudo lspci
```

If you have a USB adapter then use this command

```
sudo lsusb
```

This is the first step that will lead us either to a working wireless card or a conclusion that the card will not operate under linux.

Post your results and we will continue .....

Sabi

---

### Post by wushuFreak on 2007-04-01
> **bcollignon said:**
> Ah, yes.  I have listed a WIRED CONNECTION and MODEM, neither of which is in use on my particular computer.  In Edgy, my WIRELESS connection was listed and, as I remember, all I had to do was to click a checkbox to activate it.  It worked flawlessly from that point forward.  For some reason (lack of drivers perhaps) Feisty doesn't acknowledge the wireless card's existence in Network Manager.  As I've stated, it's listed as a hardware device, but nowhere else.  I'm sure a command-line or two would help, but I'm not a command-line savvy person -- at least where Linux is concerned.  Any help would be appreciated from the ranks of gurus.

I've read a few posts in which individuals used ndiswrapper (a simple search of the forum will turn up numerous howtos on installing this) with your driver which can be found here:
[http://download.opendrivers.com/drv/...-8180(330).zip]("http://download.opendrivers.com/drv/...-8180(330).zip")

I used paperDiesel's tutorial for an inspiron 1501 and it works great. The ndiswrapper install should work well for you, just sub your driver. These howtos are very step by step and easy to follow. You don't have to be command-line-savvy.

I also read [here]("http://ubuntuforums.org/showthread.php?t=368642&highlight=RTL8180") that people had success with ndisgtk after uninstalling network manager.

If you are going to use Linux, you will be most successful getting used to the command line. Its really not that bad and you don't have to be a guru. You can find a cheap book on bash that will help quite a lot and give you much more control over your system. The learning curve is very short.

---

### Post by sabi on 2007-04-01
> **wushuFreak said:**
> I installed the beta on my inspiron 1501 and followed paperDiesel's tut on installing the driver and had total success. Network Manager worked great and I had no problem connecting at all. Everything was beautiful at first, but on the 3rd or 4th boot, wlan0 disappeared alltogether. My card was not even detected. During the very next boot, Feisty hung on configuring network settings(?) and froze.

I was hoping maybe a fluke, but I did 3 more fresh installs with exactly the same results.
wushuFreak,

This behavior (e.g. freeze, slow performance) is generally caused by conflicting builtin kernel drivers. In general you can solve these types of problems by blacklisting the offending driver (module). Determine what drivers are loaded by utilizing my earlier post.

In general you should never have to reinstall the operating system to solve a driver problem.

Hope this helps....

Sabi

---

### Post by thetruth on 2007-04-01
My system froze when using Wireless when using Ndiswraper driver. how do you black  the offending driver??

Thanks

---

### Post by sabi on 2007-04-01
> **thetruth said:**
> My system froze when using Wireless when using Ndiswraper driver. how do you black  the offending driver??

Thanks

Blacklisting a driver is utilized for built in kernel drivers.

If you are using ndiswrapper to install a driver you can remove the driver by using:

```
sudo ndiswrapper -r <driver name> 
```

The driver name has to be correctly specified (e.g.):

```
sudo ndiswrapper -r netrtusb
```

If you want to examine what ndiswrapper drivers you have installed, use:

```
sudo ndiswrapper -l
```

Does this make sense?

Sabi

---

### Post by sabi on 2007-04-01
There are questions about which cards are supported with native linux drivers. The following quote from the Ubuntu wiki attempts to answer the question.

> If you are going wireless card shopping, please look at this searchable list of cards which are supported under Linux at [WWW] [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/) . Make sure you buy wireless cards supported fully under Linux. It is worth noting that the [WWW] Free Software Foundation (FSF) recommends the Ralink 2500/RT2400 and Realtek RTL8180 chipsets. A recent (December 20, 2006) [WWW] article also mentions Ralink and Realtek as open-source friendly Wifi vendors, as well as Atmel.

Remember this quote is discussing Ubuntu releases through Edgy, **not** Feisty!

As an example, yesterday, a user had to blacklist the built in kernel driver for Realtek:

```
# use ndiswrapper instead for rt2x00 devices: rt2570 panics kernel
blacklist rt2570
```

One day the built in driver worked as expected, the user performed a daily update through Update Manager and suddenly the driver caused his system to freeze on boot. He then used blacklist to be able to boot his system without the benefits of the driver.

Remember the developers are working very hard to meet the release schedule for Feisty and this type of behavior is expected for beta releases. The final release will be much more stable.

The goal is the release version will have new features and drivers and will allow more wireless cards to simply work without adjustments ("work out of the box").

Enjoy,

Sabi

---

### Post by bcollignon on 2007-04-02
> **sabi said:**
> Some things to keep in mind.

1. Feisty is beta software, it is under going daily changes. If you are looking for stability, Edgy might be a better choice.
2. Most wireless cards can be used with Feisty, using either linux drivers or vendor drivers. There are some cards that simply will not work with Feisty or any distribution of linux.
3. A step-by-step approach to problem solving will provide others with information to help you.

With that said, the first step is to determine the status of your wireless card.
In Feisty, from the menu bar in the upper left select 

Applications>Accessories>Terminal

In the terminal window, at the prompt type

```
sudo lshw
```

This command will produce a detailed listing of all the hardware in your system. You need to find the section

 *-network
          description: Wireless interface

This will tell us if your wireless card is recognized, what driver is in use and the vendor. If you have a PC card (PCMCIA) use this command

```
sudo lspci
```

If you have a USB adapter then use this command

```
sudo lsusb
```

This is the first step that will lead us either to a working wireless card or a conclusion that the card will not operate under linux.

Post your results and we will continue .....

Sabi


This is a beginning... thanks.  I'll post what I find.

---

### Post by ScooterDMan on 2007-04-06
I am having similar problems with my Linksys WPC 11 card with Feisty Fawn. I installed the correct drivers (Realtek 8180) via ndiswrapper; the card is recognized in my Network Settings (It even detects my wireless network, and reports signal strength), but it will not go on the Internet.

Here is the report I got from typing in the suggested commands in Terminal from Page 2 of this thread:

> 
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:06:25:17:e5:5d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2 ip=192.168.1.103 link=yes multicast=yes wireless=IEEE 802.11b
scooterdman@SonyUbuntu:~$ sudo lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 14)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)


If there is no easy solution to this, can someone tell me a wireless card I can go buy at Best Buy tomorrow that will be plug n play with Feisty Fawn?

---

### Post by TEDNUGNT on 2007-04-12
heres what i got using the commands:

sudo lshw

*-network UNCLAIMED
          description: Ethernet controller
          product: RTL8180L 802.11b MAC
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 1
          bus info: pci@07:00.0
          version: 20
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=64 mingnt=32
          resources: iomemory:3c000000-3c0001ff irq:10

and ...

sudo lspci

07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

what do i do now? please help?

---

### Post by chili555 on 2007-04-12
ScooterDMan-> I installed the correct drivers (Realtek 8180) via ndiswrapperYet lshw -C network reports: ```
driver=orinoco driverversion=0.15 firmware=Intersil 1.4.2
```This is certainly a conflict. Is this a version 2.5 or version 3 card? It may say on the card itself.

---

### Post by devkelso on 2007-04-16
Or if you want a proper solution instead of running off to ndiswrapper, trying doing this:
```
sudo modprobe r818x
```It looks like there are some hangs for ralink chipsets but so far network manager works for my WPC11 version 4 (realtek 8180 based)  card.

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):
[URL="http://www.len.ro/work/tools/old-new-i8000-2"]
http://www.len.ro/work/tools/old-new-i8000-2[/URL]

---

