---
title: "[SOLVED] Internet Connection Dies under Heavy Load"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Brandel Valico on 2008-05-18
First my apologies if there is a bug report or this has all ready been posted. I have searched for several hours with various combinations to no avail.

I seem to have an odd issue. 

Under heavy bandwidth usage my connection to the internet just dies and doesn't come back until a reboot. Then it works fine again.

This generally occurs for example while downloading on Ktorrent or playing games like Guild Wars or any other heavy traffic programs. It's easy to repeat and happens every time.

I am Running Hardy with the latest updates a Linksys Gigabit ethernet card through a Linksys Gigabit Router. Via a cat6 wired connection. 

Anyone else having this issue or have an idea how to fix it?

---

### Post by chewearn on 2008-05-18
It's probably the linksys router, crashing under too many connetions.

[http://www.azureuswiki.com/index.php/Bad_routers](http://www.azureuswiki.com/index.php/Bad_routers)

---

### Post by Brandel Valico on 2008-05-18
Didn't see my Router on the list but will still look into the solutions they suggest. Hopefully one of them will work.

---

### Post by Brandel Valico on 2008-05-19
Oddly enough this only seems to effect my wired connection on Hardy. I have 4 computers two laptops and two desktops. One Laptop and Desktop on Gutsy the remaining laptop and Desktop on Hardy. Both laptops connect through the gigabyte router via wireless. The Desktops are wired into the same exact router. Which after messing around with the router settings makes me think it's not the router itself as all the computers but the desktop running Hardy don't experience this issue. The other three computers remain connected and work fine even while the Hardy Desktop has lost it's connection.

---

### Post by dmizer on 2008-05-19
post the output of:
```
lshw -C network
```

are you by chance using an imput method editor for alternative language interface like scim?

---

### Post by Brandel Valico on 2008-05-19
>  *-network               
       description: Ethernet interface
       product: Gigabit Network Adapter
       vendor: Linksys
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth0
       version: 10
       serial: 00:12:17:5c:80:ae
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=########## full ip= latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=1GB/s

Added the #### In place of my IP Address

As for the Alternative Language Interface. As far as i know I'm not doing so.

---

### Post by Brandel Valico on 2008-05-19
The above command ran on my hardy laptop

>   *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:80:c1:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=###.###.#.### latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:11:85:86:22:18
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.14 latency=64 mingnt=64 module=tg3 multicast=yes

---

### Post by dmizer on 2008-05-19
i did quite a bit of hunting on this problem and didn't find much of anything at all.

things you can try:
[LIST]
[*]reboot the router.
[*]reseat the ethernet cable connectors (remove and reconnect) on both ends.
[*]try a different ethernet cable.
[/LIST]

did you make your own cable? if so, how long are the untwisted portions of the wires?
is the cable running near any heat, power sources, or through a tangled mass of cabling? if so, make sure it's clear because these things can cause interference.

it's possible that none of this will fix your problem, but it's worth trying.

---

### Post by Brandel Valico on 2008-05-19
Will clear the cables and try everything else also. I have yet to reboot the router and the cable does run through alot of other wires. I bought them so thats out.

I do appreciate your help it is just odd. Though it seems it may have actually worked itself out as after my last reboot it has maintained a connection for hours of ktorrent usage.

---

### Post by Eroll on 2008-07-12
I have a very similar issue.  The connection dies under heavy load from the computer.  However this is something that just started happening within the last few weeks.  Things to note: recently updated the system (Hardy) with all the latest patches.  I had just recently purchased and installed an nVidia 9600GT.  I switched from an ATI x700 Pro card that was very touchy for 3d acceleration so once I got the ATI card working... i didn't really update much of the OS.  I guess what i'm getting at is that everything was working fine up until I installed the new video card and updated the system.  

Everything else is the same, heavy load just kills the connection. I can ping localhost, but nothing else.  I've tried everything to restart the connection, but seems (so far) that only a reboot fixes the issue.  Also it's sporatic. Sometimes the connection dies immediately upon loading up a game, and sometime will work for hours while I play.

---

### Post by waka324 on 2008-08-06
I have the same exact issue on both wired and wireless connections. dies under load, and will not resume until reboot. I think now though, that it may only happen under high upload rates. I also came across a thread stating to change wlan0 or eth0 to lo, but am unsure of how to do so.

---

### Post by Thedjatclubrock on 2008-08-06
Same here, during high-use (apt) the connection dies, and it only resumes after a reboot.

---

### Post by dmizer on 2008-08-06
can you revive the connection with this command:
```
sudo /etc/init.d/networking restart
```

could be a problem with NetworkManager, or any number of other things.

---

### Post by waka324 on 2008-08-06
all it says is
" * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
" and does not repair the connection. another interesting note, after I loose connection and disable and enable my adapter by the switch on my laptop, it connects back to the wireless router, however I cannot connect by 192.168.0.1 method.

---

### Post by dmizer on 2008-08-06
Please post the output of:
```
cat /etc/network/interfaces
```

---

### Post by waka324 on 2008-08-06
ok now it just says  "* Reconfiguring network interfaces... " and the output of cat /etc/network/interfaces is
"auto lo
iface lo inet loopback" I have yet to see if the revised interfaces file causes it to reconnect when using the reset command after loss.

---

### Post by dmizer on 2008-08-06
> **waka324 said:**
> ok now it just says  "* Reconfiguring network interfaces... " and the output of cat /etc/network/interfaces is
"auto lo
iface lo inet loopback" I have yet to see if the revised interfaces file causes it to reconnect when using the reset command after loss.

You didn't edit anything in the interfaces file did you?

I suspect that you're having a problem with NetworkManager.  On your wireless, are you using WEP, or WPA?

---

### Post by waka324 on 2008-08-06
yes actually I fixed my loopback entry from 
"auto wlan0" to what it was before. I edited it in attempt to fix the problem. didn't notice any difference either way.

I use WPA. And I have to agree. I think it must be an issue with my network manager, as vista never has issues with using too much bandwidth with my adapter/router combination.

---

### Post by dmizer on 2008-08-06
> **waka324 said:**
> yes actually I fixed my loopback entry from 
"auto wlan0" to what it was before. I edited it in attempt to fix the problem. didn't notice any difference either way.

I use WPA. And I have to agree. I think it must be an issue with my network manager, as vista never has issues with using too much bandwidth with my adapter/router combination.

Well, I suggest that you disable NetworkManager: [https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager)

Then, configure your network according to this howto: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by waka324 on 2008-08-07
Hmmm. I would much rather have a GUI for my wireless connection, but I have tried wicd and that seemed to fail, as my broadcom bcm4328 adapter requires the ndiswrapper drivers.

If there is any other solution you can think of? I am open to other 
sugestions, I just would like to keep a gui.

also, I read that changing wlan0 or etho0 to lo through connection properties fixed the issue, but I have no Idea what that means.

Thanks for all your help.

---

### Post by dmizer on 2008-08-07
Changing or manipulating your wired connection will be easy.  Just go to: System > Admin > Network

As for wireless, just configure it once, and you won't have to touch it again.  If you roam, you're unlikely to run into another WPA encrypted hot spot, so you can use System > Admin > Network to add the WEP key.

> **waka324 said:**
> also, I read that changing wlan0 or etho0 to lo through connection properties fixed the issue, but I have no Idea what that means.

I can't imagine a situation where this would make even the slightest bit of difference.  Actually, you should leave lo alone.  It's necessary for your computer to talk to itself (localhost) so if you change it, you may render your machine unbootable.

---

### Post by waka324 on 2008-08-07
Well I don't know, maybe it was the update I had a few days ago, hopefully it will correct itself sometime. I am just glad that I can use my wireless for normal browsing. I have Vista for torrents I guess. until an update fixes this. 

Thanks again for all your help.

---

### Post by waka324 on 2008-08-07
I am VERY sure it is solved!

[https://bugs.launchpad.net/ubuntu/+bug/136836]("https://bugs.launchpad.net/ubuntu/+bug/136836")

just open in a console

$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

to make the changes permanent, 

sudo gedit /etc/rc.local

and paste the commands above before exit command it is mentioned in the link.

I had to change the msi value to 1 though for my stable connection.

---

### Post by waka324 on 2008-08-08
*Update* 
Seems to have failed after a few hours. I have done further research though, and many seem to think that it is the ndiswrapper drivers causing this strange issue hopefully I can find a different driver or n another workaround. on the positive note, wicd works perfectly now.

---

### Post by waka324 on 2008-08-10
well... I am going to be a bit more conservative this time arround, but changing the mtu on my router seems to have fixed this issue. HOPE!!!

I am guessing if you don't have access to this option on your router there is a manual setting on you computer you can set. I set mine to 1492 and so far so good.

---

### Post by waka324 on 2008-08-10
Changing the mtu did not help at all i'm affraid. The connection still drops and will not resume regardless of anything I attempt until reboot. Still extremely frustrating.

---

### Post by canpolcon on 2008-08-12
try disabling the UPnP 
how to = [http://www.tweakxp.com/article37087.aspx](http://www.tweakxp.com/article37087.aspx)

---

### Post by waka324 on 2008-08-12
How would this help? And why did that link open an XP reference?

---

### Post by waka324 on 2008-08-12
I wish to gather some info so that we might be able to figure out this issue. List things that apply (ie ubuntu build, drivers, wether you use lan or wlan, and hardware)

Hardy 8.04
ndiswrapper around broadcom 43XX drivers
occurs on BOTH eth0 and wlan0
broadcom 4328 rev3 adapter
tx2000 tablet PC
dir 625 router
motorola cybersurfer cable modem

again, lets list any common traits about this to see if we can get it solved!

---

### Post by dmizer on 2008-08-12
64 bit?

I missed the part where you mentioned that you were having trouble on both wired and wireless.  Does it happen with the live cd?  Does it happen with Knoppix?  Does it happen with Windows?

Since your problem is both wired and wireless, I find it difficult to think that anything other than the router could be at fault.  Are you running alternate firmware on your router (if so ... what)?

Check the connections between your router and your modem.  Try a different cable between them if you have a spare.

---

### Post by waka324 on 2008-08-12
An interesting development. I am not sure whether it is the router, but I don't have the drop issue when connected directly to the cable modem. I will have to check again to make sure it does happen in wired mode when connected to the router. And yes it is 64 Bit.

---

### Post by waka324 on 2008-08-12
Oh and to answer your question, no, it does not happen in windows, and I wonder now if the router is dropping or me or my computer times out and my computer picks up slower in linux than in windows. Does this make any sense?

---

### Post by dmizer on 2008-08-12
> **waka324 said:**
> Oh and to answer your question, no, it does not happen in windows, and I wonder now if the router is dropping or me or my computer times out and my computer picks up slower in linux than in windows. Does this make any sense?

Yes, it makes a lot of sense, especially since you said that it appears to work correctly if you bypass the router.

Are you getting similar speeds in both Windows and Linux?

---

### Post by waka324 on 2008-08-12
Until it dies off in Linux, yes. I have yet to double test the cable through the router, but I don't think I need to. I only wonder why it doesn't die off with windows. Anyways... Is there any way this could possibly be fixed do you think? or do I have to run out and get a new router?

---

### Post by dmizer on 2008-08-13
If your router supports alternate firmware, you could try that.

[http://www.dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html](http://www.dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html)

---

### Post by waka324 on 2008-08-14
unfortunately it says that it is a work of progress for my router... anyways it is livable for now... Just very annoying

---

### Post by Brandel Valico on 2008-09-21
Well after a few months of downgrading my comp back to Gutsy. I thought I would try Hardy again and see if they had gotten this working. But sadly it seems it still isn't. My system still dies under heavy load preventing me from using the internet until a reboot.

Has anyone had any success in getting this to work yet? 

If so let us know or if there are any tests I can run to help others hopefully figure this out let me know.

---

### Post by Brandel Valico on 2008-10-05
Well thanks to Waka and the link he shared and some research. I have my connection working and stable. I've tested it for over two days of constant internet traffic and it no longer dies.

This worked for me

Add the following line to /etc/modprobe.d/options

options forcedeth msi=0 msix=0

Then rebuild initramfs like this

sudo update-initramfs -u

and remove any stuff you added to /etc/rc.local

Reboot.

---

