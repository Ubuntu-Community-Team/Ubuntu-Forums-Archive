---
title: "Dual Video Cards, Need to only use one, Help please"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by altech6983 on 2010-05-12
Hey guys, I'm back.

For reasons that are a long story, I have two video cards in my system, a ATI HD4350 and a ATI HD4850 X2. I installed Ubuntu a while back and I have been trying to figure out how to set the "Default" card and monitor.

There are two cases that happens in Windows:

1) I am using two monitors on the HD4350 card and I want to switch them over to the HD4850 X2.

----To do this I normally go in to the Catalyst Control Center, disable the secondary
----monitor on the HD4350 and enable the two monitors on the HD4850 X2, make one the
----primary and then disable the last monitor on the HD4350. Switch the inputs on the
----monitors and done.

2) I am using two monitors on the HD4850 X2 card and I want to switch them over to the HD4350 card.

----To do this one it is just the reverse of the above.

That is the optimal situation that I hope for in Ubuntu but I know it is not a realistic goal so all I want to do now is have just one monitor on, coming from the HD4850 X2.

The problem is when I go in to CCC to change the cards the two outputs of the HD4850 X2 say [Unknown Display] Unknown Adapter. The most I can do is extend the desktop to the second monitor on the HD4350.

I suspect that I will have to modify the xorg file but I have never known what I was doing in there so I thought I would ask for help.

So what do y'all need to help me(lspci and stuff like that)?

Thanks for any help,
altech6983

---

### Post by -humanaut- on 2010-05-12
Can you just remove one? I'm not familiar with ATI but I would think you could just take one out or if you have an AMD chip you could balance the IRQ to shut it off.

---

### Post by altech6983 on 2010-05-12
Could just remove one and do all the reconfiguration but I still need to be able to access it in windows and I switch at least once a day so physically removing the card isn't an option. Now if you meant pulling the card just to do the reconfiguration then it is feasible but I would like to avoid it if at all possible. 

I have a Intel chip. Ideally I would love to just be able to shut the power off to the slot but I haven't ever found a way to do that.

Thanks for the suggestion though and if it comes down to it I will probably have to do that.

P.S. I should also say that I am on 10.04, I just hadn't updated profile yet.

---

### Post by -humanaut- on 2010-05-13
> **altech6983 said:**
> Could just remove one and do all the reconfiguration but I still need to be able to access it in windows and I switch at least once a day so physically removing the card isn't an option. Now if you meant pulling the card just to do the reconfiguration then it is feasible but I would like to avoid it if at all possible. 

I have a Intel chip. Ideally I would love to just be able to shut the power off to the slot but I haven't ever found a way to do that.

Thanks for the suggestion though and if it comes down to it I will probably have to do that.

P.S. I should also say that I am on 10.04, I just hadn't updated profile yet.

Yeah, I don't believe IRQ balancing is possible with Intel chips.

---

### Post by mayagrafix on 2010-05-13
Ubuntu does not have the best and the latest video drivers available as per Windows and in some cases, Apple McIntosh. That said, what they have available is pretty good homemade. 

From What I can make out of your post, you have two (2) physical cards installed in your box? I am assuming 2 PCIx slots (for Crossfire hookup) and using catalyst control center you make one or the other card the primary. Is this for HTPC?

I have a simple dual monitor set up with One ATI GPU and I cant even set the right monitor resolutions to begin with because it is still not supported by Ubuntu (Doesn't help that I'm using two different sized monitors to begin with).

Also ATI itself doesn't support a linux version of CCC so that should be a clue.

---

### Post by quadproc on 2010-05-13
> **altech6983 said:**
> Hey guys, I'm back.

For reasons that are a long story, I have two video cards in my system, a ATI HD4350 and a ATI HD4850 X2. I installed Ubuntu a while back and I have been trying to figure out how to set the "Default" card and monitor.
...

You might get some mileage out of supplying a BusID in your xorg.conf file.  Apparently, the Device which has an associated BusID is considered to be the primary device.  Here is a copy of the device section of my xorg.conf (I have HD4870x2)
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```Of course, your system is likely to use a different number than mine for the BusID so check that with```
 lspci | grep ATI
```quadproc

---

### Post by altech6983 on 2010-05-14
Well if y'all are curious then I will just have to give you the back ground story. I live in south Texas where it is always hot. I go to college and I live in an apartment. This apartment has a poorly designed a/c unit and as such there is almost no circulation in my room when the door is closed. The HD4850 pumps out plenty of heat so it would raise the room temp about 7 degrees (from about 72F to 79F). I'm one of those people that thinks 65F is nice weather and 76F is just to hot to be comfortable. Thats when I came up with the solution that I would run a smaller card when I wasn't gaming or doing graphic intensive work. Doing so managed to drop the temp to 74F so it is just barely tolerable. I also installed a fan in the a/c duct to help push the air into my room and so that there would always be some circulation. That helped get it down to about 72.5F.

Back to the problem, lol:

Here is what I have now tried.

I tried switching out the bus number but to no avail, Ubuntu would boot but get stuck at the loading screen.

I then tried trimming down the xorg file because it was actually setup for two monitors and all I did was change the bus numbers. This lead to Ubuntu booting, getting stuck at the loading screen but playing the sound you get when you get to the login screen. I checked all the monitors but I couldn't find the "Display" it was on so who knows.

Thats when it was getting late and I was getting impatient. So I decided to remove the 4350 and remove and then reinstall the fglrx driver and then have aticonfig create a file for this setup. That worked. I was able to use the HD4870 now so then I put the 4350 back in. Went to boot and it would get stuck at the loading screen. I then would boot in to recovery mode and run the command ```
aticonfig --list-adapters
``` and sure enough the 4350 was marked the primary.

I though the xorg file would handle that being that it was specific and all.

I looked through all the commands in aticonfig but I can't seem to find one to change the default adapter. I think that is what I need to do.

So any advice?

P.S. I have gotten two different size monitors setup and working. All I had to do was install the ati driver from their site (the .run file). Then I could go into ATI Catalyst Control Center (Administrative) and I could change the settings so that it wouldn't be mirrored. Both monitors were hooked up by DVI.

Also this is what my xorg.conf file looks like with just the HD4870 card in and one of the monitors disabled with ATI Catalyst Control Center (Administrative).

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[2]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[2]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[2]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[2]-0"
	Device     "aticonfig-Device[2]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

