---
title: "Can't get ndiswrapper to work on Atheros AR5BXB63"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by ruggrat on 2008-07-08
I've been reading through the forums trying to get some clarification, but nothing I have tried seems to be working.

New installation of Hardy on Acer Aspire 4720Z, sticker on the 
bottom says it has Atheros AR5BXB63.

"unsupported" (Atheros HAL) drivers didn't work out of the box, Tried installing ndiswrapper(1.9) through synaptic, wiped that, tried it with aptitude. Switched to Wicd, (which I used on a previous computer w/no problem), still nothing.  I've been trying to look up and down the various ndis tutorials for clues, but I just don't have the savvy...

When I install ndiswrapper, it behaves like everything is working, but there is absolutely no sign of wireless activity.

lshw -C network says this:
```
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:d4:68:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=192.168.1.3 latency=0 module=tg3 multicast=yes
```

What does it mean that the first device is "unclaimed"?
Also, why does neither the wired ethernet device nor the unclaimed wireless device have a logical name listed?
I would try madwifi, but I'm being told that it won't work on 64 bit system.  Should I try it anyway?

If anyone could give me some clues, I'd be very grateful!

---

### Post by acreech on 2008-08-06
I have not got my Atheros card to work on my Acer Aspire 7520-5185

> 
lshw -C network 


gives me this

> 
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


---

### Post by Lori700698 on 2008-08-06
I feel like a dork asking you this because you probably already tried it but just in case
 sudo modprobe ndiswrapper
if nothing try a rebooting the computer too!

if not you may have to put a madwifi driver in, I did and it works great but I'm have an issue with my security settings.

---

### Post by acreech on 2008-08-06
that does not seem to do a thing for me. I'lll keep searching the forums, however nothing so far seems to make it work. 

thanks for the suggestion

---

### Post by Lori700698 on 2008-08-06
Ok humor me for a minute, go to systems, admin, then see if wireless drivers is at the bottom of the list.  if it is click on it and see if it says yes, if not then we can download the tool and point to the .inf file.

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> Ok humor me for a minute, go to systems, admin, then see if wireless drivers is at the bottom of the list.  if it is click on it and see if it says yes, if not then we can download the tool and point to the .inf file.

there is just an empty box there, nothing that says yes. look at the attached screen shot. can you tell me how to 

> 
we can download the tool and point to the .inf file


---

### Post by Lori700698 on 2008-08-06
Bingo! this is the problem!  Where is the .inf file for your driver saved at, do you know?

---

### Post by acreech on 2008-08-06
no. Is there a way to find it? easily?

---

