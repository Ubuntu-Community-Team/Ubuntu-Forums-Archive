---
title: "Madwifi for AR5006EG?"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by FlyingIsFun1217 on 2008-01-14
Hey!

I'd love to get the new version of the madwifi drivers installed, in attempts to get my AR5006EG card working, but... I'm a little lost on the process.

I know to build and install the drivers, you use 'make' and then 'make install', but is that all? Do I have to do anything to make sure that the system is using these, etc.?

Thanks for the help!
FlyingIsFun1217

---

### Post by Hightide on 2008-01-14
I picked up this thread although its Feisty Fawn , you may find it useful

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

:)

---

### Post by FlyingIsFun1217 on 2008-01-14
I'll try that for a temporary fix, but I would love linux drivers for it. Call me an enthusiast if you will... :)

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-14
Alright, I installed through ndiswrapper, and figured that everything was working, since I saw this in the network dialog:

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/Networksettings.png[/IMG]

and this showed up in the network tray:

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/Canseenetworks.png[/IMG]

So, I tried connecting, and got the normal dialog (expected):

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/Connectingthroughroamingmode.png[/IMG]

So I entered in the network key, and after a while, the five bars in the bottom filled up, and the tooltip showed 100% (I'm right next to the router). Alright! I figured that I was ready to go. Opened up firefox, and nothing happened. Opened pidgin, nothing happened.

Opened up the system monitor, and saw this:

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/networkhistory.png[/IMG]

So... some stuff is getting through. But after about 20 seconds, the connection dialog asking for the network key popped back up. I kept going through the dialog coming up after about 20 seconds every single time, but it never worked.

Any ideas on this one?

Thanks again!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-14
Anybody? Bump before bed :)

FlyingIsFun1217

---

### Post by kevdog on 2008-01-14
> **FlyingIsFun1217 said:**
> I'll try that for a temporary fix, but I would love linux drivers for it. Call me an enthusiast if you will... :)

FlyingIsFun1217

What do you mean -- madwifi are linux drivers -- ndiswrapper uses windows drivers!!

---

### Post by FlyingIsFun1217 on 2008-01-15
Well, the link posted is for ndiswrapper, not the madwifi drivers like I was hoping.

Still would love to solve the issue at hand, though.

FlyingIsFun1217

---

### Post by kevdog on 2008-01-15
Try connecting from the command line first to see if you can connect using your driver set, and then we can work on the GUI later.  Sometimes connection errors are driver errors, other times they are related to network manager.  Lets just cut out one layer of complexity and just work in the command line right now, and then use the gui later.  The instructions for using the command line are in my signature.  Good Luck.

---

### Post by FlyingIsFun1217 on 2008-01-15
Well, here's the interesting part: using ifconfig only outputs 'eth0' and 'lo', no wireless of any sort.

Guess that makes it kind of hard to troubleshoot.

FlyingIsFun1217

---

### Post by kegobeer on 2008-01-15
> **FlyingIsFun1217 said:**
> Hey!

I'd love to get the new version of the madwifi drivers installed, in attempts to get my AR5006EG card working, but... I'm a little lost on the process.

I know to build and install the drivers, you use 'make' and then 'make install', but is that all? Do I have to do anything to make sure that the system is using these, etc.?

Thanks for the help!
FlyingIsFun1217

Installing the drivers is very easy, if you follow the instructions.  Read these wiki entries:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)

Now, I haven't researched your card and the chipset, so I don't know if the experimental ath5k drivers will work, but it doesn't hurt to try.  They work for my AR5418 chipset, even though that particular chipset isn't listed in the working cards list.

---

### Post by FlyingIsFun1217 on 2008-01-15
I'll try again to use Madwifi (before I just did a make, make install, nothing more).

Anything special I need to do to stop ndiswrapper from trying to be used?

Thanks again!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-15
Seems that no matter how hard I try, the current version of madwifi just wont cut it (even with a patch that is supposed to fix the issue).

After 'modprobe ndiswrapper', dmesg gives:

