---
title: "If you are having wireless problem in Gutsy - what wireless chipset are you using?"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-10-28
Trying to compile a list of the most problematic wireless cards, more specifically wireless chipsets with gutsy.  If you are having problems, it would be great if you could post your chipset (instructions below), and a very brief summary of the problems you are having (please be as direct and to-the-point as possible).  Please also list the driver you are using (see below).  Thanks.  Your input will make future versions of Ubuntu that much greater.

To determine chipset, type at command line (or just cut and paste this code into the terminal):
```

lspci -nn | grep Network

```

This will list the driver (If you have multiple network drivers, like a wired and wireless, all networking drivers will be listed with the following command.  Please only submit the wireless driver) (Cut and paste into terminal)
```

lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

```

Your wireless chipset should be listed (If you have multiple network cards, wired, wireless, please list the wireless chipset)
If you select other - please let me know the chipset and driver.

---

### Post by gb5uqx on 2007-10-28
Random unpredictable disconnections surfing/downloading.

> 00:0f.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]


---

### Post by kevdog on 2007-10-28
For poll responders, again a brief summary of the problem, along with chipset and driver information would be extremely helpful.

---

### Post by joes_meat on 2007-10-29
Ralink RT2561/RT61

In a D-Link 530 rev E.

Serialmonkeys driver (standard): 
Drops out under load, wont reconnect without 'sudo /etc/init.d/networking restart'

RaLink driver from website:
-With manually edited /etc/network/interfaces file:
Will not connect at all.

Ndiswrapper with D-Link driver from their website:
Connected, stable, would not come back up after reboot.

Status: Rooted.

---

### Post by lecanardzero on 2007-10-29
I have a  RaLink RT2600 802.11 MIMO and i'm using the rt61pci driver.  I dont know what happens or causes it, but my networking will die.  I can't restart it through networking and I have to restart the machine to get it back up again.  It used to cause my machine to lock up, so it's an improvement still!

---

### Post by kevdog on 2007-10-29
Just an FYI for all you ra chipset users -- ra native drivers (serialmonkey of rtxxpci modules) -- there is a known conflict when working with these drivers and networkmanager.  I would recommend other methods if a GUI is wanted such as either rutilt or wicd.  I dont believe ra chipsets and ndiswrapper have the same conflict.

---

### Post by Tomosaur on 2007-10-29
I use rt2500usb - Ubuntu can see the network and apparantly connects, but it says strength is at 0%, and the internet doesn't work at all.

I tried using ndiswrapper and the Windows drivers, and replaced network-manager with wicd, but the same issue occurs - although the pre-connection signal strength is much better.

---

### Post by Ferrat on 2007-10-29
> **kevdog said:**
> Just an FYI for all you ra chipset users -- ra native drivers (serialmonkey of rtxxpci modules) -- there is a known conflict when working with these drivers and networkmanager.  I would recommend other methods if a GUI is wanted such as either rutilt or wicd.  I dont believe ra chipsets and ndiswrapper have the same conflict.

It's just as simple as removing networkmanager?

---

### Post by rustybronco on 2007-10-29
When I tried it, wusb54g-v4, rt2570 chipset, can see networks but can't connect ( w/o a work-a-round) I believe it used rt2500pci upon the initial install. (needs rt2500usb?)
would not work with ndiswrapper also...

---

### Post by Flexo82 on 2007-10-29
The commands you have written doesnt work for me. It doesnt give me anything.
It might be because im a bit of a linux noob
Anyways, i have a Ralink RT73 with 7.10 build-in drivers. I have tried serialmonkeys drivers, Ndiswrapper, Ralinks own linux drivers.. But nothing worked so far

at the moment i can see my wireless network and i can connect to it (its WPA2 encrypted), but when i open a webpage it just says "looking up [insert webpage here]" and thats how far i have come.

---

### Post by fearevilleet on 2007-10-29
At least now I know it is an issues with the ra chipset.  So in order to fix this I need to remove the network manager, how do I do that?   have tried all of the suggested fixes, I disabled ipv6, used open dns and have done all the proposed updates for gusty yet my connection will not go over 200k tops when I was getting 700-800k in edgy. from doing an lspci, My current wireless card is
RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

EDIT:

I removed the network manager, and speeds are still slow.

I am going to give it one more week before I go back to my beloved edgy, who never game me any issues.

---

### Post by ivarka on 2007-10-29
```
01:06.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
```

```
driver=rt2500pci
```

Slow connection. Max 500 kbit/s

---

### Post by kevdog on 2007-10-29
This post is really not for assistance however there a two possible posts to help you guys with all of your ra problems (and there seem to be a lot of them)

