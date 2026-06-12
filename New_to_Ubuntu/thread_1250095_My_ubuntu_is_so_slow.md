---
title: "My ubuntu is so slow"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by ~The~Killer~ on 2009-08-26
Hi guys. 

I installed ubuntu last week and many members gave me alot of help here. 

But My ubuntu is going so slow (like a computer made before christ). and it's really annoying compared to windows Vista. 

what shall I do ? 

and shat is this ? Gnome? because I clicked "log out" then I changed the session to "Gnome" and now my firefox is "shirekoto" a name for an anime browser ? :P

Thanks

---

### Post by lisati on 2009-08-26
Going by t[his post]("http://ubuntuforums.org/showpost.php?p=7826026&postcount=1") your system specs seem OK, similar to my laptop.

I'm wondering if you're running a lot of programs at the same time or your Ubuntu partition is filling up.....

Are you having trouble with all programs being slow, or is it just one or two that are slowing down?

---

### Post by 3rdalbum on 2009-08-26
Look in System Monitor for any programs that are pushing your CPU (with high numbers in the %CPU column), and kill those programs.

---

### Post by Bartender on 2009-08-26
If Vista feels speedier than Ubuntu there is definitely something wrong!

3rd album's suggestion sounds good to me - it appears that the latest version of the automatic installer was built with the assumption that the user would push the slider to the left, giving Ubuntu some elbow room.  Lots of people missed that and installed Ubuntu to a tiny 3MB partition.

---

### Post by shankhs on 2009-08-26
Use xterm.
and as far as slow is concerned can you paste the screenshot of the process monitor here.

---

### Post by ~The~Killer~ on 2009-08-26
Thank you. 

I have ubuntu 30GB of Free space before the installation so it must be good. because it requires 2.5GB only. 

Yeah it's so slow compared to Vista when I minimize something there;s a slowness in doing it. when I want to open something , when I move the mouse...

NO i didn't install anything because I don't know how to :lolflag: 

this is the pic 
[img]http://i26.tinypic.com/29blev.png[/img] 

I really want to use ubuntu but it's going so slow and I don't know what to do :confused: It's like an old lady who'll die very soon

---

### Post by NoaHall on 2009-08-26
It could be a problem with your graphics card - have you got the drivers installed for it?

---

### Post by ~The~Killer~ on 2009-08-26
> **NoaHall said:**
> It could be a problem with your graphics card - have you got the drivers installed for it?
I am using a build in Graphic card , family chipset... 

do I need to install something for it ?

---

### Post by NoaHall on 2009-08-26
It could be the source of the problems. If it's a ati based card, then it's probably best to leave it, but if it's nvidia, go to 

System -> Administration -> Hardware Drivers 

And install what it recommends.

---

### Post by ~The~Killer~ on 2009-08-26
> **NoaHall said:**
> It could be the source of the problems. If it's a ati based card, then it's probably best to leave it, but if it's nvidia, go to 

System -> Administration -> Hardware Drivers 

And install what it recommends.
Thanks it gives me "No priority drivers are in use in this system" 

I did something while installation, I checked the "copy the Vista setting" to ubuntu so Now i have the same documents as Vista.

---

### Post by NoaHall on 2009-08-26
Is there anything in the list? Can you find out what card you have?

---

### Post by ~The~Killer~ on 2009-08-26
well I can't see anything but my Graphic card is "[** **Intel® 865 *Chipset Family"*]("http://www.intel.com/support/chipsets/sb/CS-009241.htm")

---

### Post by NoaHall on 2009-08-26
It could be because of that then. Try getting a nvidia graphics card.

---

### Post by zerhacke on 2009-08-26
Funny, Noa, but my wife is using an 8MB AGP video card and her computer is a screaming banshee.  Video performance has nothing to do with system performance.

---

### Post by NoaHall on 2009-08-26
Yes it does, if the drivers aren't activated, then it does effect it, in a bad way. A bad graphics card can stop it working.

---

### Post by zerhacke on 2009-08-26
> **NoaHall said:**
> Yes it does, if the drivers aren't activated, then it does effect it, in a bad way.