### Post by Lori700698 on 2008-08-06
you could look on your disks that came with the computer, you would be looking for drivers (wireless or AR#), I never had any luck with this!  If you do a search here or on the web you should be able to find the right driver and when you do save it right to your desk top, the whole folder (not just the .inf file)

---

### Post by Lori700698 on 2008-08-06
run this and look at the bottom it will show ar(and some number) get that number that's the actual driver we need to download.
lspci

The go here [http://www.atheros.cz/](http://www.atheros.cz/) and down load the windows version 32 or 64 that you need (the linux is for madwifi, which is not your goal at the moment)save the zip to your desktop then unzip it to the desktop. open the tool that was empty and load driver, point to that file, open and the .inf.  you will probably need to reboot and you should have ndiswrapper wireless.

---

### Post by acreech on 2008-08-06
> 
acreech@acreech-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


am I looking for a driver for AR242x?

---

### Post by Lori700698 on 2008-08-06
hit that link I gave you and download it to your desktop! unzip, point to the .inf file inside the folder and you should be good!

looks like there is two for that number try them both and see wich one give you a yes on that driver window.

---

### Post by acreech on 2008-08-06
I downloaded the file and then went to system>Admin>wireless drivers and installed the .inf file. I restarted the computer and it still does not seem to be working for me. 

In System>Admin>Hardware drivers there were two drivers for the wireless cards that had been check and showed in use. they are still checked however say not in use now. I have attached a couple screen shots of that so that you can see what it looks like. 

I appreciate your help with this. I am sure I am just not getting something right.

---

### Post by Lori700698 on 2008-08-06
It looks right, ndiswrapper is quirky. Try a
 sudo modprobe ndiswrapper 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
then reboot one more time.

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> It looks right, ndiswrapper is quirky. Try a
 sudo modprobe ndiswrapper 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
then reboot one more time.

I did that. Should this eventually show up in the Network Settings?

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> It looks right, ndiswrapper is quirky. Try a
 sudo modprobe ndiswrapper 
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
then reboot one more time.

it did not like the wlan0

> 
acreech@acreech-laptop:~$ sudo modprobe ndiswrapper 
[sudo] password for acreech: 
acreech@acreech-laptop:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
acreech@acreech-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
acreech@acreech-laptop:~$ 


---

### Post by Lori700698 on 2008-08-06
yea it will show as wireless and when you click on the double screens at the top it will show you your network. (can't remember if right or left click)  I can't tell you how many times I had this issue when I first started playing with Ubuntu.

That's ok just do the modprobe again and reboot.

---

### Post by acreech on 2008-08-06
ok. you got some more suggestions? this is the only thing that i have not liked about Ubuntu. It is my first experience with Linux really. 

when I did 
> 
 lshw -C network 


I did not see a location of my wireless.

> 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper


---

### Post by Lori700698 on 2008-08-06
yea go back to the check marks, uncheck and recheck them. and of course you will probably need to reboot (i hate that part)
and maybe remove one of the wireless drivers (they both look like good ones)

wait I don't think you need the ndiswrapper, it looks like you have the madwifi built in (uncheck and recheck the stuff and reboot)

Did you try installing madwifi? Just curious!

---

### Post by acreech on 2008-08-06
ok. unchecked and rechecked the things in hardware settings. I also only have one driver in the wireless drivers now. i have restarted the computer.

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> yea go back to the check marks, uncheck and recheck them. and of course you will probably need to reboot (i hate that part)
and maybe remove one of the wireless drivers (they both look like good ones)

wait I don't think you need the ndiswrapper, it looks like you have the madwifi built in (uncheck and recheck the stuff and reboot)

Did you try installing madwifi? Just curious!

no have not installed madwifi. 

sudo apt-get madwifi   ?

is that how you install it?

---

### Post by Lori700698 on 2008-08-06
I'm assuming that means still nothing!  Humor me again and do
modprobe ath_pci

I can help you with that next if this don't work!

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> I'm assuming that means still nothing!  Humor me again and do
modprobe ath_pci

this is what I get

> 
acreech@acreech-laptop:~$ modprobe ath_pci
WARNING: Error inserting ath_hal (/lib/modules/2.6.24-19-generic/volatile/ath_hal.ko): Operation not permitted
WARNING: Error inserting wlan (/lib/modules/2.6.24-19-generic/madwifi/wlan.ko): Operation not permitted
FATAL: Error inserting ath_pci (/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko): Operation not permitted
acreech@acreech-laptop:~$ 


---

### Post by Lori700698 on 2008-08-06
oops my fault
sudo modprobe ath_pci

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> oops my fault
sudo modprobe ath_pci

no response.


> 
acreech@acreech-laptop:~$ sudo modprobe ath_pci
[sudo] password for acreech: 
acreech@acreech-laptop:~$ 


---

### Post by Lori700698 on 2008-08-06
check and see if your system is seeing anything wireless!

---

### Post by acreech on 2008-08-06
under the network settings it just has the wired connection and then the point to point connection. No Wireless connection.

---

### Post by Lori700698 on 2008-08-06
what about the check marks, are they green or still red?

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> what about the check marks, are they green or still red?

The check marks are checked, but now say not in use (red)

---

### Post by Lori700698 on 2008-08-06
should be green if there is madwifi in there somewhere.  when you uncheck them and recheck them do they turn green? if they do, do the sudo modprobe ath_pci agian and see if that starts it up.

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> should be green if there is madwifi in there somewhere.  when you uncheck them and recheck them do they turn green? if they do, do the sudo modprobe ath_pci agian and see if that starts it up.

They turned green after using that command

---

### Post by Lori700698 on 2008-08-06
Ok forget ndiswrapper, sounds like you have to go with a madwifi kind of driver.  Still no wirless yet?  I had this same stiken trouble a few nights ago and got mad and put the ath5k driver in (the new madwifi) it's more automatic than the original madwifi.  let me give you the directions I followed.


[http://ubuntuforums.org/showthread.p...madwifi+driver](http://ubuntuforums.org/showthread.p...madwifi+driver)
and I skipped the 
gksudo gedit /etc/network/interfaces
I don't like messing with these unless absolutly necessary.
Now last thing I did different was use the new ath5k and you can use this link 
[http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6) 
in place of the ones in the first set of directions. And if you do you won't be going into trunk it will be 
cd madwifi, then cd madwifi.0.10.5.6
sudo make
sudo make install
sudo modprobe ath_pci
don't be suprised if it asks you to remove old stuff, just select the R and let it run.

---

### Post by acreech on 2008-08-06
I have 

linux-restricted-modules-2.6.24-19-generic

and 

madwifi-tools

installed on my system

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> Ok forget ndiswrapper, sounds like you have to go with a madwifi kind of driver.  Still no wirless yet?  I had this same stiken trouble a few nights ago and got mad and put the ath5k driver in (the new madwifi) it's more automatic than the original madwifi.  let me give you the directions I followed.


[http://ubuntuforums.org/showthread.p...madwifi+driver](http://ubuntuforums.org/showthread.p...madwifi+driver)
and I skipped the 
gksudo gedit /etc/network/interfaces
I don't like messing with these unless absolutly necessary.
Now last thing I did different was use the new ath5k and you can use this link 
[http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6) 
in place of the ones in the first set of directions. And if you do you won't be going into trunk it will be 
cd madwifi, then cd madwifi.0.10.5.6
sudo make
sudo make install
sudo modprobe ath_pci
don't be suprised if it asks you to remove old stuff, just select the R and let it run.


those links don't seem to connect to anything.

---

### Post by Lori700698 on 2008-08-06
Madwifi is there, getting it to run is not easy because it's not automatic. 
try the 
sudo ifconfig ath0 up

---

### Post by acreech on 2008-08-06
> **Lori700698 said:**
> Madwifi is there, getting it to run is not easy because it's not automatic. 
try the 
sudo ifconfig ath0 up

ok. 

> 
acreech@acreech-laptop:~$ sudo ifconfig ath0 up
[sudo] password for acreech: 
ath0: ERROR while getting interface flags: No such device
acreech@acreech-laptop:~$ 


---

### Post by Lori700698 on 2008-08-06
HOW TO: Dlink DWA-552 , DWA-556 and other Atheros chipsets with madwifi 
try this: [http://ubuntuforums.org/search.php?searchid=45836540](http://ubuntuforums.org/search.php?searchid=45836540)
is the name of the post I got directions from and the 2nd link I gave you doesn't realy go to a website, it goes in the code for the build.

---

### Post by acreech on 2008-08-06
ok. I will give it a try. Thanks.

---

### Post by Lori700698 on 2008-08-06
What the heck try this too and see if it stats your network up
sudo /etc/init.d/networking restart

Or simply remove network manager and download wicid, it works much better with the madwifi.
if you do
wlan0 is for ndiswrapper
ath0 is for madwifi
and you will need to turn all check marks green every time you boot to use madwifi/ath0.  
Either should work since you have ndiswrapper already loaded up, but it may be quirky.

---

### Post by acreech on 2008-08-07
> **Lori700698 said:**
> What the heck try this too and see if it stats your network up
sudo /etc/init.d/networking restart

That link to the other website did not do anything for me. 

That code sudo /etc/init.d/networking restart did not do anything either. 

that is about all the time I got for the night. Thanks for the help. I will give it a try again on a different day. 

thanks

---

### Post by Lori700698 on 2008-08-07
Or simply remove network manager and download wicid, it works much better with the madwifi.
if you do
wlan0 is for ndiswrapper
ath0 is for madwifi
and you will need to turn all check marks green every time you boot to use madwifi/ath0. 
Either should work since you have ndiswrapper already loaded up, but it may be quirky.

Cause I cant seem to link just search:
HOW TO: Dlink DWA-552 , DWA-556 and other Atheros chipsets with madwifi

---

### Post by Lori700698 on 2008-08-07
I thought about this last night and ubuntu is so different than windows, you cant just load everything up and it pick what works best so I had some ideas, at this rate who knows if having them both installed is causing some wacky issue.

1. uncheck both hal and the 802 drivers do
sudo modprobe ndiswrapper

if a no go try

2. check both of those again and remove the .inf off the windows driver and do
sudo modproe ath_pci

If either of these work we will need to look at making it go auto and removing the other...I've seen lots of posts on this!

---

### Post by loshdog on 2008-10-02
Hi I have an aspire one. Came with Limpus 9.2. I installed unbuntu. The wifi card is not working. 

I downloaded the xp drivers and tried to use the inf file from there both x64 & x86. 

Any suggestions. 

~Milosz

---

### Post by loshdog on 2008-10-05
I figured that since the unit was running linpus, ubuntu would work fine since they are both linux based. I'm new to linux overall. I guess there's something I'm missing. I tried all the various solutions here. To no avail. 

I also tried wrapping the correct xp driver as mention above. 

Does anyone have any suggestions? :confused:

PS. Is anyone even monitoring this thread. 


~ Milosz

---

### Post by acreech on 2008-12-03
> **loshdog said:**
> I figured that since the unit was running linpus, ubuntu would work fine since they are both linux based. I'm new to linux overall. I guess there's something I'm missing. I tried all the various solutions here. To no avail. 

I also tried wrapping the correct xp driver as mention above. 

Does anyone have any suggestions? :confused:

PS. Is anyone even monitoring this thread. 


~ Milosz

It looks like nobody is monitoring the thread anymore. I finally got my card to work. look at this other post to try for yours......

[http://ubuntuforums.org/showthread.php?p=6201697#post6201697]("http://ubuntuforums.org/showthread.php?p=6201697#post6201697")

---

