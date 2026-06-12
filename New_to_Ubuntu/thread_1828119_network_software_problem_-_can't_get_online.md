---
title: "network software problem - can't get online"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by Buntu Bunny on 2011-08-18
I cannot connect to the internet since a bad storm, and have narrowed the problem down to the network software. Dell software support wants $129 to fix it (in Windows, but I'm thinking, if I'm having the same problem in both Windows and Ubuntu (dual boot) then why can't it be fixed on Ubuntu?)

Details (hopefully the helpful ones):
[INDENT]Dell Inspiron 570
Integrated 10/100/1000 Ethernet
Westell 6100 modem with ethernet cable
dual boot Win7 and Ubuntu 10.04[/INDENT]

Troubleshooting:
[LIST=1]
[*]Power & internet went out Friday due to horrific storm

[*]Internet came back up on Tuesday, but I couldn't get online. Ethernet light on modem wasn't lit.

[*]Icon in system tray stated, "No network devices available."

[*]Contacted service provider, who confirmed I did have internet service and how to troubleshoot the modem.

[*]Connected modem to an old computer, ethernet light came on. Reconnected to my computer, no ethernet light.

[*]Contacted Dell hardware support, who pinged my network device successfully & advised the problem was software.

[*]Talked to Dell software support, who can fix the problem for $129.
[/LIST]

It won't connect in either OS, but if I can use the modem in both, is there a way to troubleshoot and fix in Ubuntu?

---

### Post by pierreyy on 2011-08-18
if you think its the network manager software then try reinstalling it... i included the link... check  it out and let me know...

 >   [http://blog.sudobits.com/2010/07/23/install-wicd-network-manager-on-ubuntu-10-04/](http://blog.sudobits.com/2010/07/23/install-wicd-network-manager-on-ubuntu-10-04/) 

---

### Post by Buntu Bunny on 2011-08-19
> **pierreyy said:**
> if you think its the network manager software then try reinstalling it... i included the link... check  it out and let me know...

Pierreyy, thanks. I could not see how to download it from a library Windows based computer. Since I can't get online with my own machine, I'm having to go to the library to research this. Your link gives download options for Synaptic or via command line. I need to be able to download it to the library computer, put it on a CD or USB stick, and take it home. 

I'm not sure it actually is the network manager software, but am willing to reinstall. Suggestions?

---

### Post by ofnuts on 2011-08-19
> **Buntu Bunny said:**
> Pierreyy, thanks. I could not see how to download it from a library Windows based computer. Since I can't get online with my own machine, I'm having to go to the library to research this. Your link gives download options for Synaptic or via command line. I need to be able to download it to the library computer, put it on a CD or USB stick, and take it home. 

I'm not sure it actually is the network manager software, but am willing to reinstall. Suggestions?
Seriously, I have never seen a storm or a power outage affect software, especially on two different operating systems, one of them being inactive during the storm (dual boot). You problem is more likely either a fried ethernet port on your computer or, if you are very lucky, just a port that got disabled in the BIOS.

On Linux, issue "lspci" and see if it lists an Ethernet controller. On Windows, try the hardware manager to see if it detects the port. If it's nor there, enter the BIOS and see 1) if the BIOS lists it and 2) if it is disabled.

If you have another computer try interconnecting their Ethernet port (you don't even need a crossover cable), and see if you light up the port lights on your PC.

---

### Post by gandaran on 2011-08-19
> **Buntu Bunny said:**
> Pierreyy, thanks. I could not see how to download it from a library Windows based computer. Since I can't get online with my own machine, I'm having to go to the library to research this. Your link gives download options for Synaptic or via command line. I need to be able to download it to the library computer, put it on a CD or USB stick, and take it home. 

I'm not sure it actually is the network manager software, but am willing to reinstall. Suggestions?
re-installing network manager won't fix it, what you should try is just removing the existing network manager connection setup then try connecting again, this has worked for me many times when for some unknown reason network manager failed to connect.
also if the ethernet modem light doesn't come on you may have a hardware problem either the ethernet cable or ethernet card.

---

### Post by Buntu Bunny on 2011-08-20
> **gandaran said:**
> re-installing network manager won't fix it, what you should try is just removing the existing network manager connection setup then try connecting again, this has worked for me many times when for some unknown reason network manager failed to connect.
also if the ethernet modem light doesn't come on you may have a hardware problem either the ethernet cable or ethernet card.

I've already done the trouble shooting for the cable, modem, and card. The cable and modem work on another computer (ethernet light comes on) and the network card can be pinged, so Dell tells me it's working. 

In terminal, ifconfig tells me

         [I]lo        [INDENT]Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)[/INDENT] 
 [/I]

With $ nm-tool I get

[I]NetworkManager Tool 
State: disconnected [/I]

So I guess my question is, how do I get it connected manually? Gandaran, can you give a perennial newbie a step by step?

I'm having to travel back and forth to the library to get online, so I apologize that I'm slow with my responses. I truly do appreciate the help.

---

### Post by ofnuts on 2011-08-20
> **Buntu Bunny said:**
> I've already done the trouble shooting for the cable, modem, and card. The cable and modem work on another computer (ethernet light comes on) and the network card can be pinged, so Dell tells me it's working. 

In terminal, ifconfig tells me

         [I]lo[INDENT]Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2640 (2.6 KB)  TX bytes:2640 (2.6 KB)[/INDENT] [/I]

With $ nm-tool I get

[I]NetworkManager Tool 
State: disconnected [/I]

So I guess my question is, how do I get it connected manually? Gandaran, can you give a perennial newbie a step by step?

I'm having to travel back and forth to the library to get online, so I apologize that I'm slow with my responses. I truly do appreciate the help.
ifconfig shows only lo (loopback, always there since it's virtual) and no eth0, so  until you have an eth0 appear there is no point in trying to reconfigure.
I reiterate my recommandation to run "lspci" on Linux and/or the hardware manager on Windows to check if they see an Ethernet adapter. And if not, to have a quick check at the BIOS to see if it's disabled.

---

### Post by gandaran on 2011-08-21
run this command and paste any output errors 
```
sudo ifup eth0
```

---

### Post by spiky001 on 2011-08-21
I agree about hardware problem, Maybe pull the eth0 card out and reseat it

---

### Post by Buntu Bunny on 2011-08-21
> **gandaran said:**
> run this command and paste any output errors 
```
sudo ifup eth0
```

I will definitely do this when I get home, come back and report what I find.

Spiky001, Dell says it can't be hardware since the card can be pinged. Could they be wrong?

---

### Post by ofnuts on 2011-08-21
> **Buntu Bunny said:**
> I will definitely do this when I get home, come back and report what I find.

Spiky001, Dell says it can't be hardware since the card can be pinged. Could they be wrong?Depends how your modem works (direct or router) but the usual setup is "router" and in this case they just pinged the router. In fact you can't ping a machine if its network software isn't up and running...

---

### Post by Buntu Bunny on 2011-08-21
Gandaran, this is what I get.

[I][INDENT]sudo ifup eth0
ignoring unknown interface eth0=eth0[/INDENT][/I]

---

### Post by Buntu Bunny on 2011-08-21
> **ofnuts said:**
> Depends how your modem works (direct or router) but the usual setup is "router" and in this case they just pinged the router. In fact you can't ping a machine if its network software isn't up and running...

Hmm. My understanding (according to my service provider) is that router setup is for wireless. I'm wired, with an ethernet cable, so I assume it's direct (?) What you're saying though, is that it could my network device, in spite of what Dell tells me correct?

---

### Post by ofnuts on 2011-08-21
> **Buntu Bunny said:**
> Hmm. My understanding (according to my service provider) is that router setup is for wireless. I'm wired, with an ethernet cable, so I assume it's direct (?) What you're saying though, is that it could my network device, in spite of what Dell tells me correct?Yes. Wireless implies router mode. However, router mode is also much safer for wired, because computers on the internet cannot initiate a connexion to your PC, so it is more or less the norm those days.  It also allows the connection of other computers, a NAS, a network printer.... It easy to tell if you connect a working computer:  if its IP address ("ifconfig eth0" on Linux, "ipconfig" in a Windows command prompt) is 192.168.something and the gateway address if also 192.168.something (usually ends in .1 or .254), then your modem is in router mode. If the address is different and identical to what you get using an Internet service such as showmyip.com, then it's direct.

---

### Post by gandaran on 2011-08-22
> **Buntu Bunny said:**
> Gandaran, this is what I get.

[I][INDENT]sudo ifup eth0
ignoring unknown interface eth0=eth0[/INDENT][/I]
unknown interface eth0 means ethernet device not detected or no drivers.
try the command
```
lspci
```
does it detect ethernet card?

---

### Post by ofnuts on 2011-08-22
> **gandaran said:**
> unknown interface eth0 means ethernet device not detected or no drivers.
try the command
```
lspci
```does it detect ethernet card?Good luck with that question, it has been asked twice here already in the last two days... Must be taboo or something :)

---

### Post by Buntu Bunny on 2011-08-22
> **gandaran said:**
> unknown interface eth0 means ethernet device not detected or no drivers.
try the command
```
lspci
```
does it detect ethernet card?

[I][INDENT]$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Dell Device 9602
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200][/INDENT][/I]

I'm not entirely sure what this is telling me, but apparently not. My network card is Integrated 10/100/1000 Ethernet, and I don't see anything on there that looks remotely like that. 

Ofnuts, my apologies. I see that you asked me that too, previously, but somehow it didn't make it into my back-and-forth-to-the-library notes. *I'm* the one who must seem nuts. Needless to say, this whole experience has been a bit nerve racking. :)