The intel chipset he has is automagically configured to work out of the box, so there's no instance of a driver not being activated here.

> A bad graphics card can stop it working.

Once again, my wife uses an 8MB AGP video card and her computer is insanely fast.  Video performance is not equal to system performance.  The Intel chipset s/he has is a fairly good card in most respects, easily 50X the video card my wife has, so it's not a "bad" card.

---

### Post by random turnip on 2009-08-26
Vista faster than Ubuntu?
DOES NOT COMPUTE!!!

Obviously the good old, do all updates and then restart thing might help, have you tried that yet?

---

### Post by NoaHall on 2009-08-26
Once again, the graphics card DOES affect the system.  And I don't care what your wife has, it does affect performance.

---

### Post by zerhacke on 2009-08-26
Ok, Noa, please describe how having an Intel 865 video adapter slows down application performance for, say, Firefox as opposed to having an nVidia 6100 video adapter.

---

### Post by NoaHall on 2009-08-26
The interface between the CPU, RAM modules and other things are all connected in some way to the onboard controller - the Intel.  If the intel controller doesn't work well with the operating system, then anything running from that board will be affected.

---

### Post by zerhacke on 2009-08-26
... yeah.

Well, I think that proves my point well enough.  I would reconsider giving advice in the future until you're a little more educated on how things work.

---

### Post by NoaHall on 2009-08-26
Urm, so you're saying that it doesn't go through the chipset at all? then what's the point having it? You're a imbecile. Without the chipset, the OS can't interface with parts. Buffoon.

---

### Post by ataide.carlos on 2009-08-26
Zerhacke, a wrongly configured video adapter will consume much more system resources than a video adapter with full support.
Older video adapters have drivers that are stable and very well teste, and therefore no conflicts and work out-of-the-box as opposed to new adapters (especially on Linux).

So your wife having an 8MB AGP board says nothing about the relation about video/system performance.

---

### Post by zerhacke on 2009-08-26
> **NoaHall said:**
> Urm, so you're saying that it doesn't go through the chipset at all? then what's the point having it? You're a fool. Without the chipset, the OS can't interface with parts. Idiot.

You have no idea what you're talking about when you use the word "chipset", do you?

Pray tell, is that northbridge or southbridge?

---

### Post by zerhacke on 2009-08-26
> **ataide.carlos said:**
> Zerhacke, a wrongly configured video adapter will consume much more system resources than a video adapter with full support.

I find myself repeating the part I said before about an Intel 865 being extremely well supported out of the box.

---

### Post by NoaHall on 2009-08-26
Yes I do, you nincompoop. Northbridge and South Bridge are both vital. Anything without simply can not interface with anything else.

---

### Post by zerhacke on 2009-08-26
Another instance of namecalling and I'm going to report your posts to the admins.

No worries though, I'm done.  I have better things to do with my time than argue with someone who doesn't understand what they're talking about.

---

### Post by NoaHall on 2009-08-26
Name calling? You're acting like I'm stupid and I don't know anything, when I'm the one in the right, not you.

---

### Post by ashwinhgtx on 2009-08-26
Guys please stop fighting. Come on let's solve this thread.:(

---

### Post by Mark Phelps on 2009-08-26
to The~Killer:

Did anyone ask you to post the results of "lspci"? If not, please do that so we can see what graphics chipset you're using.  I suspect it's probably an Intel 82865G Graphics chip.

---

### Post by ~The~Killer~ on 2009-08-26
> **Mark Phelps said:**
> to The~Killer:

Did anyone ask you to post the results of "lspci"? If not, please do that so we can see what graphics chipset you're using.  I suspect it's probably an Intel 82865G Graphics chip.
and here we go
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Multimedia controller: Broadcom Corporation Device 1612 (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

Nao and Nar do you need guns ? :guitar: to kill each other ?
[SIZE=6]
**Guys I need help**[/SIZE]

---

### Post by mrgreggie on 2009-08-26
Random thought (as I know nothing of that video adapter), do you have any special effects enabled?  If so, try disabling them (Under the appearance settings)

---

### Post by Bartender on 2009-08-26
I'm reading this thread with an Acer 5920 laptop, which uses the 965 chipset.  Or graphics controller.  Or whatever it is, please don't start calling me a nincompoop  :)