Here are the two posts I would consult (if not get back to me in a separate post:
[http://ubuntuforums.org/showthread.php?t=584657](http://ubuntuforums.org/showthread.php?t=584657)
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Sometimes the link needs to be brought up and down (ifconfig up/down) 3 times in order to work.  I dont know why.

---

### Post by JoJerome on 2007-10-30
Intel 2200bg on a Dell Inspiron 6000 laptop. 

Initially had lots of drama getting this thing to work...
[http://ubuntuforums.org/showthread.php?t=580009](http://ubuntuforums.org/showthread.php?t=580009)
Still have some potential drama in making sure it will stay working.

Wound up completely reinstalling Gusty from scratch and *this time* knew how to look up existing settings before starting. Turned out (I think anyway) that the necessary drivers were already there. All I lacked was some minor network configuration to get the laptop to actually use said drivers.

If you're doing this for the purpose of updating instructions, my suggestion would be that the instructions start with how to look up existing settings (for us total newbies), and how to configure network settings once your wireless card is recognized but still not connecting.

Thanks for the (future) help!

- Jo

---

### Post by JoJerome on 2007-10-30
I should add...

When following your instructions in [http://ubuntuforums.org/showthread.php?t=580009](http://ubuntuforums.org/showthread.php?t=580009) Kubuntu ignored the instructions to change the name of my wireless device from eth1 to wlan0.

In the end, I found out that Gusty had the proper drivers for my laptop all along. All I needed to make it work from a fresh install was a small edit:

```

~$ kdesu kate /etc/network/interfaces

auto eth1
iface eth1 inet dhcp 
pre-up ifconfig eth1 up


```

Again, my suggestion is, for us noobs, to start driver install instructions off by showing us how to peek at the drivers and connections we already have.

Thanks for the help though - learned a lot in this process!

- Jo

---

### Post by Sudarevic on 2007-10-31
```
02:0a.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```
```
driver=rt61pci
```

Connection drops every 15 to 30 minutes, although Network Manager claims that everyithing is just fine. I can reconnect without problems, but it drops again after 15 to 30 minutes.

---

### Post by ghaz on 2007-10-31
> **Sudarevic said:**
> ```
02:0a.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
```
```
driver=rt61pci
```

Connection drops every 15 to 30 minutes, although Network Manager claims that everyithing is just fine. I can reconnect without problems, but it drops again after 15 to 30 minutes.

I have exactly the same card, driver and problems. These problems also occurred in Feisty.

My connection in windows also dropped every now and then, but I think I solved it by setting the card to g mode only. (it was on b/g mode). I've searched and searched, but can't figure out how to test this in linux.

[edit]
I should probably add that it happens under gnome using network-manager, under kde using the kde-wifi-manager and doing everything manually.

---

### Post by Grafster on 2007-10-31
03:00.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
driver=rt61pci

The same ralink problem as everyone else. Works for a few minutes after you try to tweek the settons, or reload, then drops the connection. This was easily fixable in fiesty with the existing, excellent driver. Not sure why somebody decided to "update it" with a driver that doesn't work (testing?) but some simple instructions on how to get back to the driver that works would be awesome.

PS Using an Acer Travelmate 230 with Xubuntu
the card itself is a D-Link Air Plus G WDL-G630

---

### Post by kevdog on 2007-10-31
These results are not quite what I expected.  I didnt forsee the most problem with ra based cards.

ATTENTION -- All those with Ra based chipsets.  I dont have a ra chipset wireless card, so its difficult for me to directly troubleshoot your problem.  Please have a look at this thread for reference:

I want anyone who is willing to compile the latest cvs version of the driver for your chipset from the serial monkey sources.  Please be aware that for your currently buggy rt module you will need to do two things:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

#1 - blackist the module in the /etc/modprobe.d/blacklist file
For example if you are running the rt61pci driver, you need to add one line in the blacklist file that states blacklist rt61

#2 - Physically unload the old module
For example if you are running the rt61pci driver (module), you would type at the command line:
sudo modprobe -r rt61

These two instructions combined with the thread above, I like to really get some feedback from some users if this improved, made worse, solved, or didnt do anything to improve the wireless situation.  I can answer any questions specifically if needbe.

---

### Post by Grafster on 2007-11-02
Kevdog,

While I think that people would very much like to help get this resolved. That thread is a monster. The first post alone has like 15 different steps people are supposed to perform, and if you don't really understand what you're doing and the thread applies to some other driver that we're not supposed to be using anyway.

I appreciate that you haven't got the hardware to test it, so why not revert back to the older driver?

---

### Post by kevdog on 2007-11-02
You might be new to the game -- I dont know -- but if you could rewind yourself back into feisty mode -- you could see all the problems people had with the old driver -- it wasnt reliable for about 80% of the people, so I really can not recommend it.  Maybe you could try to stumble along following the serial monkey thread and if you get it working, you could write your own howto for the rt61 card for gusty.  That would be a great addition, and then I would reference your thread.  

Its not really that hard.  Just some patience is required.

---

### Post by enzyme2000 on 2007-11-03
Doesn't automatically connect to wireless network on startup as it did in Feisty. Need to enter key twice before it connects. Connection slower than feisty. 

> $ lspci -nn | grep Network
02:0c.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=e100               
driver=rt61pci

Quite irritating when it worked fine in the previous version but doesn't anymore - give the impression of a backwards step. All else is fine with gutsy. Still very happy with ubuntu but would feel much better with this problem resolved!

---

### Post by jellystones on 2007-11-03
lspci -nn | grep Network
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=ipw3945            
driver=b44


Wireless works, but if I go into sleep mode and then resume, will (50% of the time) refuse to reconnect to my  wireless network. I have to restart my computer to reconnect.

---

### Post by Buster95 on 2007-11-03
Hello kevdog,
Laptop with rtl8187 internal usb wireless;
Wired connection works OK;
Two other users (1 XP, 1 Mac) of the wireless router have no problems, just me and my downloaded U 7.10.
Everything worked OK with Edgy. On Gutsy, the wlan0 is "not associated"
Tried ndiswrapper with a w98 driver, tried the driver that comes with the Gutsy download, tried a modified driver that I found on the site. Not sure whether I will run out of ideas or enthusiasm first!
Cheers

---

### Post by elmy on 2007-11-03
Hi,

I upgraded from Feisty to Gutsy this morning. My Gigabyte Aircruiser (ralink rt2561/rt61 chipset) is no longer working. I have no network connectivity at all.

It worked long enough after installing gutsy to realise that there are 5 updates available (probably until I rebooted after the upgrade completed), but I cannot get the updates

Only eth0: appears in Network Manager, but I do not have a CAT5 lead long enough to reach my switch to use that adaptor.

When I do a "sudo lshw -C network" it displays the adaptor details but does not show a logical name. eth0: appears as network:1

the driver that I appear to be using is epic100

regards
elmy

---

### Post by Grafster on 2007-11-03
I've been using Ubuntu for years. But I do not have l33t haxxor skilz.
I don't really know where I would fall on your "new to the game" scale.

I don't really know what you mean by "rewinding to feisty". If you mean going back to my old fiesty install it's gone. I do clean installs when I shift to a new version.
I'd just like to have an easy way to use the driver that worked instead of the new driver that doesn't work.Maybe it's not compatible with Gutsy. I don't know. There is apparently [some way to get the new driver to work]("http://ubuntuforums.org/showpost.php?p=3679593&postcount=31"). I'm having trouble getting it working in Xubuntu.

I understand you would prefer if people took a lot of time to troubleshoot the new version, and figure out why it's broken now. But obviously, I'm not part of this serial monkey project and I'm not a hardware hacker.

---

### Post by kevdog on 2007-11-03
Grafster

You dont need to be a hacker to get your card to work -- its only about 10-12 commands.  Look at it this way -- what is going to happen when you install Hardy Heron??  I really doubt that the wireless issues will be resolved in the new version.  You are going to have to invest the time how to learn how to set up your wireless device sometime.  Even if it were working right now, it will break in the future - trust me on that one.  Once you know how to manually setup your card -- you can do it real quickly the next time.  For the ra cards, Im down to like 30 seconds on the install.  Please step through the posts on depreius' thread, and then pm me back with the steps you are having problems with.  You definitely dont need to be a hacker to get this setup -- Im no hacker!

---

### Post by kevdog on 2007-11-03
If anyone finds a reliable solution for Realtek cards, I appreciate if they would post back the link for the solution.  Ive yet to find one reliable thread that works all the time.

---

### Post by abh83 on 2007-11-03
```
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

```
~$ lspci -nn | grep Network
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
```

```
~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=ipw3945            
driver=b44
```


Issue:

Internet is very slow when surfing. Occasional speed bursts. Downloading from updates/repos seems to be working fine but will lag occasionally. It seems to me the network status goes idle and then active (sending/receiving) again.

hope this helps!

---

### Post by rustybronco on 2007-11-03
> **kevdog said:**
> If anyone finds a reliable solution for Realtek cards, I appreciate if they would post back the link for the solution.  Ive yet to find one reliable thread that works all the time.
This thread looks promising for ralink chipsets, don't discount the users expertise, modifications to the configuration, on why it works sometimes.
[http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)
with the substitution of the chipset's proper tar.gz and reference to wlan-rausb-eth I don't see why it won't work for other ralink chipsets.
***just an observation*** I think 7.10 needs to use more specific drivers (rt2500pci-rt2500usb ect. ) for each chipset, then the problems people are having with getting the card  to connect, I believe will diminish.

---

### Post by kevdog on 2007-11-03
Looking at the serial monkey site they have a rt2500 driver -- thats it.  What the heck is the difference between the rt2500pci and rt2500usb driver??  Are they really just the same driver?? Do they only set differ in that they set up a different interface name??  Seems like the rt2500 driver should be the same for both.

---

### Post by Grafster on 2007-11-03
> **kevdog said:**
>   Look at it this way -- what is going to happen when you install Hardy Heron??  
You mean... I'll be stuck in the same situation as I am in now?
I can follow instructions, even long ones, fine. That thread isn't even about my card or driver.... it's about some other card or driver. I've skimmed it and I understand so little of what's being said that I can tell it'd be 6-12 hours of work.
And even then it will probably end with "Oh, this thread isn't for your card. You need to be using some other method"

The old driver worked fine/great. Someone will figure out how to 'get it back' (or whoever decided to switch us to this new driver without testing it will give up on getting everyone to debug their code and just put it back) and we'll be back in business.

It's possible that Hardy will have no forward developments... but Ubuntu's number one issue is really hardware/device compatibility. If it worked before for the average user someone with the proper skill set will take a few minutes to get this squared away eventually. I have faith.

---

### Post by Speedoo on 2007-11-03
I had problems with my Realtek rtl8187.  It would drop out at random, and sometimes wouldn't reconnect.  Also, I frequently had a connection strength of "o%".  I solved the problem by downloading the Win 98 driver (netrtuw?) and ndiswrapper.  My wireless works now, but here's what my lshw -C Network command shows:

 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:c0:a8:f1:1b:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.189 multicast=yes wireless=IEEE 802.11g

Something here isn't right, but I'm not too concerned since my wireless is actually working now.

---

### Post by Jbanicar on 2007-11-04
Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223]

Driver= tg3


Wireless isn't even an option to me nor does it detect any when I am clearly in a place where there is a wireless signal.  I've tried Wicd also but nothing.

---

### Post by kevdog on 2007-11-04
For all people trying to troubleshoot your wireless connection, you are going to have to get intimate with your linux system and troubleshoot your wireless problems at the command line.  

Posting what happens when you use network manager, ifconfig, or your /etc/network/interfaces file is no help.

Usually wireless problems boil down to
1. Wireless driver not installed
2. Wrong wireless driver is installed or being used
3. Wireless driver (module) is installed, however module is not loaded either at boot or at the command prompt
4. Attempting to connect to a WPA network before testing the installation with an unencrypted network (in most cases the wpasupplicant package needs to be installed for WPA to work -- and this needs to be downloaded from the internet repository -- hence the reason to get an unencrypted connection first, download the wpa_supplicant package, install and configure the package, and then change the router settings)
5.Various other problems
   Incompatibilities of ra driver with network manager
   Bad bcm43xx broadcom restricted driver
   Orinoco, hostap driver -- driver(module) name changed from feisty to gutsy -- what a mess
   Wireless card and router on different wireless channel
   Realtek (r8180 rtl8187, rtl818x) -- driver reported by many to hand with long downloads

Usually problems in #5 are easy to troubleshoot and fix.  Problems #1, #2, #3 usually encompass the majority of wireless problems.

lshw -C network

This command is crucial.  It will tell you if your device is claimed or UNCLAIMED -- UNCLAIMED means no driver is associated with the card.  If your device is claimed, the driver that is asssociated with the card will be shown.

lsmod | grep <module name>

This command will tell you if the driver module is loaded.  These are examples how to use this command:

lsmod | grep rt
lsmod | grep ndis
lsmod | grep ipw
lsmod | grep bcm

If you issue the command
iwlist scan

(this command scans for available networks in the area) and networks are shown, then the driver is installed and working, and the problem is related to configuration parameters.

---

### Post by elfed on 2007-11-04
I've only been an Ubuntu user for 2 weeks - most of which has been spent in trying to get wireless working!  Have tried two PCI wireless cards:

ZyXEL G302-3 PCI card (RTL 8180 chipset). This is on the list of supported cards. Works OK when authentication switched off but no go with WPA1-PSK.  I've endeavoured to follow the suggestions from several forums to get authentication to work but no joy.  Galling as it feels its just something small that prevents it working!

Belkin Wireles G PCI card (RT2500 chipset).  Works, including WPA-PSK, but drops the connection fairly regularly.  This was why I tried the ZyXEL card as the Belkin was also not very reliable under Windows.  (Perhaps some incompatibility with the router - ZyXEL 660-HW?)

---

### Post by rustybronco on 2007-11-04
> **kevdog said:**
> Looking at the serial monkey site they have a rt2500 driver -- thats it.  What the heck is the difference between the rt2500pci and rt2500usb driver??  [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)
Can't help with the rt2500 pci's chipset, but the rt2500usb has a rt2570 chipset.

---

### Post by kevdog on 2007-11-04
> Can't help with the rt2500 pci's chipset, but the rt2500usb has a rt2570 chipset.

That doesnt make much sense to me.  Why would the call it rt2500usb rather than just rt2570??  Seems like it would solve a lot of confusion.

---

### Post by rustybronco on 2007-11-04
> **kevdog said:**
> That doesnt make much sense to me.  Why would the call it rt2500usb rather than just rt2570??  Seems like it would solve a lot of confusion.Agreed, most people don't know what chipset they have or how to find out that info, then to throw conflicting information into fixing their wireless problem? 
time for more ralink driver inclusion in 8.04 to enable that.

---

### Post by JohnBr on 2007-11-04
I'm having a problem with a Marvel chipset that worked fine under Ndiswrapper under 7.04.
It now states "invalid driver" 
Chipset:  Marvell Technology 88w8335

iwconfig gives report "No wireless extensions"

---

### Post by kevdog on 2007-11-04
For the marvell chipset (didnt know that marvell made wireless chipsets), I would definitely troubleshoot your ndiswrapper installation since that's the only way I know of making it work. ndiswrapper hasnt really changed in the two versions.  I prefer installing from source code.

---

### Post by Buster95 on 2007-11-05
> **kevdog said:**
> For all people trying to troubleshoot your wireless connection, you are going to have to get intimate with your linux system and troubleshoot your wireless problems at the command line.  

Posting what happens when you use network manager, ifconfig, or your /etc/network/interfaces file is no help.

Usually wireless problems boil down to
1. Wireless driver not installed
2. Wrong wireless driver is installed or being used
3. Wireless driver (module) is installed, however module is not loaded either at boot or at the command prompt
4. Attempting to connect to a WPA network before testing the installation with an unencrypted network (in most cases the wpasupplicant package needs to be installed for WPA to work -- and this needs to be downloaded from the internet repository -- hence the reason to get an unencrypted connection first, download the wpa_supplicant package, install and configure the package, and then change the router settings)
5.Various other problems
   Incompatibilities of ra driver with network manager
   Bad bcm43xx broadcom restricted driver
   Orinoco, hostap driver -- driver(module) name changed from feisty to gutsy -- what a mess
   Wireless card and router on different wireless channel
   Realtek (r8180 rtl8187, rtl818x) -- driver reported by many to hand with long downloads

Usually problems in #5 are easy to troubleshoot and fix.  Problems #1, #2, #3 usually encompass the majority of wireless problems.

lshw -C network

This command is crucial.  It will tell you if your device is claimed or UNCLAIMED -- UNCLAIMED means no driver is associated with the card.  If your device is claimed, the driver that is asssociated with the card will be shown.

lsmod | grep <module name>

This command will tell you if the driver module is loaded.  These are examples how to use this command:

lsmod | grep rt
lsmod | grep ndis
lsmod | grep ipw
lsmod | grep bcm

If you issue the command
iwlist scan

(this command scans for available networks in the area) and networks are shown, then the driver is installed and working, and the problem is related to configuration parameters.

Hello kevdog,
Cut-and-paste below.

When I run lshw, it seems to tell me that I have wlan0

When I run lsmod, it seems to tell me I have a driver loaded.

When I run iwlist scan, it seems to tell me that it can see my router OK.

All in all, it SEEMS to be working perfectly. One teensy little problem - it doesn't!

I'd very much appreciate some guidance through this infuriating problem.

Cheers

dexter@dexim-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:90:f5:57:ba:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.4 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:12:7d:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

dexter@dexim-laptop:~$ lsmod | grep rtl
rtl8187                35328  0 
mac80211              171016  2 rc80211_simple,rtl8187
eeprom_93cx6            3200  1 rtl8187
usbcore               138632  5 usbhid,rtl8187,ehci_hcd,uhci_hcd

dexter@dexim-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

[COLOR="black"]wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:C0:B8:D6
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Quality=57/64  Signal level=65/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000002d947b4234[/COLOR]

dexter@dexim-laptop:~$

---

### Post by kevdog on 2007-11-05
```
dexter@dexim-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 7c
serial: 00:90:f5:57:ba:bb
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.4 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:15:af:12:7d:b7
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

Good learning example for you (and everyone)

The top device is your wired connection, the bottom your wireless.  The top device lists via-rhine as the driver.  There is no driver listed for the bottom device.  Hence you have a driver module problem.  You didnt list the chipset of your wireless device, so I have no idea what driver you are supposed to use.  lspci -nn gives you the chipset.

---

### Post by Buster95 on 2007-11-06
> **kevdog said:**
> ```
dexter@dexim-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 7c
serial: 00:90:f5:57:ba:bb
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.4 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
*-network
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:15:af:12:7d:b7
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

Good learning example for you (and everyone)

The top device is your wired connection, the bottom your wireless.  The top device lists via-rhine as the driver.  There is no driver listed for the bottom device.  Hence you have a driver module problem.  You didnt list the chipset of your wireless device, so I have no idea what driver you are supposed to use.  lspci -nn gives you the chipset.

Thanks for taking the trouble to help, kevdog.
That's exactly what I was confused about. I could see that wlan0 didn't associate a driver, but when I invoke iwlist scan, it seems to indicate that it is working.

I've pasted both the iwlist scan to show what I mean and the lspci -nn result, which I am having trouble interpreting.
Thanks again

o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:C0:B8:D6
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Quality=58/64  Signal level=65/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000004217628234


dexter@dexim-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:0364]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:1364]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:2364]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:3364]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:4364]
00:00.5 PIC [0800]: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller [1106:5364]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. P4M900 Security Device [1106:6364]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. P4M900 Host Bridge [1106:7364]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller [1106:a364] (rev 80)
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller [1106:c364] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT8237A SATA 2-Port Controller [1106:0591] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev a0)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237A PCI to ISA Bridge [1106:3337]
00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8251 Ultra VLINK Controller [1106:287e]
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
00:13.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. Chrome9 HC IGP [1106:3371] (rev 01)
06:01.0 Audio device [0403]: VIA Technologies, Inc. VIA High Definition Audio Controller [1106:3288] (rev 10)
07:04.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730]
07:04.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller [1524:0750]
07:04.3 FLASH memory [0501]: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller [1524:0751]
dexter@dexim-laptop:~$

---

### Post by casagan on 2007-11-06
Belkin F5d7000ef, based on RT61 chipset.

Gutsy uses the rt61pci driver, I can see my network, but I cannot connect. I´ve tried WPA and WEP. Back in Feisty I tried everything, from compilation of drivers to ndispwarpper and nothing. 

I am a bit tired of this. The problem is that I even have problems to find a wifi card which works out of the box. The rest of Gutsy is working perfectly.

Casagan.

---

### Post by kevdog on 2007-11-06
Buster95

Are you using a usb device??  Usb devices do not use the pci bus, so they will not show up with the lspci statement.

---

### Post by natille on 2007-11-06
> lspci -nn | grep Network

Yields:
```
01:07.0 Network controller [0280]: Texas Instruments ACX 111 54 Mbps Wireless Interface [104c:9066]
```

I'm having an issue where wlan0 disappears after rebooting my machine and I can't find a way to make it come back even though the driver claims to be installed and the device claims to be found.

---

### Post by Buster95 on 2007-11-07
> **kevdog said:**
> Buster95

Are you using a usb device??  Usb devices do not use the pci bus, so they will not show up with the lspci statement.

Hello kevdog,
This crappy laptop I'm using has an internal usb wireless setup as you can see from the following paste:

dexter@dexim-laptop:~$ lsusb
Bus 005 Device 002: ID 0402:5602 ALi Corp. 
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d62:1000 Darfon Electronics Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
dexter@dexim-laptop:~$ 

As far as I can deduce, my dmesg file reports absense of a wireless card (I've pasted a small part of the dmesg file below to show what I mean). However, the card was there when I used Edgy (and XP before that). It "evaporated" with Fiesty and stayed that way with Gutsy. Also, other users of my wireless router have no problems. They use XP and MacOS.

I have tried Realteks latest drivers, modified drivers from this forum, ndiswrapper plus lots of tweaks and fiddles. But, to paraphrase Omar Khyyam "I went out the same door wherein I went"

Cheers

paste of part of dmesg

[   38.755610] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 17 (level, low) -> IRQ 22
[   38.755643] PCI: Setting latency timer of device 0000:06:01.0 to 64
[   38.779832] ieee80211_init: failed to initialize WME (err=-17)
[   38.819660] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   38.819703] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   38.819739] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   38.819798] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   38.820177] wmaster0: Selected rate control algorithm 'simple'
[   38.904783] phy0: hwaddr 00:15:af:12:7d:b7, rtl8187 V1 + rtl8225
[   38.904811] usbcore: registered new interface driver rtl8187
[   39.620699] lp: driver loaded but no devices found

---

### Post by kevdog on 2007-11-07
Buster -- no idea on this one.  Never seen this problem before.  Sorry.

---

### Post by Ronin69 on 2007-11-08
Good News:  I am not alone in having issues.

Bad News:  I am having issues

I've traced it down (I think) to the router connection.  When I try to ping the router I fail, but I am OK on the loopback.

I am using an rt61 chip with Kubuntu 7.10 fresh install.  Like many of the others this is rather frustrating, but it's also a learning experience.  The question of course will I learn how to resolve the issue?  Or will I learn to stick with the boring Windows?

Because I can ping the loopback does this indicate a working driver?  If yes, can I simply make a change to the interface file to have the default gateway recognized (since this seems to be lost).

Thanks in advance for any advice.

---

### Post by justinflavin on 2007-11-08
i get a total system lock on Feisty when i try to upload via SFTP or rsync - RTL8185 wireless
only way out of it is to press the reset button.
kernel panic?

>uname -r 
2.6.20-16 generic

>lspci | grep "Ethernet"
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
06:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)


i can't migrate to Gutsy because when i tried the live CD it didnt even get beyond the splash screen.

Gateway ML-3108b laptop
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)


besides this upload "hard lock" , my wireless works just fine.

---

### Post by EduMan on 2007-11-08
warden@DeskMatrix:~$ lspci|grep Marvel

02:0e.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by jwmislan on 2007-11-09
Hi all
I updated from feisty a couple of days ago and had wireless not working at the end of the update.
I guess you've heard it all already - wpa un-configurable -,wep,and open connections slow, connection just cuts out , and so on. 

When my wireless was dropping the connection frequently, I was convinced that it was a driver problem, and started looking at the drivers that were issued for gusty, in my case it's, rt61pci - and a couple of new friends namely, rt2x00pci, and rt2x00lib .

My wireless - a realtech -
product: RT2561/RT61 rev B 802.11g
Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]
logical name: ra0

Doing some net hunting - (I have another computer, with a wired network, running feisty)
I found quite a bit of info at -http://rt2x00.serialmonkey.com/wiki

Driver downloads are here -> [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

I downloaded  the rt61 (PCI/PCMCIA) -  halfway down the page

[http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

to my ~/src folder - and read the readme  
 
typed make to build the rt61.ko module
typed sudo make install to install it as root.

now sudo ifdown ra0   (to shut down wireless interface)   

Now to unload the gusty wireless modules I did 
sudo rmmod rt61pci 
sudo rmmod rt2x00pci
sudo rmmod rt2x00lib

Now I loaded my newly compiled rt61 module
sudo modprobe rt61

Now to keep the gusty issued wireless module from loading at boot
go to /etc/modprobe.d/blacklist and type in
blacklist rt61pci
[B]
UPDATE !!  DON'T BLACKLIST THE  rt61pci  MODULE or else on next boot, network fails to complete settings, I got -  'cant find firmware error'.
leave everything alone and boot as normal - let the gusty issued modules load as usual.
Once logged in then issue the commands to rmmod the old rt61pci module, and modprobe the new rt61 module.
I just put a bash script on my desktop to do this 

StartWifi.sh

 #!/bin/sh
sudo modprobe --remove rt61pci
sudo modprobe rt61

Set the script to executable - right click - Properties - Permissions - allow executing file as program
This works great and doesn't hurt too much to do.
  [/B] 

Now I need to have rt61 load at boot. I could use /etc/network/interfaces file and, add
pre-up modprobe rt61
there may be a better way though like modconf, /etc/modules, or other.
[B]UPDATE !! this was a solution in the past - but not working now, in Gusty, I got problems during reboot - 'firmware not found error'
may be alias was not set when I compiled or some other problem - 
So I just do it the  'Script way' for now.
 [/B]
 
I don't know yet if my new rt61 is going to pull in rt2x00pci and rt2x00lib with it when it loads so I did not blacklist those.
[B]UPDATE !! These don't show up in lsmod  list after running my startWifi.sh desktop script - just the new rt61 is listed 
[/B]

Wow What an improvement ! 

 It was worth it and only took me about 30-45 minutes. I was impressed that the serialmonkey driver compiled quite easily. 
There is a huge improvement with this module compared to the buggy gusty issued mod..
There are no drop-outs any more as well as notable connection speed increase. 

I try to be of some help here to you folks - I 'm still not totally out of the woods yet myself so lets see what happens tomorrow 

Cheers
John WM

---

### Post by rtmie on 2007-11-09
**My Card**
01:05.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Belkin F5D7000 Wireless G Desktop Network Card
        Flags: bus master, slow devsel, latency 32, IRQ 17
        Memory at fdefc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2


**My Problems**
Periodically losing network connection
Poor throughput

Don't get me started on graphics drivers, XEN etc.
I knew Ubuntu fancied challenging Vista with this release but I didn't think it would be in the "Not Ready For Release" Stakes :(

---

### Post by Shinbu-Otaku on 2007-11-09
i keep having a problem with mine, but found a temporary solution (also kinda temperamental...)

p.s. most prob will only with WEP/WPA encrypted connections

Go to administration > Network, and into the properties of the WiFi connection. Now change the format of the encryption (i change mine from hexadecimal to ascii) and accept. Ubuntu will now change the config. Once its done, go back in to the preferences and change it back (e.g. from ascii to hexadecimal again) and let ubuntu do its thing again. Now, open up your browser and *hopefully* it now works...

If not, restart the comp and try again lol

hope tht helps (not sure if someone had submitted this already, didnt get a chance to read through it all

---

### Post by kevdog on 2007-11-09
To make the rt61 module load at boot

echo rt61 | sudo tee -a /etc/modules

For rt2500 problems, I would recommend serial monkey driver compilation.  Look a few posts back and in the post immediately preceeding yours.  There are also a lot of other good tutorials in the forums.

---

### Post by wieman01 on 2007-11-09
The usual suspect, Kevdog. A Ralink 2570. "ndiswrapper" eventually did the job for me, but I hate to admit it. I hope the next version of (K)Ubuntu will fix it. I am tired of using workarounds.

---

### Post by kevdog on 2007-11-09
Wieman 

Did you try serialmonkey driver installation??? Im just looking for some feedback from someone to tell me if this worked??  A few people have revisted this particular post to tell of success stories, but not a lot.  Any type of feedback would be great.

The other thing that makes me kind of laugh is that Gusty is supposed to have support for ra and broadcom chipsets right out of the box (might need internet connection in case of broadcom cards but you get what I mean).  If you look at the problems people are having though, these two chipsets lead the list.  Unsure however if this is a reflection of the true percentages of problems, or that there are just so many more wireless devices with these two particular chipsets installed.  My thread asking people to just post the wireless chipset and driver was a bust -- I was just trying to figure out the relevant percentages of chipsets usied in ubuntu and was going to compare this to the number of problems people were having with each particular chipset.  (Quasi scientific study with a control group!!) Guess Ill never know the latter information.

---

### Post by wieman01 on 2007-11-09
> **kevdog said:**
> Wieman 

Did you try serialmonkey driver installation??? Im just looking for some feedback from someone to tell me if this worked??  A few people have revisted this particular post to tell of success stories, but not a lot.  Any type of feedback would be great.

The other thing that makes me kind of laugh is that Gusty is supposed to have support for ra and broadcom chipsets right out of the box (might need internet connection in case of broadcom cards but you get what I mean).  If you look at the problems people are having though, these two chipsets lead the list.  Unsure however if this is a reflection of the true percentages of problems, or that there are just so many more wireless devices with these two particular chipsets installed.  My thread asking people to just post the wireless chipset and driver was a bust -- I was just trying to figure out the relevant percentages of chipsets usied in ubuntu and was going to compare this to the number of problems people were having with each particular chipset.  (Quasi scientific study with a control group!!) Guess Ill never know the latter information.
I tried Serialmonkey's driver over 18 months ago, but haven't since. Currently I don't want to mess around with it, because "ndiswrapper" does a good job. I'll wait until Ubuntu recognizes & fully supports it. Never change a running system, buddy. :-)

As for your survey, you should also include a section for people that had no issues with particular chipsets. That way, it'd be a bit more representative. But then again, people who no trouble with theirs are unlikely to post for they might not even know what chipset they have, you know what I mean. I doubt you will get a representative statistic, however, I like it nevertheless.

---

### Post by kangabroo on 2007-11-09
> Did you try serialmonkey driver installation??? Im just looking for some feedback from someone to tell me if this worked?? A few people have revisted this particular post to tell of success stories, but not a lot. Any type of feedback would be great
I tried serialmonkey's cvs daily rt2570 yesterday with WEP on a 64-bit system. This would work for  a while but would then cut out. In the end I gave up and went back to wire. The device, a USB Linksys HU200, had previously worked on a 32-bit system with ndiswrapper.

The rt2x00 daily required git and custom kernel building of 2.6.23 so I did not try it.

---

### Post by kevdog on 2007-11-09
Im not sure with the rt2x00 is ready for prime time yet.  I know one ubuntu user was successful at getting it up and running (Austin_KW), however he said it was very difficult and that at the time it wasnt too stable.  This was with the Feisty kernel and was probably 4 months ago (if I'm remembering correctly)

---

### Post by Ronin69 on 2007-11-09
John -- nice write-up.  I look forward to trying this out.

If this doesn't work I imagine I can just roll back to the previous config.

---

### Post by jwmislan on 2007-11-09
Thanks Ronin69

 Before doing anything though - go back and read the updates in my post.
I found some issues that I didn't check yesterday.
It's on page 6 of this thread.

So if you use a modprobe-script like i'm doing, you don't have to roll back anything because nothing changes until you run the modprobe-script after login.
You can see this in the updates to my post.

11-9-07
John WM

---

### Post by K8A on 2007-11-09
Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

In a Thinkpad T30 (bit of a Frankenstein) 

When I first upgraded to gusty, my wireless setup was working ok, though not perfectly. It would work for a few days. After about 5 or 6 hibernations, without a restart, no wireless signals would show up. A restart would fix it for another 5-6 hibernation cycles. 

I was ok with that on a functional level.

Now, it no longer works so smoothly. 
When I come back from hibernation, it claims to see the same wireless signals that it saw in the last location I connected. However, it is otherwise unresponsive. If I am in the same location as before, it will claim to still be connected, but won't be. If I'm in a different location, it will claim to be connected to the same wireless signal as before, even if I am out of range. Regardless, it is not really connected. I also cannot connect to a wired connection when it is in that state. The only way that I can network at all is via a restart. If I'm connected to a wired connection when I restart, it will allow me to use that wired connection. If I'm not wired, it will connect to one of the wireless signals, but then not allow me to switch to another.

---

### Post by corncob on 2007-11-09
Chipset = Ralink RT2561/RT61 802.11g PCI
Driver=rt61pci
It worked fine in Feisty but in Gutsey, both in the fresh install and upgrade, I have to untick and then retick the wireless connection in Network Settings.  A window then opens, briefly, saying "Changing Interface Configuration" and then I'm connected.
Here's my attempt to remove networkmanager:

corncob@trailer-desktop:~$ sudo dpkg -r networkmanager
[sudo] password for corncob:
dpkg - warning: ignoring request to remove networkmanager which isn't installed.
corncob@trailer-desktop:~$ 

Did I do something wrong?  I'm a real newbie.

---

### Post by hkramski on 2007-11-09
D-Link DWL-610, seen as: 02:00.0 Ethernet controller [0200]: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter [1186:3300] (rev 20)

Was working in Feisty, had to manually load module r818x there.

This module (r818x) seems to be missing in Gutsy, and r8180 is loaded automatically instead. However, r8180 crashes with a kernel panic when trying to establish a WEP connection.

Workaround: use ndiswrapper (gets better performance, too).

Deinstalled "Network-Manager[-Gnome]" who never got my network interfaces right.

Regards,
   Heinz

---

### Post by krumble on 2007-11-09
Chipset: Realtek
Driver: rtl8180
Computer type: Laptop - Gateway ML3109

Problem: It worked fine with edgy didn't have to do anything to it.  When I got Gutsy I had problems Loading the OS.  I figured that I will load when the wireless is turned off. (FN key and F2 turns off my wireless.)  Well after it loads up I am able to turn the wireless back on and work without any problems.  I can't connect to any wireless networks because it says it is disconnected for "wlan0".  When I mess with the network settings like uncheck the box or change it to roaming mode, my computer will freeze and I have to reset the whole thing.  Any ideas or solutions is greatly appreciated.  
Thanks, Jon

---

### Post by enzyme2000 on 2007-11-09
> **Grafster said:**
> You mean... I'll be stuck in the same situation as I am in now?
I can follow instructions, even long ones, fine. That thread isn't even about my card or driver.... it's about some other card or driver. I've skimmed it and I understand so little of what's being said that I can tell it'd be 6-12 hours of work.
And even then it will probably end with "Oh, this thread isn't for your card. You need to be using some other method"

The old driver worked fine/great. Someone will figure out how to 'get it back' (or whoever decided to switch us to this new driver without testing it will give up on getting everyone to debug their code and just put it back) and we'll be back in business.

It's possible that Hardy will have no forward developments... but Ubuntu's number one issue is really hardware/device compatibility. If it worked before for the average user someone with the proper skill set will take a few minutes to get this squared away eventually. I have faith.

> **kevdog said:**
> For all people trying to troubleshoot your wireless connection, you are going to have to get intimate with your linux system and troubleshoot your wireless problems at the command line.  

Posting what happens when you use network manager, ifconfig, or your /etc/network/interfaces file is no help.

Usually wireless problems boil down to
1. Wireless driver not installed
2. Wrong wireless driver is installed or being used
3. Wireless driver (module) is installed, however module is not loaded either at boot or at the command prompt
4. Attempting to connect to a WPA network before testing the installation with an unencrypted network (in most cases the wpasupplicant package needs to be installed for WPA to work -- and this needs to be downloaded from the internet repository -- hence the reason to get an unencrypted connection first, download the wpa_supplicant package, install and configure the package, and then change the router settings)
5.Various other problems
   Incompatibilities of ra driver with network manager
   Bad bcm43xx broadcom restricted driver
   Orinoco, hostap driver -- driver(module) name changed from feisty to gutsy -- what a mess
   Wireless card and router on different wireless channel
   Realtek (r8180 rtl8187, rtl818x) -- driver reported by many to hand with long downloads

Usually problems in #5 are easy to troubleshoot and fix.  Problems #1, #2, #3 usually encompass the majority of wireless problems.

lshw -C network

This command is crucial.  It will tell you if your device is claimed or UNCLAIMED -- UNCLAIMED means no driver is associated with the card.  If your device is claimed, the driver that is asssociated with the card will be shown.

lsmod | grep <module name>

This command will tell you if the driver module is loaded.  These are examples how to use this command:

lsmod | grep rt
lsmod | grep ndis
lsmod | grep ipw
lsmod | grep bcm

If you issue the command
iwlist scan

(this command scans for available networks in the area) and networks are shown, then the driver is installed and working, and the problem is related to configuration parameters.


Sorry Kevdog, I think you might have missed Grafster's point and it is one that I'm also frustrated with now that I've "upgraded" from Feisty to Gutsy. Wireless networking worked every time, flawlessly in Feisty. Now that I've "upgraded" to Gutsy is doesn't.

I understand the point that you're trying to make with networking. It is very handy to educate yourself to understand every aspect of wireless networking and find ways to trouble shoot those problems. Much as it could be useful to have an in-depth understanding of spark plug manufacturing if you had car troubles. It's a very nice idea if you have the time to do it and you have any interest whatsoever with compiling drivers and performing command line tasks. But I and many others don't have the time nor interest to do this and I don't think that's what Ubuntu is all about.

Ubuntu is about having it work without any problems and not needing to deal with command line of you aren't interested or inclined to do so. Feisty, for me and (I think) Grafster, allowed this. The "upgrade" to Gutsy, and horrifyingly Hardy as you claim, is to make wireless networking harder and less reliable. This would be considered by most people who want something that "Just Works" to be a step back, not an improvement.

The other users in my house are also getting frustrated with the "internet always being down because of this 'stupid' operating system" and there is pressure on me to reinstall windows. I don't want that. I want wireless networking to work as it did in Feisty and if anyone has any suggestions how I can easily roll wireless networking back to Feisty, I'd be very interested in finding out how.

---

### Post by kevdog on 2007-11-09
I understand your frustration -- however writing to me about how Gusty isnt working and how you would like to have Feisty back is not productive.  I have no input in the development of Gusty, and no one has ever asked me for my opinion.  Im here to help you get your internet up and going.  Ubuntu isnt windows (good in many respects, but also bad in others).  If you post some details about your problem I can help you the best way I know how, however venting to me about the short comings of Gusty -- I really cant change any of it!

---

### Post by enzyme2000 on 2007-11-09
Sorry Kevdog

I reread my post and can see how you might have thought that that I was having a go at you and the assistance you're providing... This was not my intention.

I and many other are frustrated by the problems we're having with wireless networking since the release of Gutsy and that is what I was trying to convey. The support we receive from valuable online community members like you is always valued and it would appear that you personally put a lot effort into helping people. Please do not let my current Ubuntu frustration deter you from doing this!

My hope is that anyone that is involved in the development of Ubuntu is listening to the experiences that newish users are having so that it can improve Ubuntu with each release rather than go backwards as it did for me when I installed Gutsy.

Regardless, I'll check out the suggested fix that you've put together and hope for the best.

---

### Post by kevdog on 2007-11-09
Yes i hope someone is listening too -- however in actuality many of the drivers included in the Ubuntu compiled kernel simply come from outside developers, and ubuntu simply includes them in their kernel.  Im not too sure if the ubuntu developers actually work on the drivers themselves.  (If you ever compile your own kernel from the vanilla source you will know what Im talkiing about).  

Anyway post some details (specific details) about your card, driver, etc, and Im sure I can provide some help.

---

### Post by enzyme2000 on 2007-11-09
*-network:1
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: wmaster0
       version: 00
       serial: 00:19:5b:6e:97:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.2.2 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
~$ sudo ifconfig wmaster0 down
[sudo] password for user:
~$ sudo dhclient -r wmaster0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
~$ sudo ifconfig wmaster0 up
~$ sudo iwconfig wmaster0 essid "HandyCon"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wmaster0 ; Operation not supported.
~$ sudo iwconfig wmaster0 key a69cc3af9f
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wmaster0 ; Operation not supported.
~$ sudo iwconfig wmaster0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.
~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
--------------------------------

KevDog,

See above for the output when I was troubleshooting, Things went badly when I issued the command "sudo dhclient -r wmaster0" but I followed all of the instructions and included the output in the hope that it might offer a few clues to the problem (and the solution perhaps). It's probably something very obvious to you but at my current level of wireless networking skills, I can't work out the answer to the problem. Any suggestions are welcome.

---

### Post by jfank on 2007-11-09
I have a Intel Corporation PRO/Wireless 3945ABG Networ                                                                                                 k Connection [8086:4222] (rev 02)  with the following drivers:  driver=sky2
driver=ipw3945

That is the information that was givin to me in the terminal.  I'm running on Kubuntu.  When I go to connect to the internet it says CONNECTION FAILED.  I'm also using the WEP Security Key so that my network is secure,  I'm trying to figure out how to get the wireless to connect, but nothing is working for me.  My system is also telling me that the wireless network card on my computer is a restricted driver.  Please help me with this.  If more information is needed, let me know what information you need and I will do my best to provide the information.  Thank you for the help.  I'm still new to Linux so still learning what to o on here.

---

### Post by kevdog on 2007-11-09
Your wireless driver is the ipw3945 -- it is a restricted driver -- no need to worry about this. Try connecting from the command line to generate so better debugging output.  The instructions are in my signature.  So far the info provided to me doesnt tell me anything why you would be having a problem.

---

### Post by salefish on 2007-11-11
ra2500, on an Averatec 3250HX1
I have tried to follow the serialmonkey and ndiswrapper tutorials in the forums, but I believe people are skipping step that are obvious to all but the newest users (Me). So, at this point I have had no luck. If anyone can tell me step by step, in small words without skipping something how to use these, please do.

---

### Post by kevdog on 2007-11-11
Why dont you just post the steps you did so we can take a look?  Its a lot easier to troubleshoot if you give us some output.

---

### Post by Godsgimp on 2007-11-12
08:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

I have no trouble connecting to my work wireless network and several other networks. But my home network is detected and it does attempt to connect. However it never gets the connection it just hangs forever and finally I have to try and quit it..

---

### Post by Paradoxfox93 on 2007-11-16
Out of the box installed or on LiveCD Gutsy would crash on me.  I ended up just installing feisty without any crashes.  Though getting wireless to work is a PIA , at least it's not crashing on me every time I to connect to the network (Wireless or Wired).

This Occured Running 64bit Gutsy on this machine:

[http://www.newegg.com/Product/Product.asp?Item=N82E16834101093](http://www.newegg.com/Product/Product.asp?Item=N82E16834101093)

Which is a Realtek 8185 wireless card.  Driver would have been out-of-the-box. After 9 hours and a few dozen crashes....I just gave up and went with feisty.

---

### Post by nicoladinisio on 2007-11-16
I have an RaLink RT61

00:0e.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]

driver=rt61pci

It was running flawlessly in Kubuntu Feisty Fawn.
Since when I updated to Gutsy Gibson, I have experienced network problems in average once every two days, normally fixable through a "sudo /etc/init.d/networking restart".
However the BIG issue is that since my last update of yesterday, my network wireless is no longer working, I had to setup a wired connection again to write this post... (thank God I haven't thrown away the cable!)

Cheers
Nicola

---

### Post by kevdog on 2007-11-16
The ra drivers were supposedly updated in Gusty, however a lot of people are having problems with the newer drivers.  They either revert to Feisty, or compile the serial monkey drivers from source.  i wish I had a better option for you.

---

### Post by phillywize on 2007-11-18
> **Speedoo said:**
> I had problems with my Realtek rtl8187.  It would drop out at random, and sometimes wouldn't reconnect.  Also, I frequently had a connection strength of "o%".  I solved the problem by downloading the Win 98 driver (netrtuw?) and ndiswrapper.

I have a RTL8187 chipset as well, and have exactly the same problem.  Any way to make it work without going ndiswrapper?  I'm hesitant to go the ndiswrapper route only because I've heard that ndiswrapper and network-manager don't work together.

Is this so?

I don't want to lose nm (a) because it supports a simple interface for the pptp connection I need for work; and (b) it's one of the better things to happen to the world of linux interfaces recently.

A work around of sorts is to suspend my system and restart it, which restarts whatever subsystem dies when the RTL8187 randomly stops working.

Also, my wifi card uses an internal usb port, so it goes through the usb subsystem.  Thus, I'm also going to try restarting  udev next time it happens:

```
sudo /etc/init.d/udev restart
```
I think this is a bit of a blunt approach, and probably functionally the same thing as the suspend/resume operation.  I'll post results on that.  

Is there a more surgical way to "restart" a specific usb device?

Thanks!

---

### Post by medomedo on 2007-11-18
I have many problems,

With hostap driver used against Prism Intersil 2, when I pull out the PCMCIA card and replug it in, the system hangs.

Rt8081 is not recognized at all, just a line in dmesg somting like "injected card in pcmcia0.0". When I try to compile rt8180 driver, all files in the drivers's directory gets deleted.This problem (files gets deleted) is also observed when i try to compile ipw2200-ap driver.

---

### Post by kevdog on 2007-11-18
I wish I could help both you guys.  I have no experience with orinoco, hostap, prism, or rtl chipsets.

Just some thoughts which could be totally incorrect.  I thought that orinoco, prism, and hostap drivers were by default included in the kernel.  At least when you compile a vanilla kernel you have the option of compiling these drivers as dynamic modules (if you want).  Perhaps these particular drivers (kernel modules) do not work for your card, I really dont know.  The prism54.org project -- who knows where the development of this open source prism driver is currently.

As far as the rtl8180 and rtl818x cards, I know that the default driver (also compiled in the kernel as described above) gave some people problems, particularly with long downloads in the feisty kernel.  Gutsy's kernel is newer, but I dont know if the rtl kernel modules are newer.  By default in feisty the r8180 and r818x modules were blacklisted due to its unstable nature, however I know that the driver would work.  To make it work you had to set up the wireless connection manually via the command line/network manager manual installation/manual editing of the /etc/network/interfaces file.  One of the bugs with the driver was that you had to add a fake character to the essid name.  Hence if you were trying to connect to essid=linksys, you would have to configure your setup to connnect to linksysx.  Again I havent gotten any feed back from anyone in Gutsy about these workarounds so its hard for me to say if they still work.

ndiswrapper will work with all these chipsets if you have the winxp drivers.  I know this is a patch workaround and not intended for this purpose (the native driver should work).

---

### Post by phillywize on 2007-11-18
> **kevdog said:**
> As far as the rtl8180 and rtl818x cards, I know that the default driver (also compiled in the kernel as described above) gave some people problems, particularly with long downloads in the feisty kernel.  Gutsy's kernel is newer, but I dont know if the rtl kernel modules are newer.  By default in feisty the r8180 and r818x modules were blacklisted due to its unstable nature, however I know that the driver would work.  To make it work you had to set up the wireless connection manually via the command line/network manager manual installation/manual editing of the /etc/network/interfaces file.  One of the bugs with the driver was that you had to add a fake character to the essid name.  Hence if you were trying to connect to essid=linksys, you would have to configure your setup to connnect to linksysx.  Again I havent gotten any feed back from anyone in Gutsy about these workarounds so its hard for me to say if they still work.

ndiswrapper will work with all these chipsets if you have the winxp drivers.  I know this is a patch workaround and not intended for this purpose (the native driver should work).

Thanks, Kevdog -- I am running Gutsy, and the RTL8187 support "worked" without any intervention from me during install/hw detection & configuration...that is, it worked to the extent I outlined before, which is to say, sometimes it just *stops* working for no apparent reason.  It doesn't seem to be related to long downloads, or really anything at all (that I've been able to identify).  No issues with essid's.  I may open a bug report on it (or look for one); if I find anything out, I'll post here.

It's always one thing or another...I just replaced my old windows system -- what kept me from going full-time Ubuntu there was an incurable video card compatibility issue.  With my new system, there's nothing of the sort.  Just this much less arcane RTL issue, which I can work around until a fix arrives (or I buy another wlan adapter).  Anyhow, windows has been confined to a virtual machine now, and so far so good...

---

### Post by kevdog on 2007-11-18
Again my advice for anyone thinking of going wireless with Ubuntu would be to get a pci based card -- not usb -- and an Atheros card that is compatible with the madwifi drivers.  These are the only drivers it seems that truly work out of the box.  I thought that was a fallacy until I obtained one of these cards for free, and I was amazed!!  I still use my Linksys Broadcom card on a regular basis (with ndiswrapper).  With both cards plugged in simaltaneously, the Broadcom gives twice the signal strength as the Atheros.  Im not sure if this is an accurate reading, a relative reading, or in fact a driver issue since both cards seems to work about the same subjectively.  I haven't done any objective testing.

---

### Post by exquest on 2007-11-18
I'm having trouble with my Broadcom BCM4309 internal 802.11a/b/g in that it works when I've installed the firmware with the restricted driver wizard but the connection speed is really slow.

I've also tried using my usb wireless card with the  rt73 driver using the nidiswrapper and it works fine for a while but tends to drop the conection every once and a while (about every hour).

---

### Post by kevdog on 2007-11-18
Seems like the 4309 chipset may be a new addition.  Directly from the bcm43xx official site:

supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
    * bcm4311 rev 1 / bcm4312
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * bcm4311 rev 2
    * There is no support for any Draft 802.11n features.

Although it would appear the b/g 4309 is supported Id default to ndiswrapper.  For your rt73 device, try the serial monkey drivers.  There is an awesome and very extensive post written by deprius on how to get this up and running: [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by jfank on 2007-11-19
I finally got my wireless network card to work on one of my laptops, but sadly on my other laptop it isn't working.  Funny enough I have the exact same wireless network card in both of my laptops.  Since I was able to figure out how to get the one card to work on Kubuntu I know how to get it working on the second one.  The second one I'm still running Kubuntu 6.10 on it, so i just need to get version 7.10 in it for it to run.  I honestly don't remember how I fixed the problem, but I think it was with some files I installed.  I hope everyone can get their wireless cards to work on their computers.

---

### Post by 67comet on 2007-11-23
I've got a notebook running the:  BCM4306 802.11b/g Wireless LAN Controller (rev 03)
and I've got a desktop running the: RaLink RT2561/RT61 802.11g PCI

Both seem fine, until you reboot. Then nothing comes back unless you hammer out: sudo /etc/init.d/networking restart then it's all golden again.

I've been racking my brain, the forums and IRC for help and so far nothing.

Anyone find a fix?
Cheers.

Ubuntu 7.10 on all.

---

### Post by wieman01 on 2007-11-24
> **67comet said:**
> I've got a notebook running the:  BCM4306 802.11b/g Wireless LAN Controller (rev 03)
and I've got a desktop running the: RaLink RT2561/RT61 802.11g PCI

Both seem fine, until you reboot. Then nothing comes back unless you hammer out: sudo /etc/init.d/networking restart then it's all golden again.

I've been racking my brain, the forums and IRC for help and so far nothing.

Anyone find a fix?
Cheers.

Ubuntu 7.10 on all.
That's a known bug... Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

_Create startup script:_
> sudo gedit /etc/init.d/wireless-network.sh
_Add this line & save file:_
> /etc/init.d/networking restart
_Change permission (executable):_
> sudo chmod +x wireless-network.sh
_Create symbolic link:_
> sudo ln -s /etc/init.d/wireless-network.sh /etc/rcS.d/**[COLOR="Red"]S40[/COLOR]**wireless-network

---

### Post by anonym0us on 2007-11-24
I have got two wireless card. One is built-in BCM4318 802.11b/g (rev 02), the other one is Linksys WPC54G connected through PCMCIA card of my laptop. 
I installed the firmware using the restricted driver manager. Somehow, Gutsy recognized both my wireless card as BCM4318, which is correct for one, but obviously not right for the other. 
Funny enough, my bCM4318 is not working at all, even though I have installed the firmware.
Linksys card on the other hand, could detect wireless networks, but could not connect. It just ask for password over and over again. I am not using router for the wifi network(another laptop acts as a server) and I am using static IP address.
Addition: iwlist scan show that linksys card has some results while my built-in card doesn't. Btw, I am a bit confused. My wireless cards are named eth1 and eth2 instead of wlan0 in the tutorials and other posts. Is that significant? I am new to this..

---

### Post by kevdog on 2007-11-24
Can you post

lshw -C network

And no the difference between eth1, eth2, wlan0 is meaningless.  Its just a name.

---

### Post by madsmaddad on 2007-11-24
It was working . I upgraded from Feisty to Gutsy and it was still working. I am trying to get my link encrypted, and it ain't working. 

It's there  iwlist scan gives:
peterm@peterm-Kdesktop:/etc/network$ iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


eth1      Scan completed :

          Cell 01 - Address: 00:18:6E:CA:89:2C

                    ESSID:"bmth_wireless"

                    Protocol:IEEE 802.11b

                    Mode:Master

                    Channel:11

                    Frequency:2.462 GHz (Channel 11)

                    Encryption key:on

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

                    Quality=100/100  Signal level=76/100

                    IE: IEEE 802.11i/WPA2 Version 1

                        Group Cipher : WEP-40

                        Pairwise Ciphers (1) : WEP-40

                        Authentication Suites (1) : PSK

                       Preauthentication Supported

                    Extra: Last beacon: 64ms ago

my Interfaces file shows: 
peterm@peterm-Kdesktop:/etc/network$ cat interfaces

auto lo

iface lo inet loopback

address 127.0.0.1

netmask 255.0.0.0



iface eth0 inet static

address 192.168.1.12

netmask 255.255.255.0

gateway 192.168.0.1


auto eth1

iface eth1 inet dhcp

wpa-driver wext

wpa-ssid bmth_wireless

wpa-ap-scan 2

wpa-proto WPA

wpa-pairwise TKIP

wpa-group TKIP

wpa-key-mgmt WPA-PSK

wpa-psk   13953c483e5d42339779f01317e83931b12e530f6ee5416144da6185a89b499e


I gave up using any of the Gui tools because they don't configure it correctly, so built the Interfaces file from the information given in the Quick'n'easy user guide  posting. 

Can someone have a look at it and see what I am missing in trying to sort it out. 

wpa_supplicant is loaded, but I took out the wpa_supplicant.conf file that I had created because of another forum entry. 

DMESG and IWconfig give:

DMESG:
 

[   40.968432] input: PC Speaker as /class/input/input2
[   41.163675] ieee80211_crypt: registered algorithm 'NULL'
[   41.171412] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   41.171420] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   41.369989] usb 4-3: reset high speed USB device using ehci_hcd and address 2
[   41.586988] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ
23
[   41.611965] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   41.614890] parport_pc 00:0a: reported by Plug and Play ACPI
[   41.614940] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.633353] zd1211rw 4-3:1.0: firmware version 4605
[   41.675314] zd1211rw 4-3:1.0: zd1211 chip 6891:a727 v4330 high 00-14-7c RF295
_RF pa0 g----
[   41.677880] zd1211rw 4-3:1.0: eth1
[   41.677904] usbcore: registered new interface driver zd1211rw
[   41.896706] NET: Registered protocol family 17
[   41.909498] intel8x0_measure_ac97_clock: measured 54862 usecs
[   41.909504] intel8x0: clocking to 48000
[   42.760383] lp0: using parport0 (interrupt-driven).
[   42.809139] Adding 4217020k swap on /dev/sda7.  Priority:-1 extents:1 across:
217020k
[   43.229838] EXT3 FS on sda6, internal journal
[   49.404760] No dock devices found.
[   49.419514] input: Power Button (FF) as /class/input/input4
[   49.419545] ACPI: Power Button (FF) [PWRF]
[   49.419627] input: Power Button (CM) as /class/input/input5
[   49.419650] ACPI: Power Button (CM) [PWRB]
[   50.795517] ppdev: user-space parallel port driver
[   50.929057] eth0: Media Link Off
[   50.931699] audit(1195895517.956:3):  type=1503 operation="inode_permission"                       requested_mask="a" denied_mask="a" name="/dev/tty" pid=4848 profile="/usr/sbin/c                      upsd"
[   50.998628] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   50.998635] apm: disabled - APM is not SMP safe.
[   52.247079] Failure registering capabilities with primary security module.
[   52.387783] Bluetooth: Core ver 2.11
[   52.388210] NET: Registered protocol family 31
[   52.388215] Bluetooth: HCI device and connection manager initialized
[   52.388221] Bluetooth: HCI socket layer initialized
   52.405598] Bluetooth: L2CAP ver 2.8
[   52.405606] Bluetooth: L2CAP socket layer initialized
[   52.437840] Bluetooth: RFCOMM socket layer initialized
[   52.437865] Bluetooth: RFCOMM TTY layer initialized
[   52.437870] Bluetooth: RFCOMM ver 1.8
[   83.980700] NET: Registered protocol family 10
[   83.981007] lo: Disabled Privacy Extensions
[   83.981261] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   83.981630] ADDRCONF(NETDEV_UP): eth1: link is not ready


peterm@peterm-Kdesktop:~$

peterm@peterm-Kdesktop:~$
-------------------------------------

peterm@peterm-Kdesktop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks,

---

### Post by anonym0us on 2007-11-24
this is what lshw -C network gives me: 
```

  *-network:0
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:51:42:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth2
       version: 02
       serial: 00:18:39:51:a7:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g


```
obviously eth2 should be my linksys wireless card.. i don't know why ubuntu is recognizing it as a broadcom wireless..

btw, my linksys wireless card is connecting through PCMCIA slot.
thanks

---

### Post by vmsda on 2007-11-24
I have Intel PRO/Wireless 2915ABG.

My Problem: whenever I shutdown/restart, the wireless connection never comes up.

Normal working configuration: using either System > Administration > Network or Manual Configuration from the network icon on Desktop, the card works perfectly when configured with WPA2 Personal (to match the router it is talking to).

Configuration after Shutdown/Restart: when I display it, some application (probably Network) has changed from WPA2 Personal to WPA personal ... and nothing budges.

Circumvention: I change the config back to WPA2 Personal and everything ok again ... until the next restart/shutdown.

This looks more like an application problem than a card/driver problem. Agree?

Thanks in advance for forthcoming tips.

---

### Post by neospartan on 2007-11-24
Intel PRO/Wireless 3945ABG 
driver=ipw3945
driver=e100
Ubuntu 7.10
WEP hexidecimal
Detects network but cannot connect. Still looking around other threads for a solution. I just installed ubuntu, and new to Linux, but am a quick learner, and I look around before I ask.

---

### Post by kevdog on 2007-11-24
Anonymous

Looks like both your cards have the same chipset!!  Almost all Linksys cards have the Broadcom chipset.


vmsda

Definitely a network manager problem -- not a driver problem -- or you couldnt get a connection.  If you can get a connection then its definitely not a driver problem.

---

### Post by kevdog on 2007-11-24
Neospartan

Try connecting from the command line with an unencrypted connection (no WEP, no WPA).  The instructions how to make a manual connection are in my signature.

---

### Post by odiseo77 on 2007-11-24
rt2500 here.

```
lspci -nn | grep Network
05:00.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
```

```
 sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=RT2500STA          
driver=e100
```

Gutsy's  default driver doesn't work fine 'out of the box'; doesn't support some iwpriv commands (when connecting by editing the '/etc/network/interfaces' file and '/etc/init.d/networking start'). I also experienced random disconnections when using the default driver and NM. So, I had to install the serialmonkey driver from Gutsy's repositories (rt2500-source package) and blacklist the rt2500pci kernel module in order to make my network work, but after that, it's working flawlessly (getting ready for a kernel upgrade that either solves the problem, or breaks my driver install (which wouldn't be a big problem for me since I already have all the necessary packages to compile the rt2500 driver)) :)

Regards.

---

### Post by anonym0us on 2007-11-25
> **kevdog said:**
> Anonymous

Looks like both your cards have the same chipset!!  Almost all Linksys cards have the Broadcom chipset.




Oh no.. how do I get the linksys card to work? It can detects wireless networks but cannot connect to the network. How do you connect to an Ad-Hoc network? One of the computer is acting as a hub and needs static IP address to connect to it. How about the wireless card driver? Is it the same?

---

### Post by kevdog on 2007-11-25
Not that there is anything wrong with the bcm43xx driver per se, but I prefer ndiswrapper b/c of its stability.

Please consult this guide - you have the 4306 chipset:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by Silvestre on 2007-11-25
i am using an atheros chipset (ath_pci) and i cant reconnect with internet. I must to restart the pc. Is any solution there? Card DWL-G650 from D-Link
Thanks

---

### Post by kevdog on 2007-11-25
When you network goes down or you lose the connection can you post:

lshw -C network
iwlist scan

I know for a fact you do not need to restart your computer to solve this problem.

---

### Post by Silvestre on 2007-11-26
Hello,

Thanks for the answer. The command lines show:

```

sergio@silvestre:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 10
       serial: 00:07:0d:43:4e:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:5b:4a:dd:9c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.11 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

and

```
sergio@silvestre:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:7F:BD:BA:1E
                    ESSID:"BTHomeHub-32AA"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101880003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:14:6C:4D:DC:71
                    ESSID:"SMART-HPI"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101000dff7f
          Cell 03 - Address: 00:11:F5:F2:AF:D8
                    ESSID:"BTVOYAGER2091-D8"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:0F:24:4B:3E:82
                    ESSID:"tmobile"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/70  Signal level=-94 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 05 - Address: 00:11:F5:CC:03:B9
                    ESSID:"BTVOYAGER2091-B9"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=2/70  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 06 - Address: 00:18:4D:FD:CE:1C
                    ESSID:"SKY91979"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-45 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101060003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f010100240000
          Cell 07 - Address: 00:0F:B5:B2:0C:5C
                    ESSID:"home-saver.co.uk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101060003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f010100350000
          Cell 08 - Address: 00:16:CF:0E:3E:8D
                    ESSID:"Livebox-B550"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-75 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 00:18:4D:B3:D1:40
                    ESSID:"Vodafone_At_Home"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd070050f202000100
          Cell 10 - Address: 00:19:7D:A0:1C:B1
                    ESSID:"Livebox-F9D0"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:14:85:C4:40:4D
                    ESSID:"beph"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK

```

[COLOR="Red"]**This situation is when internet is working**[/COLOR]

---

### Post by kevdog on 2007-11-26
Ok you are using the madwifi driver -- everything you posted looks kosher.  Can repost after you lose a connection?

---

### Post by Silvestre on 2007-11-26
at the moment i am not at my laptop but i could see that the ip-adress change from 192.168.2.11 to 40.19.0.16 and i dont know why (see last line of the first command line) and i can only say you that i am using CELL 2 from the second command line  ESSID= "SMART-HPI"

---

### Post by anonym0us on 2007-11-26
> **kevdog said:**
> Not that there is anything wrong with the bcm43xx driver per se, but I prefer ndiswrapper b/c of its stability.

Please consult this guide - you have the 4306 chipset:

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Thanks for the help. It is better right now although something is missing. My built-in wireless is disabled and I am using the linksys card to connect to the wireless network. The network icon on the top right shows the power percentages, which is better now since I didn't have that before. But I still have problems connecting with static IP address... I suspect it has something to do with WEP encryption that I use. Do I need additional packages for that? I am pretty sure that the key is using ASCII. 
Btw, I tried using wifi radar, but I do not have options to select WEP with ASCII or HEX 
Thanks again for the help. It has helped me a lot. This wireless issue has always been a pain since I first tried Ubuntu 5.10

---

### Post by sgrantham on 2007-11-26
Wireless connection appears to go correctly through the process of establishing a MAC connection, with the appropriate encryption, but fails (hangs) when attempting to get an IP address.

05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

driver=8139too            
driver=bcm43xx

 Note: On dapper I was successfully running wifi on this same PC with ndiswrapper.  When I upgraded to Feisty, this problem arose and I could not fix it.  When I upgraded to Gutsy, I switched from ndiswrapper to the native bcm43xx driver, but the problem still persists.  I'm guessing it has to do with the dhcp daemon.  I have tried both gnome network manager and wicd which both show the same symptoms.

---

### Post by kevdog on 2007-11-26
anonymous and sgrantham

Try connecting manually via the commandl line, since this process is bound to give more input about what the problem is.  I can't tell right now what is not working although I know you guys are having problems.  A link to the instructions are contained in my signature.

---

### Post by anonym0us on 2007-11-28
> **kevdog said:**
> anonymous and sgrantham

Try connecting manually via the commandl line, since this process is bound to give more input about what the problem is.  I can't tell right now what is not working although I know you guys are having problems.  A link to the instructions are contained in my signature.


I tried following your guide.. It says no DHCPOFFERS.
my commands:
sudo ifconfig eth2 down
sudo dhclient -r eth2
sudo ifconfig 192.168.0.16 netmask 255.255.255.0 up
sudo route add default gw 192.168.0.1
sudo iwconfig eth2 essid "MY_NETWORK_ESSID"
sudo iwconfig eth2 key s:MY_ENCRYPTION_KEY
sudo dhclient eth2

Is that correct? Should I changed my wireless to roaming mode before attempting to connect manually? Should I turn off eth1 first? I tried to open up /etc/network interfaces file and there is no information about eth2 after i tried to set it up manually..

---

### Post by Seikmann on 2007-11-28
```

seik@portable:~$ lspci -nn | grep Network
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)
seik@portable:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=iwl4965            
driver=r8169
seik@portable:~$ 

```

My problem is that I cannot connect to any wep encrypted w-lan. It works quite well on networks that is not encrypted.

---

### Post by kevdog on 2007-11-28
Take a look at my thread about connecting from the command line.  This isnt a long term solution by any means but it will either confirm or verify that you can not connect via WEP.

---

### Post by Mad Druid on 2007-11-28
Not sure if this is specific to wireless, but it happens when I switch between wired and wireless.  I can boot up with the wired connection off and the laptop sees the AP and connects.  Everything works fine except for some quick disconnects/reconnects.  The disconnects really only affect the VPN I run in an XP VM.  All of the Ubuntu stuff works seamlessly.  When I plug in the ethernet cable, network manager shows the wireless being cut off and the wired connection comes up.  No problem.  I disconnect the wired connection and network manager shows the connecting animation and never recovers.  My keyboard stops working.  I can't open any new apps.  I have to HARD reset the box.  I have not tried to ssh in when this happens yet.  

I can repeat this any time I want with the above procedure.  It's kind of a soft lockup. I can still switch between workplaces with the mouse.  I can close windows (compiz).  I can use the menus in the panel.  When I try to start a new app with the menus, the system clocks and nothing opens.

Here's my system.

lspci -nn |grep Network:
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4227] (rev 02)

lshw -C network |grep driver |sed 's/ '\n/g' |grep driver=
driver=ipw3945

The laptop is a Lenovo T61 with intel video, just in case that's relevant.

---

### Post by rjss90 on 2007-12-07
Hi Everyone:

Completely new to Ubuntu and Linux. I have tried to get the Broadcom BCM4318 on Dell Inspiron 2200 to work with no luck. So I have another clean install of gutsy for another crack at it.

Problem: I can't connect to the network using NDISWrapper or the BCM43xx driver. The best I have gotten so far is the prompt for the password over and over again.


1. Results of lspci -nn | grep Network

@linux-laptop:~$ lspci -nn | grep Network
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

2. Results of lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

driver=bcm43xx            
driver=e100

---

### Post by kevdog on 2007-12-09
rjss90

Id go for the ndiswrapper solution.  Check this post out:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

---

### Post by A + on 2007-12-13
Realtek 8139 chipset, Atheros AR5007EG wifi card.

```

 lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

 driver=8139too
```

I've gotten to the point where Network Manager sees a wireless connection and strong signal but doesn't connect to anything.  Can't ping anything, can't surf with browser.  Looks like other program controlling the connection maybe ... ?  the wired one ...? (I can use the internet perfectly with the wire connected to the router)

```
lspci -nn | grep
``` 

Returns nothing I can see

---

### Post by John Azelvandre on 2007-12-16
I updated to Gutsy last weekend and my problem is that the wireless support has vanished.  As I'm reading along through all these posts, I gather this has been a common occurence.  

Wireless worked adequately (I wouldn't say great) under Feisty.  Now it's just gone -- no wireless connection listed in the network manager.

Here's my code results:

```
zizonus@hedgewizard2:~$ lspci -nn | grep Network
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)

```

and:

```
zizonus@hedgewizard2:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=skge               
```

My wireless card driver should be 'ipw2200.'  It's not listed.  I gather 'skge' is the wired network connection, which is working just fine.  

I'm slogging through all the documentation on this problem, but if anyone can point me in the right direction, it would be helpful ... thanks.

---

### Post by kevdog on 2007-12-16
John,

look in dmesg to see why the ipw2200 module isnt loading at startup.  I believe this module is contained in the vanilla kernel by default, so I think it should be at least trying to load, but is running into some problems.  

I bet the full output of lshw -C network probably shows the wireless device as UNCLAIMED, meaning the module hasnt loaded and "claimed" the device.

---

### Post by John Azelvandre on 2007-12-16
Thanks, Kevdog:

You're absolutely right 'lshw -C network' shows my wireless card as UNCLAIMED.

Here is a snippet of the output of dmesg that looked pertinent:

```
[   16.768000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.768000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.768000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 22 (level, low) -> IRQ 21
[   16.768000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   17.120000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   17.120000] ipw2200: Unable to load firmware: -2
[   17.120000] ipw2200: failed to register network device
[   17.120000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[   17.120000] ipw2200: probe of 0000:03:03.0 failed with error -5

```

What does this mean?  As I mentioned before, it was working on Feisty a week ago.

---

### Post by kevdog on 2007-12-16
You would have to do a search on google to find the meaning of those errors exactly.  Thats a tuff one.

Now that the boot process is completed, what if you type:

sudo modprobe ipw2200

Do you get errors now?

---

### Post by phekdra on 2007-12-17
05:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

Works fine for a while, frequently a long while, then stalls requiring a networking restart. Saturday morning required four or five restarts in the space of ten minutes. What's most frustrating is that I know that this problem is fixed in recent rt2x00 drivers and they will be included in kernel 2.6.24, but the Ubuntu versions are far from recent.

Whinge, moan... :neutral:

---

### Post by Edho on 2007-12-17
Gutsy + Intel 3945 ipw.

Works very good with WEP and "roaming mode".

WPA seems a problem.

---

### Post by lswest on 2007-12-17
I had a couple of problems with my broadcom (4311) card, but a quick ndiswrappering of the bcmwl5 drivers solved the problem (no, the firmware in Ubuntu does NOT work with that chipset, even though it should.  at least...it didnt work for me).  At the moment my ethernet card (some nondescript nvidia nforce ethernet card, HP support doesn't give my much info about the card) is the major problem.  It connects fine, but at every boot it gets allocated a new alias (i think at the moment it is at eth116 XD) and when it does connect to the wireless it disconnects randomly (unstable connection).  However, im not that prone to using ethernet cables with my laptop, so it hasnt bothered me much.  Just thought i'd throw it out here :P

---

### Post by kevdog on 2007-12-17
For any ra based cards, you would be better off compiling and using the serial monkey drivers.  Just an FYI.

---

### Post by phekdra on 2007-12-17
> **kevdog said:**
> For any ra based cards, you would be better off compiling and using the serial monkey drivers.  Just an FYI.

As far as I'm aware the cvs serialmonkey rt2x00 drivers require kernel 2.6.23. Although I'd be very happy to be proved wrong! From my experience the serialmonkey modified Ralink rt61 open source drivers have just as many hangups and stalls as the present rt2x00 drivers.

I did try ndiswrapper and it's locked up my machine twice in a couple of hours, adding to the conspiracy to keep me from spending too much time online. :)

---

### Post by kevdog on 2007-12-17
The rt2x00 drivers are experimental -- Ive only known one person Austin_KW to get them to work -- and he stated the performance was iffy.  This was in Feisty, so I dont know if things have improved.

As far as the serial monkey drivers, I'm referring to the serial monkey rt61 drivers.  These are different than those that ship with Ubuntu the rt61pci drivers.  

There is always ndiswrapper as a last resort, however I prefer people to use a native Linux driver whenever possible.

---

### Post by odiseo77 on 2007-12-17
@phekdra: I'm not using a rt61 card but a rt2500 one, but have you tried using the rt61 driver from the [serialmonkey site]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")? (either the beta driver or the cvs tarball; the cvs version is probably better).

---

### Post by phekdra on 2007-12-17
> **odiseo77 said:**
> @phekdra: I'm not using a rt61 card but a rt2500 one, but have you tried using the rt61 driver from the [serialmonkey site]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads")? (either the beta driver or the cvs tarball; the cvs version is probably better).

I initially used this with Gentoo Linux when I first got my wireless card and found it somewhat unreliable in that it kept dropping the connection. This prompted me to try the rt2x00 driver, which at the time required patching the kernel (actually copying the rt2x00 - eeprom - mac80211 code directly into to kernel tree). Much to my surprise it worked perfectly with not a single dropped connection in all the time I was using it. Now I'm with ubuntu with an older version of the rt2x00 driver and haven't yet worked up the courage to patch the kernel while everything else is working so well! :p

Since kernel 2.6.24 should be out soon (fingers crossed), and the rt2x00 drivers are included, I'll probably wait and build my own kernel package as described here:

[http://ubuntuforums.org/showthread.php?t=311158]("http://ubuntuforums.org/showthread.php?t=311158")

Phekdra

---

### Post by John Azelvandre on 2007-12-17
> **kevdog said:**
> You would have to do a search on google to find the meaning of those errors exactly.  Thats a tuff one.

Now that the boot process is completed, what if you type:

sudo modprobe ipw2200

Do you get errors now?

Haven't had a chance to research this problem further yet.

sudo modprobe ipw2200 appears to do nothing.  No errors, but also no output or change.  The card remains 'unclaimed.'

---

### Post by kevdog on 2007-12-17
If you do the sudo modprobe statement -- do you get any additional errors in dmesg?


Wow -- patching the kernel -- that was great, but a pain in the a$$.  A lot of people in this forum have reported success with the rt61 serial monkey driver -- sorry it didnt work for you.  There is always ndiswrapper, and other people have reported a lot of success with this approach.  If you ever do patch your kernel again, please post a how to.  Perhaps PM Austin_KW since he has also used this approach.

---

### Post by GVaio on 2007-12-17
I am using Gutsy and a USB Airlink101 stick ("awll3026" driver) and static IP.  It works only when using _**NO**_ WEP encryption.  As soon as WEP is turned on I can not connect.  I know there's nothing wrong with this USB stick & my old Linksys BEFW11S4 router for two reasons: **a]** this Gutsy is a dual-boot desktop and under WinXP has no trouble at all; **b]** I have an old laptop running Dapper (a Sony Vaio that does not play well hibernating with Gutsy) and it also works with its built-in wireless.  

The LiveCD suggestion (first post in this thread: [http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)) did not help.  Also "ndiswrapper" on the HD installed Gutsy does not work either.

I am disappointed ... and considering a re-install back to Dapper for this dual-boot desktop, just to prove a point ...

Just for kicks: (from the LiveCD session)
```
$ lsusb | grep -i wifi
Bus 004 Device 002: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
$ sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
driver=e100

```

---

### Post by John Azelvandre on 2007-12-17
> **kevdog said:**
> If you do the sudo modprobe statement -- do you get any additional errors in dmesg?


No additional messages in dmesg.  It appears that nothing happens.  Ideas, anyone?

---

### Post by tiachopvutru on 2007-12-18
I have been getting constant disconnection. I'm connecting through manual connection way, through configuring /etc/network/interfaces 

Here's what inside of my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-essid XXXXXXX
wireless-key 8c6bXXXXXXXX open
wireless-mode managed
address 192.168.0.102
netmask 255.255.255.0
```

For some reason, I have to add the open behind the entry of wireless-key to connect, but that's beside the issue. A lot of time, and happens even more constantly when I use a bittorrent client to download something, I would get disconnected for no reason at all. At that time, the output of **iwconfig** still show itself being connected, while the command **iwlist scan**, under wlan0, gives me a *No Scan Results* message. At that point in time, I'd have to restart, and then after I log in, do a **sudo dhclient wlan0** to actually boot back again. **sudo dhclient wlan0** or **sudo /etc/init.d/networking restart** don't work unless I restart. It doesn't really happen very often if I don't use bittorrent, but still get to the point of annoyance, and it really hinder my ability to download when I use bittorrent.

Anyway, here's the output of the command this thread requires:

```
chucuoi@chucuoi-desktop:~$ lspci -nn | grep Network
chucuoi@chucuoi-desktop:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=r8169              
driver=ndiswrapper+netwg11t

```

As you can see, the first command gives me no result. My wireless device is Netgear WG111T, but the second command's output does show that I'm using ndiswrapper.

---

### Post by kevdog on 2007-12-18
Sounds like you have a package issue, or conflicting packages that are installed.  Check dmesg and /var/sys/log to see if you find any useful information.  

This might be a really hard problem to track down.  Try disabling IPv6.  Also try booting to an older kernel version and see if this helps.  Sometimes newer kernels break with different hardware (dont ask me why!)

---

### Post by tiachopvutru on 2007-12-18
> **kevdog said:**
> Sounds like you have a package issue, or conflicting packages that are installed.  Check dmesg and /var/sys/log to see if you find any useful information.  

This might be a really hard problem to track down.  Try disabling IPv6.  Also try booting to an older kernel version and see if this helps.  Sometimes newer kernels break with different hardware (dont ask me why!)

The command **dmesg** ends up giving too long of an output so I'm not going to paste it here, but at the end of it, it does shows that there's something about IPv6:

```
[  199.359322] wlan0: no IPv6 routers present
```

I don't know how to disable IPv6, nor what it is in the first place anyway. Anyway, I don't think I have the var/sys/log. There are /var/log/syslog and /var/log/syslog.0 though.

---

### Post by kevdog on 2007-12-18
Sorry, I meant /var/log/syslog.  You were correct.  

Here are instructions for IPv6 -- use the global inactivation method:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

Here is a link about various logfiles:
[https://help.ubuntu.com/community/LinuxLogFiles#head-90a79f52ee3f6d766a16e1ee67f98267e009db55](https://help.ubuntu.com/community/LinuxLogFiles#head-90a79f52ee3f6d766a16e1ee67f98267e009db55)

---

### Post by tiachopvutru on 2007-12-18
The /var/log/syslog is too long so I'm unable to post output of the whole log as my terminal knowledge is very limited.

```
00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.986059] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.986328] scsi0 : ata_piix
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.986427] scsi1 : ata_piix
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.986566] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.986568] ata2: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.988368] USB Universal Host Controller Interface driver v3.0
Dec 18 01:34:46 chucuoi-desktop kernel: [   43.999041] FDC 0 is a post-1991 82077
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167163] ata1.00: Host Protected Area detected:
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167164] ^Icurrent size: 625140335 sectors
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167165] ^Inative size: 625142448 sectors
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167357] ata1.00: native size increased to 625142448 sectors
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167362] ata1.00: ATA-8: WDC WD3200AAKS-00VYA0, 12.01B02, max UDMA/133
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.167364] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.183992] ata1.00: configured for UDMA/133
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.658271] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB01, max UDMA/100
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.829922] ata2.00: configured for UDMA/100
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.829994] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 12.0 PQ: 0 ANSI: 5
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830843] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB01 PQ: 0 ANSI: 5
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830886] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830903] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830923] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830950] scsi2 : ata_piix
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.830979] scsi3 : ata_piix
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.831053] ata3: SATA max UDMA/133 cmd 0x0001e700 ctl 0x0001e802 bmdma 0x0001eb00 irq 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   44.831056] ata4: SATA max UDMA/133 cmd 0x0001e900 ctl 0x0001ea02 bmdma 0x0001eb08 irq 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.159673] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.159679] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.159682] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.160596] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.160619] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.160845] usb usb1: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.160940] hub 1-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.160945] hub 1-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164923] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164931] sd 0:0:0:0: [sda] Write Protect is off
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164932] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164942] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164969] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164975] sd 0:0:0:0: [sda] Write Protect is off
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164977] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164986] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.164988]  sda: sda1 < sda5 > sda2 sda3
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.174132] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.176897] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.176909] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.186325] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.186328] Uniform CD-ROM driver Revision: 3.20
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.186353] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.260979] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.260987] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.260991] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.261007] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.261030] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e200
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.261097] usb usb2: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.261116] hub 2-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.261120] hub 2-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364775] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364783] PCI: Setting latency timer of device 0000:00:1a.2 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364786] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364802] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364824] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e000
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364895] usb usb3: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364914] hub 3-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.364918] hub 3-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.407468] Attempting manual resume
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.407470] swsusp: Resume From Partition 8:5
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.407471] PM: Checking swsusp image.
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.407624] PM: Resume from disk failed.
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.427895] kjournald starting.  Commit interval 5 seconds
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.427899] EXT3-fs: mounted filesystem with ordered data mode.
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468583] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468591] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468594] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468611] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468635] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e300
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468704] usb usb4: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468723] hub 4-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.468727] hub 4-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572351] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572358] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572361] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572376] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572396] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572461] usb usb5: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572480] hub 5-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.572484] hub 5-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676149] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676155] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676158] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676174] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676193] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e500
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676260] usb usb6: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676278] hub 6-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.676282] hub 6-0:1.0: 2 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.708032] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780017] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780026] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780029] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780044] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780067] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.780071] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfa004000
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.823815] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.823878] usb usb7: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.823897] hub 7-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.823901] hub 7-0:1.0: 6 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927656] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927664] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927667] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927684] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927705] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.927710] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfa005000
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.931577] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.931625] usb usb8: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.931641] hub 8-0:1.0: USB hub found
Dec 18 01:34:46 chucuoi-desktop kernel: [   45.931645] hub 8-0:1.0: 6 ports detected
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035529] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035556] PCI: Setting latency timer of device 0000:03:00.0 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035587] scsi4 : pata_jmicron
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035618] scsi5 : pata_jmicron
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035689] ata5: PATA max UDMA/100 cmd 0x0001c000 ctl 0x0001c102 bmdma 0x0001c400 irq 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.035692] ata6: PATA max UDMA/100 cmd 0x0001c200 ctl 0x0001c302 bmdma 0x0001c408 irq 17
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.230995] usb 3-1: device not accepting address 2, error -71
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.662145] usb 7-5: new high speed USB device using ehci_hcd and address 2
Dec 18 01:34:46 chucuoi-desktop kernel: [   46.797420] usb 7-5: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   47.041392] usb 7-6: new high speed USB device using ehci_hcd and address 3
Dec 18 01:34:46 chucuoi-desktop kernel: [   47.174053] usb 7-6: configuration #1 chosen from 1 choice
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.488371] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.489538] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.581503] Linux agpgart interface v0.102 (c) Dave Jones
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.645932] input: PC Speaker as /class/input/input2
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.791451] parport_pc 00:08: reported by Plug and Play ACPI
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.791492] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.835385] usbcore: registered new interface driver libusual
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.851422] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.851425] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.889687] Initializing USB Mass Storage driver...
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.891143] scsi6 : SCSI emulation for USB Mass Storage devices
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.891181] usb-storage: device found at 2
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.891183] usb-storage: waiting for device to settle before scanning
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.891189] usbcore: registered new interface driver usb-storage
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.891191] USB Mass Storage support registered.
Dec 18 01:34:46 chucuoi-desktop kernel: [   49.927769] nvidia: module license 'NVIDIA' taints kernel.
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.177694] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.177701] PCI: Setting latency timer of device 0000:01:00.0 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.177766] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.262312] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.262326] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.744226] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.886465] lp0: using parport0 (interrupt-driven).
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.909265] it87: Found IT8718F chip at 0x290, revision 4
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.909272] it87: in3 is VCC (+5V)
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.922676] coretemp coretemp.0: Using undocumented features, absolute temperature might be wrong!
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.922702] coretemp coretemp.1: Using undocumented features, absolute temperature might be wrong!
Dec 18 01:34:46 chucuoi-desktop kernel: [   50.953123] Adding 3903724k swap on /dev/sda5.  Priority:-1 extents:1 across:3903724k
Dec 18 01:34:46 chucuoi-desktop kernel: [   51.196791] EXT3 FS on sda2, internal journal
Dec 18 01:34:46 chucuoi-desktop kernel: [   51.702481] kjournald starting.  Commit interval 5 seconds
Dec 18 01:34:46 chucuoi-desktop kernel: [   51.702759] EXT3 FS on sda3, internal journal
Dec 18 01:34:46 chucuoi-desktop kernel: [   51.702763] EXT3-fs: mounted filesystem with ordered data mode.
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.066422] ndiswrapper version 1.49 loaded (smp=yes, preempt=no)
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.211150] usb 7-6: reset high speed USB device using ehci_hcd and address 3
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.347992] ndiswrapper: driver netwg11t (NETGEAR,01/07/2005,1.0.1.1007) loaded
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.658330] wlan0: ethernet device 00:14:6c:5c:5c:84 using NDIS driver: netwg11t, version: 0x10000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4250.F.conf
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.658341] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
Dec 18 01:34:46 chucuoi-desktop kernel: [   52.658355] usbcore: registered new interface driver ndiswrapper
Dec 18 01:34:46 chucuoi-desktop kernel: [   53.163590] No dock devices found.
Dec 18 01:34:46 chucuoi-desktop kernel: [   53.177023] input: Power Button (FF) as /class/input/input4
Dec 18 01:34:46 chucuoi-desktop kernel: [   53.177116] ACPI: Power Button (FF) [PWRF]
Dec 18 01:34:46 chucuoi-desktop kernel: [   53.177718] input: Power Button (CM) as /class/input/input5
Dec 18 01:34:46 chucuoi-desktop kernel: [   53.177811] ACPI: Power Button (CM) [PWRB]
Dec 18 01:34:47 chucuoi-desktop kernel: [   53.985435] ppdev: user-space parallel port driver
Dec 18 01:34:47 chucuoi-desktop kernel: [   54.078236] audit(1197959687.192:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5067 profile="/usr/sbin/cupsd"
Dec 18 01:34:47 chucuoi-desktop kernel: [   54.123471] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec 18 01:34:47 chucuoi-desktop kernel: [   54.123474] apm: disabled - APM is not SMP safe.
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.775604] Failure registering capabilities with primary security module.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Successfully dropped root privileges.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: avahi-daemon 0.6.20 starting up.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Successfully called chroot().
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Successfully dropped remaining capabilities.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: No service file found in /etc/avahi/services.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: New relevant interface wlan0.IPv4 for mDNS.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Network interface enumeration completed.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 18 01:34:48 chucuoi-desktop dhcdbd: Started up.
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.878438] usb-storage: device scan complete
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.879629] scsi 6:0:0:0: Direct-Access     WD       5000AAJS Externa 101a PQ: 0 ANSI: 4
Dec 18 01:34:48 chucuoi-desktop ntpdate[4428]: no servers can be used, exiting
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.889288] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.889785] sd 6:0:0:0: [sdb] Write Protect is off
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.889787] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.889789] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.891032] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.891532] sd 6:0:0:0: [sdb] Write Protect is off
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.891534] sd 6:0:0:0: [sdb] Mode Sense: 11 00 00 00
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.891536] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.891539]  sdb: sdb1
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.892075] sd 6:0:0:0: [sdb] Attached SCSI disk
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.892104] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec 18 01:34:48 chucuoi-desktop hcid[5361]: Bluetooth HCI daemon
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.974458] Bluetooth: Core ver 2.11
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.974540] NET: Registered protocol family 31
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.974542] Bluetooth: HCI device and connection manager initialized
Dec 18 01:34:48 chucuoi-desktop kernel: [   54.974544] Bluetooth: HCI socket layer initialized
Dec 18 01:34:48 chucuoi-desktop hcid[5361]: Starting SDP server
Dec 18 01:34:48 chucuoi-desktop kernel: [   55.006821] Bluetooth: L2CAP ver 2.8
Dec 18 01:34:48 chucuoi-desktop kernel: [   55.006823] Bluetooth: L2CAP socket layer initialized
Dec 18 01:34:48 chucuoi-desktop hcid[5361]: Created local server at unix:abstract=/var/run/dbus-UYeiIIgl84,guid=e7626b81e4a98c6f828bd10047676a08
Dec 18 01:34:48 chucuoi-desktop input[5391]: Bluetooth Input daemon
Dec 18 01:34:48 chucuoi-desktop input[5391]: Registered input manager path:/org/bluez/input
Dec 18 01:34:48 chucuoi-desktop audio[5395]: Bluetooth Audio daemon
Dec 18 01:34:48 chucuoi-desktop audio[5395]: Parsing /etc/bluetooth/audio.conf failed: No such file or directory
Dec 18 01:34:48 chucuoi-desktop audio[5395]: Unix socket created: 5
Dec 18 01:34:48 chucuoi-desktop kernel: [   55.048721] Bluetooth: RFCOMM socket layer initialized
Dec 18 01:34:48 chucuoi-desktop kernel: [   55.048798] Bluetooth: RFCOMM TTY layer initialized
Dec 18 01:34:48 chucuoi-desktop kernel: [   55.048800] Bluetooth: RFCOMM ver 1.8
Dec 18 01:34:48 chucuoi-desktop audio[5395]: add_service_record: got record id 0x10000
Dec 18 01:34:48 chucuoi-desktop audio[5395]: add_service_record: got record id 0x10001
Dec 18 01:34:48 chucuoi-desktop audio[5395]: Registered manager path:/org/bluez/audio
Dec 18 01:34:48 chucuoi-desktop avahi-daemon[5321]: Server startup complete. Host name is chucuoi-desktop.local. Local service cookie is 4289207719.
Dec 18 01:34:51 chucuoi-desktop anacron[5471]: Anacron 2.3 started on 2007-12-18
Dec 18 01:34:51 chucuoi-desktop anacron[5471]: Normal exit (0 jobs run)
Dec 18 01:34:51 chucuoi-desktop /usr/sbin/cron[5498]: (CRON) INFO (pidfile fd = 3)
Dec 18 01:34:51 chucuoi-desktop /usr/sbin/cron[5499]: (CRON) STARTUP (fork ok)
Dec 18 01:34:51 chucuoi-desktop /usr/sbin/cron[5499]: (CRON) INFO (Running @reboot jobs)
Dec 18 01:35:02 chucuoi-desktop ntfs-3g[5776]: Version 1.913 
Dec 18 01:35:02 chucuoi-desktop ntfs-3g[5776]: Mounted /dev/sdb1 (Read-Write, label "Storage", NTFS 3.1) 
Dec 18 01:35:02 chucuoi-desktop ntfs-3g[5776]: Cmdline options: rw,nosuid,nodev,locale=en_US.UTF-8 
Dec 18 01:35:02 chucuoi-desktop ntfs-3g[5776]: Mount options: noatime,rw,nosuid,nodev,silent,allow_other,nonempty,fsname=/dev/sdb1,blkdev,blksize=4096 
Dec 18 01:35:02 chucuoi-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Dec 18 01:35:04 chucuoi-desktop hcid[5361]: Default passkey agent (:1.18, /org/bluez/passkey) registered
Dec 18 01:35:04 chucuoi-desktop hcid[5361]: Default authorization agent (:1.18, /org/bluez/auth) registered
Dec 18 01:35:28 chucuoi-desktop modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: Withdrawing address record for 192.168.0.102 on wlan0.
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: New relevant interface wlan0.IPv4 for mDNS.
Dec 18 01:36:10 chucuoi-desktop avahi-daemon[5321]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Dec 18 01:36:10 chucuoi-desktop modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 18 01:36:10 chucuoi-desktop ntpdate[5994]: no servers can be used, exiting
Dec 18 01:36:17 chucuoi-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.5
Dec 18 01:36:17 chucuoi-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Dec 18 01:36:17 chucuoi-desktop dhclient: All rights reserved.
Dec 18 01:36:17 chucuoi-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 18 01:36:17 chucuoi-desktop dhclient: 
Dec 18 01:36:17 chucuoi-desktop avahi-daemon[5321]: Withdrawing address record for 192.168.0.102 on wlan0.
Dec 18 01:36:17 chucuoi-desktop avahi-daemon[5321]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Dec 18 01:36:17 chucuoi-desktop avahi-daemon[5321]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 18 01:36:18 chucuoi-desktop kernel: [  145.081322] NET: Registered protocol family 17
Dec 18 01:36:18 chucuoi-desktop dhclient: Listening on LPF/wlan0/00:14:6c:5c:5c:84
Dec 18 01:36:18 chucuoi-desktop dhclient: Sending on   LPF/wlan0/00:14:6c:5c:5c:84
Dec 18 01:36:18 chucuoi-desktop dhclient: Sending on   Socket/fallback
Dec 18 01:36:22 chucuoi-desktop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Dec 18 01:36:30 chucuoi-desktop dhclient: DHCPREQUEST on wlan0 to 255.255.255.255 port 67
Dec 18 01:36:30 chucuoi-desktop dhclient: DHCPACK from 192.168.0.1
Dec 18 01:36:30 chucuoi-desktop avahi-daemon[5321]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Dec 18 01:36:30 chucuoi-desktop avahi-daemon[5321]: New relevant interface wlan0.IPv4 for mDNS.
Dec 18 01:36:30 chucuoi-desktop avahi-daemon[5321]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Dec 18 01:36:30 chucuoi-desktop dhclient: bound to 192.168.0.102 -- renewal in 283317 seconds.
Dec 18 01:36:36 chucuoi-desktop modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 18 01:42:13 chucuoi-desktop modprobe: WARNING: Not loading blacklisted module ipv6 
```

I followed the instruction on the other thread and got IPv6 blacklisted, although I had to do another sudo ***/etc/init.d/networking restart*** + ***sudo dhclient wlan0*** after I rebooted.

EDIT:
Blacklisting IPv6 doesn't seem to solve the problem. I just had that issue happening again momentarily ago.

PS: I also notice that my bittorrent speed slows down after a while...

---

### Post by kevdog on 2007-12-18
Please filter any log messages before posting them.  Any log messages are only going to be useful if you check the log right after the disconnection.  

Has this always been a problem, or just recently after installing certain upgrades or software?

---

### Post by John Azelvandre on 2007-12-18
Just a little update on my problem, that I posted a few days ago:

After some google research, it appears I need firmware for this card, which I have tracked down on the Intel site.  Looks like I'll have to download it from there.  Unless it's on the synaptic repositories somewhere? I'm not home to try this out just now, but in the meantime, does anyone have any experience with Intel firmware installation?


> **John Azelvandre said:**
> Thanks, Kevdog:

You're absolutely right 'lshw -C network' shows my wireless card as UNCLAIMED.

Here is a snippet of the output of dmesg that looked pertinent:

```
[   16.768000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.768000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.768000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 22 (level, low) -> IRQ 21
[   16.768000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   17.120000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   17.120000] ipw2200: Unable to load firmware: -2
[   17.120000] ipw2200: failed to register network device
[   17.120000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
[   17.120000] ipw2200: probe of 0000:03:03.0 failed with error -5

```

What does this mean?  As I mentioned before, it was working on Feisty a week ago.

---

### Post by slikwill on 2007-12-18
This chipset works in 7.04.

slikwill@slikwill-laptop:~$ lspci -nn | grep Network
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
slikwill@slikwill-laptop:~$ sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
[sudo] password for slikwill:
driver=sis900             
driver=bcm43xx

I installed the .inf with ndiswrapper
slikwill@slikwill-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

Also, I did the following to install ndiswrapper
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9

I have fiesty/gutsy dual boot. Fiesty works, gutsy don't.
UPDATE... The solution was to install bcm43xx-fwcutter through Synaptic.

---

### Post by kevdog on 2007-12-18
John

never worked with intel firmware, I would suggest making a new post hoping someone with some knowledge will read it

Ndiswrapper + broadcom should be easy to get going.

---

### Post by John Azelvandre on 2007-12-18
> **kevdog said:**
> John

never worked with intel firmware, I would suggest making a new post hoping someone with some knowledge will read it

Ndiswrapper + broadcom should be easy to get going.

This is probably a stupid question, but I'll ask it anyway: What exactly IS ndiswrapper and why would I want it/need it?

---

### Post by gfd_2 on 2007-12-18
> **slikwill said:**
> This chipset works in 7.04.

slikwill@slikwill-laptop:~$ lspci -nn | grep Network
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
slikwill@slikwill-laptop:~$ sudo lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
[sudo] password for slikwill:
driver=sis900             
driver=bcm43xx

I installed the .inf with ndiswrapper
slikwill@slikwill-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

Also, I did the following to install ndiswrapper
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9

I have fiesty/gutsy dual boot. Fiesty works, gutsy don't.
UPDATE... The solution was to install bcm43xx-fwcutter through Synaptic.

quick question.... what type of system did you do this on?  AMD or Intel?    I ask because I'm having major issues getting this to work on an 64 bit HP dv6633us (Intel based system)

---

### Post by tiachopvutru on 2007-12-18
> **kevdog said:**
> Please filter any log messages before posting them.  Any log messages are only going to be useful if you check the log right after the disconnection.  

Has this always been a problem, or just recently after installing certain upgrades or software?

Well, I have only gotten this computer for a bit more than a week, but it had always been happening, even when I was using Network Manager to connect instead of the manual way.

As you instructed, I did a cat /var/log/syslog right away when I lost Internet connection again, and the only new line was:

```
Dec 18 16:59:03 chucuoi-desktop -- MARK --
```

---

### Post by charwhee on 2007-12-18
rt61

---

### Post by new2*buntu on 2007-12-18
My Intel Pro Wireless 3945 ABG worked out of the box. :)

---

### Post by DRK-AAM on 2007-12-18
Intel Corporation PRO/Wireless 2200BG Network Connection
driver=b44                
driver=ipw2200

Sometimes right after boot, or just randomly, for no reason, I lose the connection and if I try to check the available networks, the menu only displays "no network devices have been found" and the only option I have is to manually configure the network... 

The odd part is I can still reconnect wirelessly, but my system still doesn't recognize both my cards... (the second is an ethernet Broadcomm BCM4401-B0 100Base-TX, which is ALSO affected if connected by ethernet)

Hope that helps!

---

### Post by John Azelvandre on 2007-12-18
Just a follow-up on my series of posts to this topic on the missing firmware for ipw2200:  

I've discovered that ipw2200 and its firmware do not load properly with the i386 kernel.  

They work perfectly with the generic kernel.  I'm wireless, as I type right now - YAY!

So, the Gibbon through me a curve-ball: changed my kernel to i386 when I upgraded and made it default, and killed my wireless in the process.

If you're having problems like this -- check which kernel you're using first.

---

### Post by kevdog on 2007-12-18
How did you change your kernel??

Did you have another option in the grub menu or did you compile a vanilla kernel?

Good find by the way on this piece of information!!

---

### Post by John Azelvandre on 2007-12-18
Luckily I had the latest version of the generic kernel installed and listed in my grub menu.lst.  All that is left to do is edit the menu.lst to make the generic kernel the default.  I must have been using the generic kernel with Feisty; last week when I upgraded to Gutsy it must have slapped the i386 kernel in there.  But the old images were still in grub.

I don't imagine it would be that hard to obtain the generic kernel if you don't have: use synaptic to install the packages ... I think that will work ...

---

### Post by kevdog on 2007-12-18
Good find, maybe you should report a bug!!

---

### Post by jan quark on 2007-12-19
Running a Dell 1501 with Broadcom 4311.

My problem is rather annoying but not critical. After a few minutes Internet becomes really slow in Gutsy. Disabling ipv6 does not make a difference. I have read a lot but no how to really solved this.

---

### Post by Cybermax on 2007-12-19
Using :

Broadcom BCM4312 (Rev 02)

Hardware ID: 14E4-4312
Subsys ID: 103C-1371

DMESG error :

bcm43xx: Unsupported 80211 core revision 13
bcm43xx: Invalid PHY Revision 9
bcm43xx: FATAL ERROR: BCM43xx_IRQ_XMIT_ERROR
bcm43xx: MAC suspend failed

--
Works with ndiswrapper, but not with BCM43xx kernel module. Have not gotten a vanilla 2.6.24 kernel with b43 module to work either.

C

---

### Post by brandoncolorado on 2007-12-31
Hard freeze on RTL8185

---

### Post by avsa242 on 2008-01-02
bcm43xx *or* ndiswrapper with an internal miniPCIe 4311 rev 1:

For all practical purposes unusably slow throughput and high or unpredictable latency, with packet loss.
See this bug I've reported:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154647](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154647)
The summary of it is that there seems to be a strange conflict between the video and the wifi. Whenever in X, the connection is quite slow and problematically latent (or loses many packets). However, If I go to download something and switch to a VT, when I return it will have progressed quite far and the last reported speed is very normal by comparison.

This has plagued my mother's laptop since the beginning. It has driven me to incredible rage on several occasions trying to diagnose it.
I have resorted to using a Netgear WG111v1 USB 2.0 b/g adapter with ndiswrapper, which brings me to my other problem device:

The WG111 doesn't seem to work with the Prism54 drivers. When inserted, the p54u driver claims it and attempts to upload the firmware, but fails (IIRC, with error -22). According to the naming convention used by the different prism firmware files in /lib/firmware, the correct file should be isl3886 (I've cracked open the device; it does indeed have a 3886 in it). It seems to work fairly well with ndiswrapper, although so far it sometimes seems to erroneously choose to associate with the weaker of my two cells: the router in the basement instead of the repeater in the next room with the obviously stronger signal.
On a positive note *my* laptop with a 4318 miniPCI works fantastically with the new b43 driver in Hardy...vastly improved.

---

### Post by larseko on 2008-01-03
Card: Broadcom 4311 rev 1 mini-PCI.

Drivers, at least after following one of the mini guides here (no fluff): ndiswrapper+bcmwl5, tg3.

I have a (that is, 7) Dell Latitude D531 with 7.10. It appeared to work well, but then I was testing very close to the wireless router. At a little distance, it is very unstable, and have difficulties keeping the connection. This is where other computers normally show about 70% signal strenght. These will show about 30-50%.

So, I will maybe have to buy 7 new wireless adapters? This was really not what I was hoping for.

---

### Post by jeffus_il on 2008-01-03
Texas Instruments ACX 111 PCI
Network Manager does not work with it.
Need to manually configure.

---

### Post by andymushu on 2008-01-05
Consistently when i try to download something in firefox my connection stops. Network manager says my wireless is connected, but it completely stops downloading and i have to restart either the router or the computer for it to work again. "lshw -C network" lists no driver for my wireless connection, despite the fact that it works most of the time.

---

### Post by kevdog on 2008-01-05
lshw -C network only works for pci based devices, not usb wireless dongles.  Could you be using a USB device?

---

### Post by techgeek40 on 2008-01-08
I tried the command and nothing is showing up

I don't have the drivers installed for the PCMCIA socket adapter I"m using 

I have a NetGear 54 Mbps Wireless PC Card WG511 v2

---

### Post by kevdog on 2008-01-08
Hmm, if its not showing up with lshw -C network, then likely its a PCMCIA slot issue.

---

### Post by techgeek40 on 2008-01-09
Well, before I installed Linux on here - I had the card in and it was running fine. I don't think installing Linux blew out the port

---

### Post by rustybronco on 2008-01-09
> **jeffus_il said:**
> Texas Instruments ACX 111 PCI
Network Manager does not work with it.
Need to manually configure.I know it's not much help.
[http://ubuntuhcl.org/pub/reviews.php?product_id=408](http://ubuntuhcl.org/pub/reviews.php?product_id=408)
works for me with network manager in 7.04, 7.10 and 7.04 with a 2.6.24 kernel.
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230040888B20](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230040888B20)

---

### Post by Drakx on 2008-01-09
drakx@ubuntuLaptop:~$ lspci -nn | grep Network
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
07:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)
drakx@ubuntuLaptop:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=ipw3945            
driver=e100
drakx@ubuntuLaptop:~$

---

### Post by killasooty on 2008-01-10
I am using a Belkin F5D6050 on and AMD Duron system with Kubuntu Gutsy installed - & I get two problems with this combination  


1) If i attempt to use dhcp to assign my address it will hang my system up - symptoms are
Desktop stops responding to keyboard or mouse movement, & Caps Lock & Scroll Lock LEDs flash together. 

Disk activity normally ceases entirely, but the wireless adapter will often flash away merrily.  Rebooting by power cycling is the only way I've found to recover from this 'hanging' state     :confused:

2) The only way I can connected is to set up a static IP address - this will work, but often I have to go into KNetworkManager several times, entering the same data before it all 'sticks' - eg I might have to add the default gateway address, or dns addresses 2 or 3 times before the network gives up & starts working. This may be a KDE problem rather then wireless problem

```

sooty@uvavu:~$ lspci -nn | grep Network
sooty@uvavu:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=at76_usb
sooty@uvavu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=8.101.5-84 ip=192.168.2.40 wireless=IEEE 802.11b


```

---

### Post by kevdog on 2008-01-10
killasooty

try connecting from the command line to an unencrypted network for testing purposes.  The instructions are in my signature.

---

### Post by attpap on 2008-01-13
I'm experiencing random unpredictable disconnections.

02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

 driver=hostap

---

### Post by TRANQU111TY on 2008-01-17
```
03:05.0 Network controller [0280]: RaLink RT2561/RT61 rev B 802.11g [1814:0302]

```

Disconnects under load, jumpy/unstable speeds (from 164kB/s to less than 1kB/s).

---

### Post by kevdog on 2008-01-17
Tranq

You got a few options

The built in rt61 drivers in gutsy are not great.  Other driver options available

#1. Compile the cvs serial monkey rt61 drivers -- There is a post by deprius that explains the process for rt73 -- the process is exactly similar except you are using rt61 rather than rt73
#2. Ndiswrapper + winxp drivers -- A lot of people have go this route with success
#3. Recently contributed by RustyBronco - upgrade your kernel to Hardys developing kernel (this how-to is in the tutorial and tips section), and try to use the rt2x00 driver.

Thats about all I can say as far as advice.

---

### Post by primate on 2008-01-19
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

driver=ipw3945            
driver=tg3

Wireless network appears to disconnect randomly.  Must re-boot by power cycling to re-establish connection.

---

### Post by rawirth on 2008-01-19
Cant tell you my card's chipset b/c gutsy freezes 10 seconds afer I insert my card. The card worked with  ndiswrapper and new driver in fawn but not gutsy.

---

### Post by carolinason on 2008-01-21
I have no connectivity problems using 7.04 kubuntu or xubuntu using ndiswrapper with chipset:
2:0c.0 Ethernet controller [0200]: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 03).

I cannot get an ip address from the router with dhclient in 7.10 k/xubuntu. The router is unsecured and open!

I've been working on it for over a day and yet to find why it fails to get an ip address. i've tried different versions of ndiswrapper and googled and ubuntu forumed it to no avail. 
wifi-radar sees the networks, but dhclient will not fetch an ip. dhclient tries the old ip address and still no connectivity. 

statically applying the ip/dns does not work either.

](*,)

---

### Post by bhavin66 on 2008-01-21
very slow, already disabled ipv6 , disabled in firefox too, disconnects randomly
using the firmware in restricted driver no ndiswrapper

lspci
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"DI-634M"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:E9:ED:B0:1A   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level=-50 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:152  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:ED:B0:1A
                    ESSID:"DI-634M"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-40 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 8ms ago

---

### Post by bhavin66 on 2008-01-21
very slow, already disabled ipv6 , disabled in firefox too, disconnects randomly
using the firmware in restricted driver no ndiswrapper
Compaq V2570NR
512 MB shared (384 usable , 128 display )

updated the BIOS to the latest available on support site.
power management does not work. Sleep or hibernate does not return back.

wired connection works fine.

lspci
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"DI-634M"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:E9:ED:B0:1A   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=63/100  Signal level=-50 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:152  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:ED:B0:1A
                    ESSID:"DI-634M"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=92/100  Signal level=-40 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 8ms ago

---

### Post by thefatmoop on 2008-01-21
bump

---

### Post by snailmail on 2008-01-21
> 05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 020
Network card
> driver=ipw3945            
driver=b44

Driver

After waking the computer up, the wireless no longer works, requires restart

---

### Post by regomodo on 2008-01-21
the rt61 pcmcia plays silly buggers in Ubuntu Gutsy as of updates last week. I gave it another chance but gave up on it. Back to Debian

---

### Post by frenkel on 2008-01-22
Freaking slow connection with rt2500 chipset. Only 50kb/s :|

---

### Post by zipperback on 2008-01-22
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


Works fine with the ndiswrapper under 32bit, does not work with the ndiswrapper correctly with 64bit.

I am running 32 bit ubuntu gutsy 7.10 and I am using wicd for network management.

WIth this configuration I am happy and it works for me and is stable.

I have an Acer Aspire 5050-3371 laptop.

- zipperback
:popcorn:

---

### Post by Annalisa on 2008-01-22
the same as bhavin66...
i've got a broadcom 4318 using ndiswrapper (latest one) and gutsy.
it seems to connect but it really doesn't..
these are my outputs:

annalisa@computer:~$ lspci -nn | grep Network
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
annalisa@computer:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=sis900             
driver=ndiswrapper+bcmwl5

if I do iwlist scan it give me my home-network 
i cannot ping my router and when I type 
sudo ifconfig eth1 down 
light is still bright, i must manually turn off.
i hope sb will help me!! :(

---

### Post by adam_benson on 2008-01-22
problem: no wireless servers detected.

card/driver: 04:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
driver=bcm43xx

thanks for your help

---

### Post by m.capurso on 2008-01-23
lspci done
The result is:
Advanced Micro Devices [AMD] Am 1771 MBW [Alchemy] (rev 04)

It is a PCIMCIA  IEEE802.11b card

---

### Post by grainbarcelona on 2008-01-23
ok, this is what I get from the terminal commands that you requested::
henk@ubuntu:~$ lspci -nn | grep Network
02:01.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
henk@ubuntu:~$ lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=
WARNING: you should run this program as super-user.
driver=rt2500pci          
driver=e100


My probelm?... :
- In the manual configuration of the network,  I've to manually connect - unconnect at least 3 times before I get some connection to the internet
- and then still, it is about as 3 times as slow then windows (I am on dual boot)

Any suggestion what I should do? Or just switch back to Windows? ( I am pretty desperate by now!)

---

### Post by kevdog on 2008-01-23
What version of Ubuntu are you using?

---

### Post by chaos315 on 2008-01-24
My network controller is an Intel PRO/Wireless 4965 AG or AGN

My network manager will only connect if I restart the computer with a LAN plugged in from my router. When I do that, it sees all the networks out there. If that connection is dropped for any reason, the computer will only see the connection that it had (my personal network) and will not connect to it. If I then plug in the LAN, it drops that one too and will not connect wirelessly unless I restart the process -- how weird is that?

---

### Post by tad1073 on 2008-01-24
My problem is getting connected, i have to try 3 or 4 times before my card will finally connect. there are 11 signals that are in my immidiate area, but am only able to connect to one, which is my network.

Before I repositioned my computer I was getting singnal strength between 10% and 20%, now it is between 25% and 30%.

```
00:02.0 Ethernet controller: Atheros Communications, Inc.
AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
driver=e100               
driver=ath_pci
```
and when I do```
lspci -nn | grep Network
``` I get nothing

---

### Post by tad1073 on 2008-01-25
I think I figured out what my problem was. My signal strength had something to do with me having a hard time connecting.

---

### Post by just-want-one-attachment on 2008-01-25
adapter -  shuttle pn15g

zydas usb -  and it is getting WORSE with time

in 6.06 with the zd1211 it would have troubles every week or two with locking up.

in 7.10 with the zd1211-rw the firmware almost never loads correctly (i have to un/replug my device 30+ times to make it work)  AND the connection to my AP fails almost every day.

---

### Post by SirYes on 2008-01-26
I have an ASUS A8V Deluxe Mainboard that comes with regular wireless PCI card.
This card uses the rt2500pci module and is detected as:
```
$ sudo lspci -v
00:0e.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
    Subsystem: ASUSTeK Computer Inc. WL-130g
    Flags: bus master, slow devsel, latency 64, IRQ 21
    Memory at fbb00000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2

```In both Feisty and Gutsy the card worked okay. However, in Hardy I have about 8 times slower connection than normal. So downloading updates at 30kB-40kB rate is definitely slower than the expected 240kB-250kB (I have a 1Mbps ADSL connection).

Note:
I've just finished downloading the updates in chrooted environment and during the process the kernel and dependent packages (headers, modules, etc.) have been upgraded. Alas, after reboot the connection is still slow.

The kernel:
```
$ uname -a
Linux zjawa 2.6.24-5-generic #1 SMP Thu Jan 24 19:45:21 UTC 2008 i686 GNU/Linux
```My router is the D-Link DWL-G730AP with the latest firmware available installed.

---

### Post by einstein on 2008-01-26
Had trouble getting wireless working on new install on Toshiba Satellite A200-25V with Atheros AR5007EG (lspci says it is AR5006EG).  Installation of wicd was pivotal to final success.  Once wireless installed and working, no problems.  My route to success is posted here - [http://ubuntuforums.org/showthread.php?t=678953](http://ubuntuforums.org/showthread.php?t=678953)

Regards,
          Dennis

---

### Post by walterhisownself on 2008-01-26
ran

lspci -nn | grep Network

but returned no results, just a prompt in bash.

ran

lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

returned

driver=e1000
driver=ath_pci

Under Hardware Information in Gnome I see:

82801 Mobile PCI Bridge
  AR5213 802.11abg NIC

Vendor: Atheros Communications, Inc.
Device: AR5212 802.11abg NIC

I can connect via wireless on occasion, but get this, not to my D-Link router in my home. The laptop using the wireless device listed above can connect to another, unsecured network easily. It seems to time out when I select my wireless network from the ESSID list displayed by left clicking on the Network Manager icon on the top panel in a Gnome session.
I don't even have any wireless security set up, and it can't connect. I know that I have things set up on the router because my other laptop, which doesn't use Atheros wireless NIC can easily connect to my wireless network. (It uses a Cisco Aironet Wireless 802.11b by AIRONET Wireless Communications.

Sure could use some helpful suggestions from anyone.

Thanks!

---

### Post by kevdog on 2008-01-27
sounds like a network manager problem, rather than a driver/chipset problem.  Try WICD.

---

### Post by TRANQU111TY on 2008-01-27
> **kevdog said:**
> Tranq

You got a few options

The built in rt61 drivers in gutsy are not great.  Other driver options available

#1. Compile the cvs serial monkey rt61 drivers -- There is a post by deprius that explains the process for rt73 -- the process is exactly similar except you are using rt61 rather than rt73
#2. Ndiswrapper + winxp drivers -- A lot of people have go this route with success
#3. Recently contributed by RustyBronco - upgrade your kernel to Hardys developing kernel (this how-to is in the tutorial and tips section), and try to use the rt2x00 driver.

Thats about all I can say as far as advice.

Thanks. I discovered 64Bit Ubuntu Gutsy was highly unstable and unbearable with wireless. Have switched to 32Bit using ndiswrapper and my internet is soaring like an eagle :)

---

### Post by kevdog on 2008-01-27
I havent heard either way, but just wondering if the serial monkey drivers work with 64bit.  I guess I could check on the serial monkey forum :).  Feedback from any user using an ra based chipset, serial monkey driver on a 64 bit install would be appreciated.

---

### Post by TRANQU111TY on 2008-01-28
> **kevdog said:**
> I havent heard either way, but just wondering if the serial monkey drivers work with 64bit.  I guess I could check on the serial monkey forum :).  Feedback from any user using an ra based chipset, serial monkey driver on a 64 bit install would be appreciated.

I tried using those drivers but the result was the same as the default ones that came with 64Bit - unbearable (frequent disconnections/problems connecting/very unstable speeds etc...). I'm sure if I used them in 32Bit I wouldn't have as many problems.

---

### Post by fosheezy05 on 2008-01-28
I'm running an Atheros Super A/G card (AR5006) with only one minor problem - it can't connect to my router using WPA2.  WPA, WEP and everything else works.  I'm running the 64 bit version of Gutsy - device manager lists the card as a AR5413.  The driver information is:
driver=b44                
driver=ath_pci

This card did not work properly with anything better than WEP previously in 7.04.

---

### Post by Modplanman on 2008-01-28
Using Ubuntu 64bit Gutsy, BCM4320 Broadcom chipset (a wireless USB adapter). Methinks the problems of this one should be infamous.

---

### Post by kevdog on 2008-01-28
Im thinking of starting another thread similar to this thread to actually discover any chipsets, drivers, etc that actually work with 64 bit Ubuntu.  It seems like lately everyone is struggling with 64 bit -- b/c I dont have a 64 bit install, I can't really add anything meaningful to the conversation!!

---

### Post by andrewb78 on 2008-01-30
I have a Zonet ZEW2500P, which is a USB device that comes up as ```
148f:2573 Ralink Technology, Corp.
``` in lsusb.  Plugging in the device causes a huge increase in system load to well over 20.  This is on the AMD64 port of the Gutsy distribution of Mythbuntu.

---

### Post by Annalisa on 2008-01-31
I have a problem with broadcom4318 in an Acer Aspire 3000....I think my problem is actually stupid! I have a network, I can see it but I can't connect...
Maybe is a problem of my router digicom michelangelo wave...I don't think is a driver problem, I use the bcm43xx-fwcutter and network manager.
iwlist is ok
ifconfig can see my chipset
iwconfig show the AP too!
but when I do 
annalisa@computer:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
annalisa@computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"wlan-ap"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:04:ED:53:F9:47   
          Bit Rate=24 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

annalisa@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:9C:D3:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:51938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39841 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48051005 (45.8 MB)  TX bytes:4629014 (4.4 MB)
          Interrupt:16 Base address:0x1800 

eth1      Link encap:Ethernet  HWaddr 00:0E:9B:C5:E6:D5  
          inet6 addr: fe80::20e:9bff:fec5:e6d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:17659 errors:0 dropped:11320 overruns:0 frame:0
          TX packets:10647 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6016473 (5.7 MB)  TX bytes:483138 (471.8 KB)
          Interrupt:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7681 (7.5 KB)  TX bytes:7681 (7.5 KB)

as you can see.
I cannot stay anymore I must go to live in Reggio Emilia where there is wireless everywhere and I must install wincocks!!!!!!!!!!!!!!!!!!!
I am desperate!!!
help me, it seems to be so close!
I looked for in each forum, howto, changing to dapper, then to edgy, then to gusty and returned to dapper..I don't know what I'm going to do!

---

### Post by silver-city-productions on 2008-02-01
rtl8185l -- r8180 driver from realtek and/or sourceforge go ok up to anything to do with getting on the network.  then polling from dhpc never resolves to an ip address.  attempting static addressing similar, but just never gets to the router.  Accidentally connected briefly to a neighbor's linksys router.  

Realtek has no XP 64-bit driver, just Vista, and ndiswrapper does not support.

shipped as no-name card in Gateway mt3422 laptop.  r8180 driver in latest kernel is flawed.  so far, running 64-bit system, but am going to try dropping back to 32-bit and seeing what happens with ndiswrapper and/o my usb dongler:

To complicate:  tried Trendnet tew-424ub, ndiswrapper crashes.  Suspected 32/64 bit ndiswrapper issue, tried uninstalling/reinstalling various versions, with no luck.

---

### Post by rtrdom on 2008-02-01
Using Intel PRO ipw2100 3b
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:04:23:68:95:8d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.0.102 
latency=128 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
jim@Bravo:~$
       unit connects to home network using D-link router, does not connect to Netgear Accesspoint

---

### Post by prohwer on 2008-02-02
Broadcom

---

### Post by RFGunslinger on 2008-02-02
Using Intel PRO/Wireless 4965AGN card with iwl4965 driver and networkmanager 0.6.5

Works great at home, but tends to drop the connection at the office and won't re-acquire without reboot.  Some observations about droppage:

- Seems to happen more during the day than in the morning or evening (perhaps because more people are around increasing traffic through the access point during the day?)
- Always drops when on the move (switching access points)

Not sure if this is a driver issue or a networkmanager issue, but I thought I would share as I lack the requisite skills to get my hands dirty.

---

### Post by Vadi on 2008-02-02
realtek 8185

There are Linux drivers on the website but Ubuntu _completely_ (not even iwconfig) recognize the card.

Have to use ndiswrapper + windows drivers (net8185 driver).

---

### Post by wahr on 2008-02-02
Atheros (not sure which model, but the one in the first gen macbook - I understand there is a new OSS driver being developed for it?)

---

### Post by btrichardson on 2008-02-02
Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)

Can't even see available networks to connect to.  I can have my external Cisco (Atheros) PCMCIA inserted and when I click on the network icon in the top right of the screen, it lists both wireless cards, but no networks are listed under the Broadcom card and available networks will be listed under the Cisco card.

---

### Post by aaargh486 on 2008-02-04
I have a card that needs the RT2500 driver. I worked only sporadically in Gutsy, so I downloaded the good driver from their site ([http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)). I compiled it manually and that one worked perfect.

Kasper

---

### Post by rwmrwm on 2008-02-05
Linux version 2.6.22-14-generic using ndiswrapper for dlink wua1340 that would like a working rt73usb - from lsusb: ID 07d1:3c04 D-Link System .

Also a new Acer notebook has atheros  AR5007EG but waiting on madwifi to enable that...another ndiswrapper interim.

---

### Post by starsheeep on 2008-02-06
intel 3945abg with gutsy:
can't connect with wpa, if i try nm-applet will freeze after a while
nm-applet manual configuration takes 5' to load

tried ipw3946 and iwlwifi drivers
the manual configuration delay was corrected with the iwlwifi driver (guess it was the binary daemon causing it) but wap still freezes the nm-applet

solved: downgraded to edgy and installed wicd and wpa worked just fine
_haven't tried wicd with gutsy yet but will do_

---

### Post by kevdog on 2008-02-06
starsheep

Why dont you try WICD as an alternative to NM.  Others have reported success.

---

### Post by Rob V on 2008-02-06
RTL8185

Got it working briefly with the rtl8180 default (bundled on live cd) driver, but after trying a windows net8185 driver using ndiswrapper and wep enabled, it won't even boot :(

---

### Post by astro space zombie on 2008-02-10
I'm not sure what chipset it is, because every time I type 

> lspci -nn | grep Network

it doesn't do anything, but when I type the 

> lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=

It shows "SPCI" or something, and now it says driver= e100.

I'm so bad with Ubuntu, so some help please?

---

### Post by kevdog on 2008-02-10
Just post lspci -nn.  lspci is for listing pci devices.  If you are using a USB wireless device, then do a lsusb -v and look for the chipset here.

---

### Post by linuxgnuru on 2008-02-15
I have a 2wire pcmcia card, which I've used in the past with prism modules just fine (not under Ubuntu however) When I insert the card I get the following:

[ 1285.576000] eth1: uploading firmware...
[ 1285.640000] eth1: firmware version: 2.7.0.0
[ 1285.640000] eth1: firmware upload complete
[ 1285.816000] eth1: timeout waiting for mgmt response 250, triggering device
[ 1285.916000] eth1: timeout waiting for mgmt response 225, triggering device
[ 1286.016000] eth1: timeout waiting for mgmt response 200, triggering device
[ 1286.116000] eth1: timeout waiting for mgmt response 175, triggering device
[ 1286.216000] eth1: timeout waiting for mgmt response 150, triggering device
[ 1286.316000] eth1: timeout waiting for mgmt response 125, triggering device
[ 1286.416000] eth1: timeout waiting for mgmt response 100, triggering device
[ 1286.516000] eth1: timeout waiting for mgmt response 75, triggering device
[ 1286.616000] eth1: timeout waiting for mgmt response 50, triggering device
[ 1286.716000] eth1: timeout waiting for mgmt response 25, triggering device
[ 1286.716000] eth1: timeout waiting for mgmt response

[ 1286.716000] eth1: mgt_commit_list: failure. oid=ff020008 err=-110
[ 1289.716000] eth1: mgmt tx queue is still full

NOTE: the above 2 lines repeat 14 times with difering oid numbers)

[ 1289.716000] eth1: mgt_update_addr: failure
[ 1289.716000] eth1: mgt_commit: failure
[ 1289.716000] eth1: interface reset failure
[ 1289.716000] prism54: Your card/socket may be faulty, or IRQ line too busy :(

This device works just fine under windows, so am I missing something?

---

### Post by kevdog on 2008-02-15
Sounds like a module failure to me -- those prism cards -- I wouldn't wish those on my worst enemy!!

---

### Post by Melcar on 2008-02-15
Card is an Airlink AWLH3026T, which uses the RT2561 chip.  Card *works* fine, but it's incredibly slow (more like painfully slow).  Gutsy loads the rt61pci module.  The card can achieve much better speeds with ndiswrapper, but ndiswrapper causes my system to freeze when I engage in heavy network activity (weird :confused:).

---

### Post by kevdog on 2008-02-15
Melcar -- either upgrade to Hardy's developing kernel and use the rt2x00 module or stay with the gutsy kernel and use the serial monkey cvs modules.

---

### Post by Melcar on 2008-02-15
> **kevdog said:**
> Melcar -- either upgrade to Hardy's developing kernel and use the rt2x00 module or stay with the gutsy kernel and use the serial monkey cvs modules.

So compiling my own 2.6.24 (and the module) kernel should resolve this?

---

### Post by kevdog on 2008-02-15
You can compile if you want to -- its really run, a great learning exercise, however if you are anything like me, you will have to do it about 5-6 times to get what you want -- or you could just consult this thread:
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755).  Its not as fun, however it will get you there quicker and no compiling is required.  User rustybronco has reported success with this method with an rt61 card.

BTW - off topic -- 4000th post for me -- Wow -- what an utter waste of time!  Ok now back to the thread!!!

---

### Post by mungosr on 2008-02-16
Running an IBM A31 2652

```
02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

```

```
driver=hostap
```

Hardware version:
```
Host AP driver diagnostics information for 'wifi0'

NICID: id=0x8013 v1.0.0 (PRISM II (2.5) Mini-PCI (SST parallel flash))
PRIID: id=0x0015 v1.1.0
STAID: id=0x001f v1.4.2 (station firmware)

```


{RESOLVED}  

Reflashed - Having no issues now. 
```

[   22.364000] wifi0: NIC: id=0x8013 v1.0.0
[   22.364000] wifi0: PRI: id=0x15 v1.1.1
[   22.364000] wifi0: STA: id=0x1f v1.8.2
[   22.588000] wifi0: Intersil Prism2.5 PCI: mem=0xf8000000, irq=11

```

---

### Post by Melcar on 2008-02-16
Well, I tried the rt61 driver from serialmonkey.  Compiles, installs, and associates with the card, but I loose wlan0; it's simply not there anymore (in network manager, iwconfig, or in the network tools), even if lshw detects the card and the driver.  Compiling the rt2xxx package needs a new kernel, but the current 2.6.24 kernels seem to have issues with my hardware (therefore I also can't update to the Hardy kernel).  Really sucks.  Anybody know of another PCI card that doesn't use Ralink chips?  I also don't get why ndiswrapper freezes my system when I'm running a 64bit OS.

---

### Post by kevdog on 2008-02-16
Look for an atheros based card then -- these in my experience may be the easiest to fix.

I tried to make a thread asking people to report cards that worked on 64 bit Installs of Ubuntu, however this thread went no where:
[http://ubuntuforums.org/showthread.php?t=684128](http://ubuntuforums.org/showthread.php?t=684128)

---

### Post by weegie on 2008-02-19
Frequent wireless dropouts. Sometimes it reconnects automatically after short time but sometime " ifdown "followed by " ifup " is needed. 

Using Sitecom WL-012 usb adapter
driver=p80211_prism2_usb

---

### Post by rtrdom on 2008-02-20
lspci -nn | grep Network
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)

The problem is have is that the computer "sees" the Home network by clicking on the
manual network configuration icon. When I get to the library's open access point, I
have to reset the iwconfig several times, using your procedures. The most effective
way is to enable roaming and restart the computer. Then I change the ip address from
DHCP to static and then restart the computer. Whe it restarts, I remove the enable 
roaming, then select DHCP with the proper network name.  The I do the instructions
again and sometimes it "binds" after the final sudo dhclient eth1. Some times not.
When it does bind, and I return home, it automatically finds the personal "open" network and locks on. (My network is open because I'm rural and no one else is in
pickup distance.

---

### Post by Cilionelle on 2008-02-21
Hey.  I'm using an Atheros AR 5212 (apparently) and when typing in "lspci -nn | grep Network", got no response.  On typing "lshw -C network | grep driver | sed 's/ /\n/g' | grep driver=", I got this:

```
driver=ath_pci            
driver=e100 
```

Hope that helps!

---

### Post by bhenry on 2008-02-21
i'm not at my laptop right now, but it has an atheros ar5212 wireless card. for some reason, it works fine and connects, but it doesn't stay connected. after it disconnects, the only way to get it connected again is to restart.

---

### Post by silver-city-productions on 2008-02-22
regarding rtl8185 by realtek:  finally got it working on my gateway mt3422 laptop w/amd64 x2.  Had to run 32-bit os, blacklist r8180 driver, and use win98 drivers under ndiswrapper.

---

### Post by chrisinspace on 2008-02-23
My chipset:

```
RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] 
```

My driver:

```
rt2500pci
```

I have outlined my problem in another post.

[http://ubuntuforums.org/showthread.php?p=4384851#post4384851](http://ubuntuforums.org/showthread.php?p=4384851#post4384851)

Any help would be greatly appreciated.

---

### Post by xvedejas on 2008-03-11
lshw -C network

Yeilds:

```
*-network DISABLED
description: Wireless Interface
product: RT2561/RT61 802.11g PCI
vendor: RaLink
physical id: a
bus info: pci@0000:01:0a.0
logical name: wmaster0
version: 00
serial: 00:18:f8:a8:98:b2
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

Still can't get it working (see link in signature)

---

### Post by kevdog on 2008-03-12
ra chipsets --

You think since these are supported by the kernel they would cause the least problems -- however they top the poll for most problematic chipset -- seems like the developers have a way to go with this one!

---

### Post by xvedejas on 2008-03-12
Do you have any idea what I need to do? I've tried the serialmonkey drivers and ndiswrapper, neither have worked for me.

---

### Post by F D B on 2008-03-12
My Wireless adapter is D-Link Airplus G DWL - G510..... RT2561/RT61 rev B 802.11g
A full explanation of my problem can be found right here [http://ubuntuforums.org/showthread.php?t=719582](http://ubuntuforums.org/showthread.php?t=719582) 5 pages long of trial and error and no solution yet.

---

### Post by gianchi on 2008-03-12
This is what I get when I run the  lshw -C network | grep driver | sed 's/ /\n/g' | grep driver= command

driver=skge               
driver=ndiswrapper+netwpn11

I get nothing, running the other command.

Anyway, I have a WPN111, it has an Atheros chip, should be the 5523 model (it's the number in the driver name): of course I'm running it under ndiswrapper.

As for my problem, it's all in [this thread](http://ubuntuforums.org/showthread.php?t=722151) I posted this morning, that has been deserted.... if you could take a look at it, Kevdog, I'd be your slave for ever! :D

---

### Post by makkan77 on 2008-03-15
I'm using the prism54 chipset and I'm having trouble with high network loads and also not being able to go 54Mbit (only 22Mbit). 
Basically when I try to do a "sudo aptitude safe-upgrade" the whole system hangs during the download phase and I have to do a reboot to get back in. I have done a successfull upgrade thou so the problem seems quite erratic.

I have done quite alot of reinstallations the last weeks and I have never successfully done an update at the first couple of tries.

[B]
lspci:[/B]
01:00.0 Network controller [0280]: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] [10b7:6001] (rev 01)
[B]
lshw[/B]
driver=prism54pci

---

### Post by diilbert on 2008-03-15
I am using a Intel 4965AGN wireless chip on a Toshiba A205-S4607

```

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)

```

```

driver=sky2               
driver=iwl4965

```

Works only WICD (had to uninstall the default Network Manager).  Connects fine, works fine. EXCEPT it just drops the network somehow randomly and will not find any networks at all until I reboot.  Not sure what the problem is.  As well if the laptop sleeps for an extended period of time no networks show up in the network browser, again I need to reboot.

Hope there is some kind of solution for this problem. ;-)

---

### Post by hermitical on 2008-03-20
> **kevdog said:**
> 
To determine chipset, type at command line (or just cut and paste this code into the terminal):
```

lspci -nn | grep Network

```

right, I've been trying to get the wireless working on my new laptop for a few weeks off an on. Reintalled Ubuntu 7.10 a couple of days ago and I'm trying some [new instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a4de89718c16c9016a03c95196485224afc67de1"). Things is now I can't even get the lspci commands to work, I just get a flashing cursor and no info, I've checked that pci utilities are installed. I'm getting so very tired of all this!

---

### Post by kevdog on 2008-03-20
Is your wireless device a network card of a usb device connected the usb bus?

---

### Post by Jordanwb on 2008-04-03
I'm not sure how I would find out what Chipset I have but it's a Linksys WPC54G vers 7. I don't have major connectitivity problems other than my laptop is 3 feet from my router (+/- 6  inches) and strength is ~75%

---

### Post by kevdog on 2008-04-03
That signal strength is accurate.  Just to let you know.  The number is totally off.

---

### Post by bookgrampy on 2008-04-03
I have had intermittent problems with gutsy and a Trendnet TEW423PI wifi card. It never works right off after an initial boot. If I futz (a highly technical term meaning try this and that , change encryption and passcode, etc) with it, it connects but does not work. If I futz some more, it may suddenly start working and never drops out. Sometimes the only way to get it to start is (get this!), power cycle the router/wifi access point. Now I normally boot to 7.4.22 and on a hunch (another unscientific term meaning 'gut feeling') I opened grub and booted the older version, 7.4.20 (I think. It is hard to look that up in the middle of an message.) Well, lo and behold, it boots and works every time! I use ndiswrapper and the Win98/2000 version of the Windows driver, Marvell drivers come in several flavors.

My system responds with this to
 lspci | grep Marvell

00:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

I hope this helps someone else.

Bookgrampy

---

### Post by neddyfreddy on 2008-04-04
$ lspci -nn | grep Network
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG Network Connection [8086:4223] (rev 05)

----

driver=ipw2200

----

The problems I have having are intermittent loss of connection. The WNIC will simply "go offline" for a few and then come back in. Here are messages I see in my logs :

[ 4034.420000] ipw2200: Firmware error detected.  Restarting.
[ 4629.856000] ipw2200: Firmware error detected.  Restarting.
[ 5468.192000] ipw2200: Firmware error detected.  Restarting.
[ 6087.024000] ipw2200: Firmware error detected.  Restarting.

and also these (eth1 is my wnic) :

[   40.676000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   87.716000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  101.992000] eth1: no IPv6 routers present
[  255.932000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  256.884000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  266.952000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  279.672000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  294.764000] eth1: no IPv6 routers present
[  385.116000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3775.852000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3777.480000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3794.456000] eth1: no IPv6 routers present
[ 3800.448000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3810.468000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3812.800000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 3823.704000] eth1: no IPv6 routers present
[ 3835.504000] eth1: no IPv6 routers present
[ 7104.012000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7125.656000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 7129.720000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 7143.016000] eth1: no IPv6 routers present

---

### Post by Jordanwb on 2008-04-04
> **kevdog said:**
> That signal strength is accurate.  Just to let you know.  The number is totally off.

Lol that's funny. When I was setting up my wifi card the name of it was ath0 so that makes me think the chipset is Atheros

---