I took a look inside my machine to try and locate the ethernet card, assuming it will have to be replaced. I didn't find a card per se, but rather the ethernet port is mounted to the motherboard. It's kind of tight, apparently soldered?

Since it will likely need to be replaced, any advice, tips, or heads up would be greatly appreciated. You guys are the best.

---

### Post by ofnuts on 2011-08-22
> **Buntu Bunny said:**
> I took a look inside my machine to try and locate the ethernet card, assuming it will have to be replaced. I didn't find a card per se, but rather the ethernet port is mounted to the motherboard. It's kind of tight, apparently soldered?

Since it will likely need to be replaced, any advice, tips, or heads up would be greatly appreciated. You guys are the best.

You may not find it because the Ethernet port is usually integrated in the motherboard (it's part of a processor support chip, aka "southbridge") (very likely since you seem to have a recent machine).

So 1) check the BIOS (I also recommended that a while ago....) to see if the Ethernet port hasn't become disabled by mistake. If you don't see any such option and the BIOS doesn't see the Ethernet port,  then you may be facing either a motherboard replacement (expensive if warranty doesn't apply), or at least adding a PCI Ethernet card (cheap...). Or you take Dell support by their own word and ask them to repair the machine for the $100 they ask :)

---

### Post by Buntu Bunny on 2011-08-22
> **ofnuts said:**
> You may not find it because the Ethernet port is usually integrated in the motherboard (it's part of a processor support chip, aka "southbridge") (very likely since you seem to have a recent machine).

So 1) check the BIOS (I also recommended that a while ago....) to see if the Ethernet port hasn't become disabled by mistake. If you don't see any such option and the BIOS doesn't see the Ethernet port,  then you may be facing either a motherboard replacement (expensive if warranty doesn't apply), or at least adding a PCI Ethernet card (cheap...). Or you take Dell support by their own word and ask them to repair the machine for the $100 they ask :)