The laptop came with Vista.  I've installed Heron, Ibex, and Jackalope to it and they all left Vista in the ditch.  Much less RAM usage, snappier feel, and Jaunty's boot times are MUCH faster than Vista.  

So it's probly not the graphics.

EDIT:  I double-checked just now - "No proprietary drivers" detected in Hardware Drivers, and Visual Effects is set to "Normal", the middle of the three choices.

---

### Post by lswb on 2009-08-26
what version of ubuntu did you install? There are known problems with intel graphics in 9.04 and to some extent in 8.10. If you installed 9.04, would it be feasible for you to try 8.04 for comparison?

There are some fixes for the 9.04/intel problem, they might seem a little daunting to a new linux user. Hopefully the problem will be corrected when 9.10 is released. Here is a thread listing some fixes for the problems with 9.04

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Just to shed a little more more light and less heat, graphics problems can affect system performance for a number of reasons. A poorly implemented graphics driver can use excessive cpu cycles. And a slow display can cause a perception of a slow system.

---

### Post by sydbat on 2009-08-26
I just skimmed through this thread and I noticed that everyone forgot to ask the OP this obvious question...

**How did you install Ubuntu?**

If it is a wubi install AND the OP did not defragment his Windows install first, that can cause huge problems.

However, if the OP installed on a separate partition, please continue with your original line of questioning...

---

### Post by Bartender on 2009-08-26
sydbat -
You're right, I just assumed an actual install.  Post #6 kinda sounds like he installed it rather than wubifying...

---

### Post by sydbat on 2009-08-26
> **Bartender said:**
> sydbat -
You're right, I just assumed an actual install.  Post #6 kinda sounds like he installed it rather than wubifying...True. However, he may have meant he had 30GB free on his HDD, not a 30GB partition for Ubuntu. Either way, it sounds like something is definitely screwed up.

It may be a video driver issue.

Or it may require a full reinstall. It does happen...rarely, but it does happen.

---

### Post by fela on 2009-08-26
> **NoaHall said:**
> Once again, the graphics card DOES affect the system.  And I don't care what your wife has, it does affect performance.

I smell two people having a an argument with neither person knowing why his/her reason makes sense.

I'll tell you that, yes Noa you're right. It's because if you don't have a video driver installed the system runs software graphics. This means that the CPU renders all the graphics on its own, and so has much less cycles to do normal code execution.

Hope this clears things up for both of you.

PS. I'm 13, just a bit of depressing news for you both :P

---

### Post by cusinmex on 2009-08-26
> **NoaHall said:**
> It could be the source of the problems. If it's a ati based card, then it's probably best to leave it, but if it's nvidia, go to 

System -> Administration -> Hardware Drivers 

And install what it recommends.


what does ubuntu have against ATI cards 
T.T
mine is rigged with one 
and it works perfectly
idk

---

### Post by fela on 2009-08-27
> **cusinmex said:**
> what does ubuntu have against ATI cards 
T.T
mine is rigged with one 
and it works perfectly
idk

It's not as such what does Ubuntu have against ATI cards, more what does ATI have against Linux/Ubuntu. In fact Ubuntu devs would love (I assume) to get more ATI support in Ubuntu. It's just ATI that's stopping them.

---

### Post by SunnyRabbiera on 2009-08-27
> **~The~Killer~ said:**
> well I can't see anything but my Graphic card is "[** **Intel® 865 *Chipset Family"*]("http://www.intel.com/support/chipsets/sb/CS-009241.htm")

That might be the issue, if you use Jaunty the latest version of Ubuntu there is SERIOUS slowdown on intel graphics cards due to some bad mistakes made by both Intel and the Ubuntu development team.
I too faced slowdown on Jaunty on my machine that also uses a intel graphics card.

---