> [12063.184000] ndiswrapper (NdisWriteErrorLogEntry:191): log: C0001389, count: 4, return_address: f8eb06d4
[12063.184000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf510f600
[12063.184000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0x28
[12063.184000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf8dee000
[12063.184000] ndiswrapper (NdisWriteErrorLogEntry:194): code: 0xf8dee000
[12063.184000] ndiswrapper (mp_init:216): couldn't initialize device: C000009A
[12063.184000] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[12063.184000] ndiswrapper (mp_halt:259): device eb2cc500 is not initialized - not halting
[12063.184000] ndiswrapper: device eth%d removed
[12063.184000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[12063.184000] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[12063.184000] usbcore: registered new interface driver ndiswrapper


Hmmm... :/

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-15
> 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 137a
        Flags: fast devsel, IRQ 22
        Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-15
Got iwconfig to print out info for wlan0, so I'm gonna try the guide from your sig...

FlyingIsFun1217

---

### Post by kegobeer on 2008-01-15
To remove the ndiswrapper driver:

ndiswrapper -l  (to display the driver list)
ndiswrapper -r (driver name)

---

### Post by kevdog on 2008-01-15
ndiswrapper and madwifi do not go together -- they are mutually exclusive.  You need to remove the ndiswrapper kernel module, compile, and install the madwifi module, and then load the ath_pci kernel module (instead of ndiswrapper).

Just an FYI

---

### Post by kegobeer on 2008-01-16
> **kevdog said:**
> ndiswrapper and madwifi do not go together -- they are mutually exclusive.  You need to remove the ndiswrapper kernel module, compile, and install the madwifi module, and then load the ath_pci kernel module (instead of ndiswrapper).

Just an FYI

No, I don't believe that's correct.  I have used both the 0.9.3 and the experimental versions, and I never had to do anything to ndiswrapper.  In fact, the newbie howto docs on the madwifi website make no mention of ndiswrapper.

---

### Post by kevdog on 2008-01-16
What??

You can only use one specific kernel module:

ndiswrapper+windows driver
or
madwifi

not both!

You can have both installed, but only one kernel module can be loaded into the kernel at any one time.  To use one and not the other, you need to unload one module and then load the other.  They are not meant to be used at the same time, and if they are, driver conflicts will probably arise.  I have both madwifi and ndiswrapper installed on my machine with an Atheros chipset, but usually use madwifi.  This is not an endorsement of madwifi, only telling you that you cant use both kernel modules at the same time.

---

### Post by FlyingIsFun1217 on 2008-01-16
Well, I've ruled out madwifi (as I have tried using a patch for it made by atheros themselves, and it does not work), so I'm sticking with ndiswrapper.

The only problem now is getting it to actually connect. I can see networks, scan, etc., but (in wicd) I get to obtaining IP address, I don't get anything. This goes for network-manager too.

Any ideas on this one? It's the only thing on this system that seems to not be supported, and it's also one of the most crucial (to me).

Thanks again!
FlyingIsFun1217

---

### Post by kegobeer on 2008-01-16
> **kevdog said:**
> What??

You can only use one specific kernel module:

ndiswrapper+windows driver
or
madwifi

not both!

You can have both installed, but only one kernel module can be loaded into the kernel at any one time.  To use one and not the other, you need to unload one module and then load the other.  They are not meant to be used at the same time, and if they are, driver conflicts will probably arise.  I have both madwifi and ndiswrapper installed on my machine with an Atheros chipset, but usually use madwifi.  This is not an endorsement of madwifi, only telling you that you cant use both kernel modules at the same time.

I understand that you can't have the ndiswrapper using a Windows driver at the same time you are using madwifi.  I just wanted the OP to know that you don't have to recompile a kernel to use the madwifi drivers.  Just uninstall the ndiswrapper Windows driver and then install madwifi.

---

### Post by kegobeer on 2008-01-16
> **FlyingIsFun1217 said:**
> Well, I've ruled out madwifi (as I have tried using a patch for it made by atheros themselves, and it does not work), so I'm sticking with ndiswrapper.

The only problem now is getting it to actually connect. I can see networks, scan, etc., but (in wicd) I get to obtaining IP address, I don't get anything. This goes for network-manager too.

Any ideas on this one? It's the only thing on this system that seems to not be supported, and it's also one of the most crucial (to me).

Thanks again!
FlyingIsFun1217

The same thing happened to me with my 5418 (D-Link DWA-643).  When using the ndiswrapper I could see the network but never connect.  Others with the same card were able to use ndiswrapper.  I couldn't get the thing to work at all, but luckily madwifi works for me.  Sorry I don't have an answer for you, other than to get a different wifi card for your computer.

---

### Post by FlyingIsFun1217 on 2008-01-16
Well, in a laptop, thats definitely not an option. I don't plan on using my PCI port for an older, yet supported card... I want the one my laptop came with to be able to support it ;)

I'll get in contact with atheros, HP, and possibly madwifi about this. Obviously I have some sort of rare case where something just isn't lining up right.

FlyingIsFun1217

---

### Post by kegobeer on 2008-01-16
Have you tried the experimental drivers without any special patch?

---

### Post by phidia on 2008-01-16
> **kegobeer said:**
> Have you tried the experimental drivers without any special patch?

Does anyone know if the experimental driver will work on 64bit ubuntu?

---

### Post by FlyingIsFun1217 on 2008-01-17
By experimental drivers, do you mean the SVN build? In that case, yes, I have.

FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-19
Alright, I feel I'm getting closer. I've gone through the command-line tutorial in said signature again, this time making sure that I have specified the access point as open encryption, and I see the light on the modem/wireless router lighting up. When I do 'ifconfig', it presents me with:

> wlan0     Link encap:Ethernet  HWaddr 00:1E:4C:98:41:7F  
          inet addr:75.57.173.133  Bcast:75.57.173.135  Mask:255.255.255.252
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59927 (58.5 KiB)  TX bytes:24495 (23.9 KiB)
          Interrupt:17 Memory:f6000000-f6010000 


I can see from the RX/RT bytes that some stuff is getting through.

The thing is, I still am not able to USE the connection. No matter what app, Iceweasel, Pidgin, Icedove, Transmission,... doesn't matter, it just doesn't pick up a connection.

What am I missing? Surely being this close does not mean that it cannot be done!

I even tried PCLinuxOS to see if I could connect using ndiswrapper (heard it had decent wireless support), and using the same driver I am right now, it let me choose which network to connect to, and let me enter the key. Next thing I know, it's connected, and I was able to use the connection right away.

Uhhh... this is getting exhausting!

Thanks again!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2008-01-19
Well, in desperation, I'm trying SAM Linux, because I'm in love with XFCE, and so far, PCLOS is the only distro that's... well, 'just worked' with my hardware.

Sorry Ubuntu :(

FlyingIsFun1217

---

### Post by bobpaul on 2008-01-21
> **FlyingIsFun1217 said:**
> 
I even tried PCLinuxOS to see if I could connect using ndiswrapper (heard it had decent wireless support), and using the same driver I am right now, it let me choose which network to connect to, and let me enter the key. Next thing I know, it's connected, and I was able to use the connection right away.

Well, I'm watching this thread because I want to get madwifi working, but I thought I'd share some experience with ndiswrapper.

I have an AR5BXB63 Mini PCIe card in my laptop. This is an AR50006EG based card. I used ndisgtk to install the driver mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=3592522&postcount=23").

Even after that, though, I still experience some problems. Occasionally if I check ifconfig my mac address is all 00s. I can fix this with "sudo rmmod ndiswrapper". If I wait about 10-20 seconds, ndiswrapper reloads itself and the interface reappears, usually with a valid mac address. When this happens, "iwlist wlan0 scanning" usually works, otherwise I repeat the same fix as for a 00 mac address.

I'm running it with WPA configured through network-manager.

---

### Post by bobpaul on 2008-01-21
Well, I got it to work on my hardware mostly.

I found [this bug report linked]("http://madwifi.org/ticket/1679") from the madwifi compatible hardware page. 

First, do step 2 in the requirements to ensure you have a compatible card. Also keep in mind that this works on 32bit ubuntu only. You can have a 64bit processor, you just have to be running the 32bit software.

Now, scroll down in the comments to "12/16/07 03:05:03 changed by mrenzmann" and there is a ready patched tarball you can download. 

After untaring, cd to the scripts/ folder and run 'sudo ./madwifi-unload' and 'sudo ./find-madwifi-modules.sh $(uname -r)'. When find-madwifi-modules asks you to remove old modules, be sure to press 'r' to remove them.

Now you need to reboot. If you don't, no ath0 interface will be created and dmesg will complain about incompatibilities with ath_hal, despite the fact that you unloaded the ath_hal module and replaced it with the newly compiled one...

Upon rebooting, cd to the madwifi-ng-r2756+ar5007 again and run 'make' and 'sudo make install'. You should now be able to 'modprobe ath_pci'.

My network-manager still doesn't seem to recognize the interface, but I did connect to an insecure access point using [Kevdog's HowTo]("http://ubuntuforums.org/showthread.php?t=571188")

**Edit:** Turns out network manager doesn't recognize wireless if you have a wired network plugged in. I unplugged my cable and now everything works great!

---

### Post by FlyingIsFun1217 on 2008-01-28
I've simply switched to PCLOS, and was able to use my windows drivers through NDISWrapper. Works like a charm.

FlyingIsFun1217

---

