---
title: "Linksys WMP54G"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by fromp on 2007-04-05
Hi, I know there are a few other posts on this wireless card, but they are too advanced for me.
I have a XP running downstairs connected via ethernet to a Westell modem with wireless. I have an Ubuntu machine running upstairs with a Linksys WMP54G card in it. I dont know what version the card is or what the key is to my network or anything like that. 
n00b - thats me
Any help on how to go about getting it set up would be appreciated.

---

### Post by Floppyjoe on 2007-04-05
To start off with you could determine the chipset of the card.
Issue for a pci card:
```
lspci
```
for a usb device:
```
lsusb
```
Post those outputs here and maybe someone can help you.

---

### Post by fromp on 2007-04-07
lspci returns:

the lspci returns:
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory
Controller Hub] (rev 03)
0000:00:01.0 VGA compaatible controller: Intel Corporation 82810E DC-133 CGc [Chi
pset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:01:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
0000:01:0a.0 Network controller: RaLink: Unknown device 0301 *I think you want this one*
0000:01:0b.0 Communication controller: Contextant HCF 56k Data/Fax Modem (rev 0:)

iv been through ndiswrapper, i followed the steps and tried the driver it said to use, but it still didnt work. I dont know if it was a bad tutorial or what...

---

### Post by beauwulf on 2007-04-07
> **fromp said:**
> lspci returns:

0000:01:0a.0 Network controller: RaLink: Unknown device 0301 *I think you want this one*
...

That would be a RaLink chipset - not sure which one though - RT2600? Mine comes up with a bus id of 02:06.0 instead of 01:0a.0 and it works with the RT61 drivers. 

I think it also depends one which version of Ubuntu you are using. I've heard others say these cards worked out of the box in Dapper, I couldn't get it to work at all in Edgy, but in Feisty it works (sorta) without using ndiswrapper.

---

### Post by fromp on 2007-04-07
yeah, i figured that out, and have installed the driver. ndiswrapper -l says hardware and driver are present, i got no errors.
 i think i just need to edit /etc/network/interfaces
i have no idea what i would need to put in it, it is empty except for lo loopback stuff
thanks

---

### Post by Floppyjoe on 2007-04-07
> **fromp said:**
> yeah, i figured that out, and have installed the driver. ndiswrapper -l says hardware and driver are present, i got no errors.
 i think i just need to edit /etc/network/interfaces
i have no idea what i would need to put in it, it is empty except for lo loopback stuff
thanks
Are you using Network-Manager applet?
What version of Ubuntu is running on the target machine?

---

### Post by beauwulf on 2007-04-07
first you have to find out what the interface is called - ifconfig will show the interfaces that the system can use, lo - loopback, eth0 - ethernet, and in my case ra0 for the wireless card, though it might be wlan0 or something else.

once you have the name, add the following to your interfaces file:

iface ra0 inet dhcp
wireless-essid {your router's name}
wireless-key {your WEP key if you use one}
auto ra0

note, using the GUI System\Administration\Network app will also edit to this file. If everthing were set up properly, (ieally) you should be able to just go there, see the new wireless interface, enable it, enter the ESSID and key and then connect without having to bring up a terminal at all.

---

### Post by fromp on 2007-04-07
im running dapper **server** 6.06 for various reasons, so it all has to be command line.
I believe its ra0 although I'll check. I have set the network name on my router, is that the essid? and how would i know if it has a wireless key?

---

### Post by Floppyjoe on 2007-04-07
I Found this information on the ndiswrapper list site after some investigation but I guess you may have already got it working.
> Card: Linksys #[WMP54G v4.1], 54mbps -- [link here|List#WMP54G v4.1]

    * Chipset: Ralink RT61
    * pciid: 1814:0301 and 1814:0302
    * Driver: Don't use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink [http://www.ralinktech.com](http://www.ralinktech.com). It compiles for 2.4 and 2.6 kernels.
    * Other: The rt2x00 Open Source Project ([http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)) have now a driver - but realy beta.
    * Other: The Ralink driver works great. It is not a plug and play, you need your kernel headers, the appropiate gcc (3.4) but when you can link it together and put it where it loads at startup, it works great. I am using WPA without any problem. 

You only have a wireless-key if you use encryption.

---

### Post by beauwulf on 2007-04-07
Yes, ESSID is the router's name, it's how you know you're connecting to your own router and not your neighbours.
Floppyjoe is right, the WEP key is for encryption, very rudimentary security but better than nothing. You'd probably know if you had one since you'd have to enter in a long string of numbers in the router and each computer that connects to it. 

Unless there's no other wireless networks in range, it's really a good idea to set some sort of security - WEP,(there's better encryption around, but harder to set up) or mac address filtering. Though it seems that lots of people don't bother, of the four other wireless networks I can detect, only two are secured, the others are wide open and broadcasting their default SSID's (one is literally named 'default'). There's not telling what someone less ethical than myself might do with that knowledge :twisted:

---

### Post by fromp on 2007-04-08
alright,
so if i set my network to be called "mynetwork" and have no key, /etc/network/interfaces should read:

```
iface ra0 inet dhcp
wireless-essid mynetwork
auto ra0
```

right?

iv tried that, but when i iwconfig, i still get no essid. what do i need to do. I found something awhile ago, but dont remember where it is that said i needed to do ifdown ra0

---

### Post by beauwulf on 2007-04-08
I think you're referring to restarting networking so that the changes will "take". You could try ```
sudo ifdown ra0 && ifup ra0
``` for just the wireless interface. Or  ```
sudo /etc/init.d/networking restart
``` for everything.
Or of course just reboot...

---

### Post by fromp on 2007-04-08
alright so i booted up this morning, and when it reached loading hardware dirvers, i get error:
```
[42950362.030000] BUG: soft lockup detected on CPU#0
``` after which it freezes.
i restarted, restarted in recovery mode, booted in rescue mode from cd, all with the same error, except for the cd which just didnt work.
I reinstalled and got back to the point of having just finished finalizing the driver, i put in the stuff in /etc/network/interfaces and tried ifdown ra0 (im logged in as root FYI). it telles me there is no such device. I tried ifup ra0 and get the error. I dont know what to do about it. im thinking new computer really soon, but i cant get working papers till may :(, so no income yet

---

### Post by beauwulf on 2007-04-08
There's a whole thread somewhere here on that soft lockup issue. Sounds like there's no one cause but it does seem like a common trigger is having the wireless card (or whatever other offending device) powered up while drivers are loading. 

My theory to explain my own eventual success is that I managed to prevent activating the wireless card too early by removing Network Manager (because it automatically starts up and searches for networks), and avoiding setting up the connection in the GUI...  thought that could be just Voodoo reasoning.

It may be that you got the soft lockup because once you managed to get the card set up, drivers are now being loaded (via ndiswrapper) on startup.
You might try removing the wireless card, and assuming that prevents the lockup, confirm all the steps setting things up are completed, then re-installing the card.

If ifdown reports no such device, do ifconfig or iwconfig show the card present? Those might point to a missed step in the configuration.

---

### Post by fromp on 2007-04-08
iwconfig shows it present. I dont know what i missed. Ndiswrapper says that dirver and hardware are present. depmod -a has no errors, modrobe ndiswrapper is also fine.
I have no idea what else i need to do. Everything in etc/network/interfaces is correct.
Anyhelp is welcomed and appreciated

---

### Post by Dj Delta9 on 2007-04-14
Im fairly new to all of this, but I finally got my WMP54G v4.1 working tonight.  I'm running dapper as well, but not server.  I followed this how to: 

[http://ubuntuforums.org/showthread.php?t=296822&highlight=RT61](http://ubuntuforums.org/showthread.php?t=296822&highlight=RT61)

I had to go to the ralink website, [http://www.ralinktech.com](http://www.ralinktech.com) to download the driver, and the how to assumes you have build-essential installed, but otherwise I followed the directions exactly up until step 6 where you edit the new rt61sta.dat file....this is what was in the how to:

> SSID=<SSID of Access Point>
NetworkType=Infra
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<Secret WPA key>

This is what I did since I'm using WEP right now:
> 
SSID=thematrix
NetworkType=Infra
Channel=0
AuthMode=SHARED
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=XXXXXXXXXX

That came from the 28th page of that thread.  Not sure if this will work for you, but maybe it will lead in the right direction.  Good luck!

---

### Post by fromp on 2007-04-15
thank you very much, i will check it out.
although i dont know what most of those are or how to find them

---

### Post by fromp on 2007-12-02
upgraded to 7.10 and it works fine.
although on ifdown wlan0 and ifup wlan0 i get an unrecognized hardware message but it works fine.

---