Actually my machine is not quite a year old and still under the original warranty, until Sept 16, 2011. The software is not, hence the $129 fee! 

OK. I've made a copy of this entire thread and put it on a flash drive. When I get home, where I'm not rushed with a computer time limit, I'll go through it all *c-a-r-e-f-u-l-l-y*. LOL

---

### Post by Buntu Bunny on 2011-08-22
> **ofnuts said:**
> ... or at least adding a PCI Ethernet card (cheap...). 

Thinking out loud here. Does this mean I could add a PCI ethernet card and bypass the original network device? That would mean I'd need to configure it as well(?) 

I really need to take a class in this stuff.

---

### Post by ofnuts on 2011-08-22
> **Buntu Bunny said:**
> Thinking out loud here. Does this mean I could add a PCI ethernet card and bypass the original network device? That would mean I'd need to configure it as well(?) 

I really need to take a class in this stuff.1) yes, if you can't revive it through the BIOS, which is the next thing to try. 2) yes, but those days it could be configured automatically.

---

### Post by Overcast32 on 2011-08-22
> **Buntu Bunny said:**
> Thinking out loud here. Does this mean I could add a PCI ethernet card and bypass the original network device? That would mean I'd need to configure it as well(?) 

I really need to take a class in this stuff.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=27&name=Network-Interface-Cards](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=27&name=Network-Interface-Cards)

Yep, indeed you can just add one and use it. Always handy to have one around.

My guess would be that your Ethernet card took a power spike.

Anyone have a recommendation for a specific card that is known to work well with Ubuntu?

If i were in your same situation - my NIC just died after a good storm and wouldn't work in Windows or Ubuntu, I'd be getting a PCI Network Card (NIC for short).

---

### Post by Buntu Bunny on 2011-08-23
BIOS. The only thing network related I could find in BIOS was under Boot. It tells me my network device is my 5th boot device and that it's disabled. When I highlight & enter network device on that page, it tells me a network device is not installed.

So, ofnuts and Overcast32, your replies give me hope. I will search around on the forums and see if any specific cards are recommended for Ubuntu.

---

### Post by ofnuts on 2011-08-23
> **Buntu Bunny said:**
> BIOS. The only thing network related I could find in BIOS was under Boot. It tells me my network device is my 5th boot device and that it's disabled. When I highlight & enter network device on that page, it tells me a network device is not installed.

So, ofnuts and Overcast32, your replies give me hope. I will search around on the forums and see if any specific cards are recommended for Ubuntu.Since the Ethernet port is likely sharing its control chip with other stuff (USB, SATA, and serial ports, built-in sound...) you have better run a thorough checkup of your PC to asses the damage.

---

### Post by Buntu Bunny on 2011-08-23
> **ofnuts said:**
> Since the Ethernet port is likely sharing its control chip with other stuff (USB, SATA, and serial ports, built-in sound...) you have better run a thorough checkup of your PC to asses the damage.

The only other problem I *know* I'm experiencing, is that the system automatically reboots itself every time I shut it down. To turn it off I have to pull the plug. When I plug it back in, it stays off. 

I've run all the checks offered in the various menus, and they tell me everything is fine. Is there something else I should do to further assess my machine?

---

### Post by Buntu Bunny on 2011-08-23
> **Overcast32 said:**
> [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=27&name=Network-Interface-Cards](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=27&name=Network-Interface-Cards)

Anyone have a recommendation for a specific card that is known to work well with Ubuntu?

I found a list of Ubuntu supported wired network cards here - [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

---

### Post by ofnuts on 2011-08-23
> **Buntu Bunny said:**
> The only other problem I *know* I'm experiencing, is that the system automatically reboots itself every time I shut it down. To turn it off I have to pull the plug. When I plug it back in, it stays off. 

I've run all the checks offered in the various menus, and they tell me everything is fine. Is there something else I should do to further assess my machine?Could be another BIOS setting or another fried thing around the power supply.

---

### Post by Buntu Bunny on 2011-08-24
> **ofnuts said:**
> Could be another BIOS setting or another fried thing around the power supply.

OK I'll go back and check again. Thanks!

---

### Post by Buntu Bunny on 2011-08-26
I'm very relieved to announce that I am back online at my home computer. Installing a network card did the trick; a $25 fix for the software problem Dell wanted $129 to fix. 

All my research into Ubuntu compatible NICs was for naught. When I finally got to an electronics store, they only had one PCI desktop card on the shelves!  It's a Dynex and it worked right out of the box. The only thing I had to do, was to sign into my modem into my service provider and I was good to go.

Many thanks to everyone who responded to my plea for help. I couldn't have done it without you all.

---

### Post by ofnuts on 2011-08-27
Good :)

---

