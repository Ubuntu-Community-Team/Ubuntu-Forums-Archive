---
title: "Very slow!"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by zcacogp on 2009-04-03
Chaps, 

I'm new here. Be gentle! 

I grasped the nettle earlier on this week, and did what I have promising myself I would do for about a year or so; downloaded and installed Ubuntu on my desktop PC. I used the latest version (8.10 - Intrepid Ibix), chose the 32-bit variety 'cos that's what seemed to be recommended, partitioned my hard drive (even further - it was in three chunks already) and ended up with a dual-boot thing to allows me to choose between XP and Ubuntu at start-up. 

It wasn't as easy as I'd hoped. But it wasn't that hard. It works. It runs, I have Firefox (which I rate highly, and am very familiar with from XP), and Open Office (yet to play with that, but it will be crucial - I am a heavy MS Word/Excel user.) I managed to download a Citrix client to allow me to access the network of one of my clients' today, and just about managed to make that work too. 

However, Ubuntu is SLOW! Frankly, it runs like a dog. The machine is a dual-core AMD 5600 machine, with 2Gb of RAM. I built it about 5 months ago, and it runs XP like a rat up a drainpipe. It has always been bulletproof, and is a pleasure to use XP on. 

With Ubuntu however, there is a different story. It is slow to respond to mouse clicks, slow to display characters on screen and is a problem to use. Looking at the traces of processor activity, it always shows at least 50% activity on one of the cores (seems to swap them over from time to time), and the other shows around 30%. That's at idle; run some software and it'll go up from there ... the same machine shows between 1% and 2% at idle when in XP ... 

I have a number of questions about Ubuntu (I may become a regular on here - which may be bad news!) but the biggest one is performance. I want to like it. I want to use it. But it's just not a go-er at the moment, because of the slow running. 

I can't believe this is typical (everyone says that Ubuntu is quicker than XP on a like-for-like machine) so if you can give me some pointers on what to look at I'd be grateful. 

Warning ... I know nothing about LINUX. I am a moderately dab hand with XP, but really don't know where to start with Ubuntu, so please speak slowly ... thanks! 


Oli.

---

### Post by kyalee on 2009-04-03
I don't know how helpful this will be, but it's worth a shot. I recently installed Ubuntu on my laptop and it was running slowly for me. Very frustrating. Then I looked at my GUI and realized things were spiffier than I was used to on my desktop. I went to System-->Preferences-->Appearance (depending on how your desktop is set up, this might just be Preferences-->Appearance) and clicked on the Visual Effects tab and sure enough, Ubuntu was set to "Normal". I guess Ubuntu detected my hardware during the install and decided my machine could handle it. Not so much. I changed the setting to "None" and it improved performance a whole bunch.

So, if you want, you can try that.

---

### Post by zcacogp on 2009-04-03
Whoosh! That was quick - thanks kyalee!

I'll try it. (I'm not on the Ubuntu machine at the mo. That's another thing I guess - I have the desktop - Ubuntu'd - and a couple of IBM Thinkpads. If I can get things to go swimmingly on the desktop, then I'll be putting Ubuntu on the lappies as well. But something tells me I may have a lot of learning to do before I get to that stage!) 

I'll report back when I've tried your suggestion. 


Oli.

---

### Post by quinnten83 on 2009-04-03
Do you know if all the hardware you have is supported, sometimes that might be the case.
I suspect you might have mispartitioned your drive though, and that might be causing you some issues.
Did you leave the defaults or did you manually partition?
Are you ready to use a terminal?
If so, issue the command ps on the command line, to see what is using processor power, that way we might be able to help further.

---

### Post by ibuclaw on 2009-04-03
Before I buckle you over. I just thought I might like to point out that there is a rather curious bug in the gnome-system-monitor app that causes the program to use an abnormally large amount of CPU usage, so what you are reading may be rather tainted from the truth.

So what I'll ask you to do first, is re-open up the System Monitor App and go into **Edit->Preferences**.

Under the **Processes** tab, set the **Update Interval** to **10.00** seconds.
Under the **Resources** tab, to **6.00** seconds.
And Under the **File System** tab, to **30** seconds.

That should help half the usage being emitted from gnome-system-monitor to give you a more accurate reading.

As for any other sluggishness, Ubuntu comes with quite a few bundled startup apps and background processes that are there to suit both Laptops and Desktops at the same time, but may not benefit just the one or the other.

Fortunately, Ubuntu, as well as all things Linux are made to be as easily fine grained and re-tunable as possible. :D

There are plenty of HowTOs about for the competent user, but to get you started off, applications that start every time you login can be tuned with the **System->Preferences->Sessions** app.

And you can uncheck or remove some uneeded things, such as:
**Bluetooth Manager**
**Evolution Alarm Notifier**
**Remote Desktop**
**Tracker**
**Tracker-Applet**
**Visual Assistance**


For the more competent user, you could go into **Applications->Add/Remove**, and search for **bootup-manager** and install it.

Then go into **System->Administration->BootUp-Manager** and remove any unnecessary background processes.
There is an excellent reference here: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

And that is really just the smallest piece of icing on the cake of just what you can do, there is so much more to explore and learn, if you are willing. :)

Regards
Iain

---

### Post by mgmiller on 2009-04-03
tinivole, your suggestions would be good for a machine with limited resources, and indeed is very helpful in those circumstances.  But.... the OP's mahcine is a dual core AMD 5600 with 2 gig of ram.  This should absolutely fly on Ubuntu. 

You can try opening a terminal by going to Applications > Accessories > Terminal and entering the following command:
```
top
```This will tell you what processes are using the cpu and memory and by how much.  It also does not have the overhead of System Monitor, so you get a pretty accurate reading.

Once you do that, post back here and let us know what the first few processes are and how much cpu they are using.  That may give us a clue.


Also, what video card are you using and what driver for it?  Sometimes a misconfigured video driver can bog down even the fastest system.

---

### Post by zcacogp on 2009-04-04
Chaps, 

Thanks for your suggestions. Let's work through them one by one. 

kyalee - I have set the Effects to 'None' and this has helped things quite a lot, thanks. Still not as good as when running XP but it will now scroll webpages in Firefox at something resembling a reasonable speed, so that's good. It has however meant that I have lost the natty effects that it had - I particularly liked the way it shrunk and expanded the windows! Oh well. Surely it should do better than that - it is not a slow machine usually? 

quinnten83, yes, I am happy to use a terminal - I had to do so to install Citrix. My concern however is that I just typed in commands that I picked up from a web page, and had no understanding what I was doing - which worried me. 

I think all the hardware is supported, how would I tell if it is otherwise? 

I manually partitioned the drives. They are now as follows (according to the Disk Usage Analyser): 

Device       Mount Point    Filesystem Type   Total size   Available
/dev/sda8    /              ext3              18.3gb       15.6gb
/dev/sda9    /home          ext3              37.0         36.7
/dev/sda1    /windows       fuseblk           70.6         42.1
/dev/sda6    /media/ianthe  fuseblk           74.8         53.8
/dev/sda5    /media/helena  fuseblk           92.8         76.2

This will probably tell you this already, but I have one partition which is the Windows programs, and two others (ianthe and helena) which are documents and music respectively. To this I added a Ubuntu operating partition ( 8 ), and a Ubuntu Home ( 9 ). Total disk usage is 23.6%. 

PS on the command line gave me this: 

  PID TTY          TIME CMD
12111 pts/0    00:00:00 bash
12129 pts/0    00:00:00 ps

... which means nothing to me. 

tinivole, changing the settings in the system monitor application really bought the system usage graph down. Not sure if it has made the system any quicker tho', although it seems to type a little better, perhaps (some of the delay between pressing the key and the character appearing on the screen has been reduced.) Both traces are knocking around below the 25% mark most of the time (although nearer 25% than 0%.) That's an improvement. 

I had already turned off some of the things under "Session" (bluetooth manager being one of them). I have now turned off the others you suggested, although left on the remote desktop - that is something I will be using (although need to experiement with.) I'm not sure that it made any difference at all tho', but thanks for the suggestion. I'll try reading the details on the link you provided. 

mgmiller, yes, my machine does very tidily on XP, so I would have thought it should be even better with Ubuntu. It still isn't tho' - even after these suggestions from the other chaps. 

"top" gives this: 

top - 19:45:51 up  8:55,  2 users,  load average: 0.04, 0.15, 0.16
Tasks: 122 total,   1 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.9%us,  2.4%sy,  0.0%ni, 89.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1811848k total,   867432k used,   944416k free,   101916k buffers
Swap:  3903724k total,        0k used,  3903724k free,   342376k cached

... and then a list of processes (I am assuming) that un-highlight as soon as I highlight them so I can't copy and paste! Sorry. Would a screenshot help? 

(In the process of writing this response I have also found that the good 'ol Windows standby of CTRL+C to copy doesn't work on Ubuntu. I am sure it can be built in, but I just don't know where to start!) 

The video card could be a good guess actually. I am using an all-in-one motherboard and video card, by Gigabyte. I think the driver is an ATI one (could be wrong - how do I find out from Ubuntu? I'd know where to look in Windows!) BUT I do recall there being problems with the driver in XP - I had to reduce the hardware acceleration one notch from 'maximum' to make it scroll in Firefox. How do I know if I am using the right driver in Ubuntu for this video card (/motherboard)? 

I can see that there is a lot more to learn with Ubuntu than with Windows. Yes, I would like to learn (I don't like using things I don't understand - tools, cars, computers, anything); can anyone point me to good resources to start with? I have already downloaded the *.pdf "Beginners Guide to Ubuntu" file which I am working my way through ... 

It will be good if I can get this performance thing cracked tho'. Or, to put it another way, I*** need*** to get this performance thing cracked! 


Oli.

ETA: Thanks again for your help. It's appreciated.

---

### Post by CatKiller on 2009-04-04
> **zcacogp said:**
> 
(In the process of writing this response I have also found that the good 'ol Windows standby of CTRL+C to copy doesn't work on Ubuntu. I am sure it can be built in, but I just don't know where to start!) 


Ctrl-C does something else in the Terminal. Shift-Crtl-C and Shift-Ctrl-V are the equivalents. But you can just highlight the text and then middle-click with the mouse to copy/paste.

---

### Post by mgmiller on 2009-04-04
> ... and then a list of processes (I am assuming) that un-highlight as soon as I highlight them so I can't copy and paste! Sorry. Would a screenshot help?

You don't have to do a screen shot, just tell us what the top 4 or 5 processes are along with their cpu and memory use, which you can determine from the column headings in top.  Overall, your CPU use of 7.9% does not seem too bad, but I have Firefox, rhythmbox and ssh servers running as well as a few terminal windows and top running and all of the desktop effects turned on and mine shows 2.9% to about 5% cpu total.  Top is dynamic, so it changes every second or so.

To determine what video card you have, copy and paste the following into a terminal.  The easiest way is to high lite it using the left mouse button and then click the middle mouse button in the terminal window to paste it.
```
lspci -x | grep -i "vga\|display"
```

You can also run System > Administration > Hardware Drivers  to see if you have an accelerated driver installed or not.

---

### Post by mgmiller on 2009-04-04
> (In the process of writing this response I have also found that the good 'ol Windows standby of CTRL+C to copy doesn't work on Ubuntu. I am sure it can be built in, but I just don't know where to start!)Yes, I find that annoying also.  It's set that way by default to make it easier for coders to do stuff.  I am not a coder, so here is how you change to to use ctrl+c and ctrl+v:

Open a terminal window and at the top click on Edit > Keyboard Shortcuts

You will see the copy and past short cuts listed as the first 2.  Just click the one for cut once to high lite it then  click it again to change it to "New Accelerator..." and then hold down the ctrl key and click the letter c key and it should change to ctrl+c.

Do the same for paste and change it to ctrl v.

---

### Post by DJonsson2008 on 2009-04-04
I'm experiencing the same thing as zcacogp, 

My dual core 1.8ghz UBUNTU machine sits side by side with my PIII
500ghz machine, and my PIII W2K out performs the Dual-Core Ubuntu
on many tasks. 

I've disabled start up sessions, programs, used something called preload to cache programs and have dumbed down my desktop effects to NONE. In otherwords all of the above, but on a 1.8ghz dual-core
this should not be neccesarry. W2K or XP on the same machine runs like a scalded cat, files and apps open in nano-seconds.

I'm really beginning to suspect that Ubuntu does not negotiated the
built in video cards on motherboards very well. I'm betting on a new Nvidia video card that will arrive next week, and hopefully that will help things a bit. 

Watching the systems monitor its easy to tell what I do on this machine never caps the available resources. TOP on shows the text
editor and browser running that I use. It seems this OS needs a better way to help folks track and nail what the bottlenecks are.

---

### Post by mgmiller on 2009-04-04
> I'm really beginning to suspect that Ubuntu does not negotiated the
built in video cards on motherboards very well.

It really depends on the video chipset.  I have 4 machines with built in SIS video that run great, although they are not capable of any kind of 3D effects.  I use them for office tasks and even image editing and they run great. 750 MB ram and AMD 2600+ 32 bit CPU's.  

I also built a machine for my son that is a dual core AMD with 3 GB of ram and built in 7500 Nvidia chipset and it runs great desktop effects and all.  

I have also run the Live CD on machines with various built in Intel chips and they have also run quite well, often providing correct resolutions for wide screen monitors that windows can't do on the same chips.

The point here is I have always stayed away from ATI wherever possible.  They have had a very bad reputation in the Linux world for a long time.  Hopefully this is now changing since AMD acquired them and they are slowly releasing source code for their drivers.

I suspect, what you and the OP have are ATI chipsets and this may be the root of your problems.  A video driver change (if possible) may work or you may need to explore a discreet Nvidia option.

---

### Post by CatKiller on 2009-04-05
> **mgmiller said:**
> Yes, I find that annoying also.  It's set that way by default to make it easier for coders to do stuff.

Not really. Ctrl-C terminates a running process. So if you've started something, say a locate command, and you changed your mind, Ctrl-C will stop it. But Linux is very flexible, as you've found. Things can generally be changed.

/end OT

---

### Post by DJonsson2008 on 2009-04-05
Keyboard macros are very programable in Ubuntu, small nuances easy to remedy. There are sufficent GUI's to get most things going. The performance thing tho seems to be hitting a lot of people.

For me I've 8 gigs HD overhead and there is enough RAM that swap is rarely if ever used. My Video curcuit is a Intel 947 / GMA on board,
I can see its using about 256MB of available RAM. I'm eager to get an Nvidia card with better support and even GUI (Envy) tools to tweak with it because Ubuntu does not seem to recognize or give me any control over refresh rate and few screen size options in this scenario. It also lessens my confidence that Ubuntu is working effectively with the onboard video. 

I've put Xbuntu on the same HD set up, it inherits most of the Ubuntu settings and I can boot into either Xbuntu or Ubuntu for now. Xbuntu with Swiftfox and preload is a bit snappier. The new video card arrives next week, I'm very curious how it impacts this setup.

Linux Mint is out, I'm sticking with Debian/Ubuntu variants at this point in time, now towards the science of performance optimization.

---

### Post by mgmiller on 2009-04-05
> Not really. Ctrl-C terminates a running process. So if you've started something, say a locate command, and you changed your mind, Ctrl-C will stop it.I was not aware of that use for ctrl-c.  Thanks for the info.

I just tried "locate bluetooth" in terminal and hit ctrl-c before it finished and it did successfully stop the process.  So, I guess I can have my cake and eat it too, as I also have ctrl-c and ctrl-v set for copy & paste.

---

### Post by 3rdalbum on 2009-04-05
I'd also check the last few lines of "dmesg".

```
dmesg
```

Sometimes my blu-ray drive doesn't come back from suspend properly and causes high CPU use because Linux is continually trying to bring it back up. Dmesg (which is the kernel's log) shows that this activity is happening.

---

### Post by mgmiller on 2009-04-05
> I'm eager to get an Nvidia card with better support and even GUI (Envy) tools to tweak with itYou really should avoid envy.  You won't need it to tweak an nvidia card.  Once the proprietary driver is selected from System > Administration > Hardware Drivers, it will also install a nice gui in System > Administration > Nvidia X Server Settings, that will allow you do do a lot of stuff.  If you need to have it write to the xorg.conf (not always necessary) You would run it as root by hitting Alt/F2 and entering the command:
```
gksu nvidia-settings
```The screen does go black for a few seconds when you run this whether from the regular menu or the gksu command, so don't have a heart attack when it happens.

The point is, try to avoid envy if at all possible.  It can make subsequent upgrades a real problem.  Try to stay within the normal Ubuntu configuration tools.

I forgot to mention the machine I use Ubuntu on is an AMD 8750 black edition triple core, overclocked on the mobo (M3N78pro) by 10%.  I have 4 gig of ram but since I am running the 32 bit version of Intrepid, I only get to use 3.5 gig.  the most important aspect is my video card.  Nvidia Geforce 8600 Gt (PCIe) with 256 MB ram.  I am running the Nvidia 180 driver as installed by the Hardware Drivers application.  This is certianly not a high end mosnter video card by any means, but when I'm playing UT2004, this setup really flies.  

I also use a Western Digital SATA HDD with the mobo BIOS set to EHCI for the SATA drives.  This makes a very noticable difference in HDD performance, so if your mobo supports it, enable it.  Ubuntu doesn't need any further configuration to use the EHCI advantages, it "just works".

If you are dual booting with Windows XP or Vista, you will probably have to install EHCI drivers before changing the BIOS settings, or Windows may refuse to boot or blue screen.

I recently upgraded my DVD burner to a Sony SATA burner that I got at Microcenter warehouse for US$35 on sale.  What a bargain.  It runs rings around my old PATA burner and even does litescribe.

I find the machine very snappy in every application I run, whether it be simple video editing, googleearth, gimp, etc.  

So, hang in there, a good video card can make a huge difference.

---

### Post by mtm_king on 2009-04-05
I was surprised how much of an improvement I got after installing Flashblock.

In Firefox Tools->Add-ons->Get Add-ons

---

### Post by DJonsson2008 on 2009-04-06
The Nvidia PCI-E card arrived and made a vast difference in the performance of this unit. I've since though developed an interest in Xbuntu but now with both Ubuntu and Xbuntu loaded on the same HD, can move between the 2 as appropriate.

Perhaps someone could tweak the intel drivers and jockey-gtk (AKA Hardware drivers) and displayconfig.gtk GUI's to get better response with the onboard video but you can read here in this wiki the Intel GMA has a weakness in how it impacts resources.

[http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

For 40$, this made a big difference.

Otherwise have found that using another browser Seahorse proves that my multiple Foxfire/Mozilla plugins are another factor in my  performance sluggishness in Firefox.

---

### Post by zcacogp on 2009-04-15
Chaps, 

Picking this one up again. Time is (as usual!) short, and I think that the 'playing-with-Ubuntu' project is going to be happening in dribs and drabs over time. 

The good news is that I just turned Ubuntu on (normally use XP on this machine) and it downloaded a bunch of updates, which is the second time it has done this. I rebooted and it seems a bit smarter after this, and I can now press a key on the keyboard and not wait for 0.2-0.5 of a second before the character displays on screen. (Yes, it really was that slow!) So, we are making progress. 

mgmiller, the top five processes listed with "Top" are as follows: 

User           %CPU            %MEM             COMMAND
root           8               4.5              Xorg
ogp            16              5.3              Firefox
ogp            3               0.9              gnome-system-mo
ogp            1               0.9              compiz.real

The Xorg one is very variable tho' - bringing up a window or two from the taskbar at the bottom of the screen and shrinking them again gets this up to between 40 and 50% very easily. 

The command you gave me in terminal told me this: 

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3300 Graphics

... which sounds like that which I am running in XP (in XP it lists as an ATI Driver, version 8.541.0.0, dated 23/9/08, with an ATI Radeon HD3300 Graphics card.) 

Hardware Drivers tells me that I am running a "3D-accelerated proprietary graphics driver for ATI cards". So it is an accelerated driver - same as in XP. In XP I have the acceleration backed off one notch from 'Full', which gives the best graphics performance, but I can't see an equivalent of this in Ubuntu. Is there one? 

Thanks also for the tips on how to get CTRL-C and CTRL-V working ...  that's helped a lot! 

I'll try the EHCI drivers and see if that makes any difference. I'll post back on here when I have done so. 

DJonsson - glad that the new video card worked for you. I am suspecting it is the ATI thing here which is causing my problems ... 

On another slight positive note, I have worked out how to make the top taskbar a bit smaller and the on-screen text smaller, so the whole screen looks less clunky. It hasn't made it any faster, but it has made it a bit more elegant to look at. I still don't view Ubuntu as a serious contender to Windows (it's a toy, and I boot to XP when I want to do some work), but I guess I am making progress. I suspect the next bit of progress will require buying another graphics card, which is a shame (Ubuntu was meant to be a very-low-cost bit of amusement for me!) 

Thanks again for your help. 


Oli.

---

### Post by zcacogp on 2009-04-15
3rdalbum, 

(As a seperate post, as this will be quite long!), dmesg gives me this: 

[I][    0.023184] ACPI: Checking initramfs for custom DSDT
[    0.260376] ENABLING IO-APIC IRQs
[    0.260602] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.303316] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 02
[    0.304019] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5812.26 BogoMIPS (lpj=11624539)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.388133] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 02
[    0.388154] Brought up 2 CPUs
[    0.388156] Total of 2 processors activated (11624.62 BogoMIPS).
[    0.388198] CPU0 attaching sched-domain:
[    0.388200]  domain 0: span 0-1 level CPU
[    0.388202]   groups: 0 1
[    0.388207] CPU1 attaching sched-domain:
[    0.388208]  domain 0: span 0-1 level CPU
[    0.388210]   groups: 1 0
[    0.388257] net_namespace: 840 bytes
[    0.388257] Booting paravirtualized kernel on bare hardware
[    0.388257] Time: 22:13:33  Date: 04/15/09
[    0.388257] NET: Registered protocol family 16
[    0.388257] EISA bus registered
[    0.388257] ACPI: bus type pci registered
[    0.388257] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.388257] PCI: MCFG area at e0000000 reserved in E820
[    0.388257] PCI: Using MMCONFIG for extended config space
[    0.388257] PCI: Using configuration type 1 for base access
[    0.388499] ACPI: EC: Look up EC in DSDT
[    0.397063] ACPI: Interpreter enabled
[    0.397070] ACPI: (supports S0 S1 S4 S5)
[    0.397084] ACPI: Using IOAPIC for interrupt routing
[    0.400556] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.400556] PCI: 0000:00:00.0 reg 1c 64bit mmio: [e0000000, ffffffff]
[    0.400556] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.400556] pci 0000:00:0a.0: PME# disabled
[    0.400556] PCI: 0000:00:12.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.400556] PCI: 0000:00:12.1 reg 10 32bit mmio: [fe02e000, fe02efff]
[    0.400556] PCI: 0000:00:12.2 reg 10 32bit mmio: [fe02d000, fe02d0ff]
[    0.400556] pci 0000:00:12.2: supports D1
[    0.400556] pci 0000:00:12.2: supports D2
[    0.400556] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.400556] pci 0000:00:12.2: PME# disabled
[    0.400556] PCI: 0000:00:13.0 reg 10 32bit mmio: [fe02c000, fe02cfff]
[    0.400556] PCI: 0000:00:13.1 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.400556] PCI: 0000:00:13.2 reg 10 32bit mmio: [fe02a000, fe02a0ff]
[    0.400556] pci 0000:00:13.2: supports D1
[    0.400556] pci 0000:00:13.2: supports D2
[    0.400556] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.400556] pci 0000:00:13.2: PME# disabled
[    0.400621] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.400628] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.400634] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.400640] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.400647] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.400702] PCI: 0000:00:14.2 reg 10 64bit mmio: [fe024000, fe027fff]
[    0.400741] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.400745] pci 0000:00:14.2: PME# disabled
[    0.400836] PCI: 0000:00:14.5 reg 10 32bit mmio: [fe029000, fe029fff]
[    0.400943] PCI: 0000:01:05.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.400946] PCI: 0000:01:05.0 reg 14 io port: [de00, deff]
[    0.400950] PCI: 0000:01:05.0 reg 18 32bit mmio: [fdee0000, fdeeffff]
[    0.400957] PCI: 0000:01:05.0 reg 24 32bit mmio: [fdd00000, fddfffff]
[    0.400966] pci 0000:01:05.0: supports D1
[    0.400967] pci 0000:01:05.0: supports D2
[    0.400981] PCI: 0000:01:05.1 reg 10 32bit mmio: [fdefc000, fdefffff]
[    0.400998] pci 0000:01:05.1: supports D1
[    0.400999] pci 0000:01:05.1: supports D2
[    0.401037] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.401039] PCI: bridge 0000:00:01.0 32bit mmio: [fdd00000, fdefffff]
[    0.401043] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.401075] PCI: 0000:02:00.0 reg 10 io port: [ee00, eeff]
[    0.401090] PCI: 0000:02:00.0 reg 18 64bit mmio: [fdfff000, fdffffff]
[    0.401101] PCI: 0000:02:00.0 reg 20 64bit mmio: [fdfe0000, fdfeffff]
[    0.401107] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff]
[    0.401128] pci 0000:02:00.0: supports D1
[    0.401129] pci 0000:02:00.0: supports D2
[    0.401131] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.401135] pci 0000:02:00.0: PME# disabled
[    0.401175] PCI: bridge 0000:00:0a.0 io port: [e000, efff]
[    0.401178] PCI: bridge 0000:00:0a.0 32bit mmio: [fda00000, fdafffff]
[    0.401181] PCI: bridge 0000:00:0a.0 64bit mmio pref: [fdf00000, fdffffff]
[    0.401237] pci 0000:00:14.4: transparent bridge
[    0.401241] PCI: bridge 0000:00:14.4 io port: [c000, cfff]
[    0.401245] PCI: bridge 0000:00:14.4 32bit mmio: [fdc00000, fdcfffff]
[    0.401250] PCI: bridge 0000:00:14.4 32bit mmio pref: [fdb00000, fdbfffff]
[    0.401261] bus 00 -> node 0
[    0.401267] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.401729] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.401891] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.401989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.416801] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416801] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416816] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.416863] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.416863] pnp: PnP ACPI init
[    0.416863] ACPI: bus type pnp registered
[    0.420563] pnp 00:0c: mem resource (0xe0000000-0xefffffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.420563] pnp 00:0d: mem resource (0xffff0000-0xffffffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.420563] pnp 00:0d: mem resource (0xfec00000-0xfec00fff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.420563] pnp 00:0d: mem resource (0xfee00000-0xfee00fff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.420563] pnp 00:0d: mem resource (0xfff80000-0xfffeffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.420563] pnp: PnP ACPI: found 14 devices
[    0.420563] ACPI: ACPI bus type pnp unregistered
[    0.420563] PnPBIOS: Disabled by ACPI PNP
[    0.420563] PCI: Using ACPI for IRQ routing
[    0.420563] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.428035] NET: Registered protocol family 8
[    0.428037] NET: Registered protocol family 20
[    0.428048] NetLabel: Initializing
[    0.428048] NetLabel:  domain hash size = 128
[    0.428048] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.428053] NetLabel:  unlabeled traffic allowed by default
[    0.428062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.428066] hpet0: 4 32-bit timers, 14318180 Hz
[    0.429879] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.429881]    actual entries 65620
[    0.429988] AppArmor: AppArmor Filesystem Enabled
[    0.430009] ACPI: RTC can wake from S4
[    0.432041] Switched to high resolution mode on CPU 0
[    0.432169] Switched to high resolution mode on CPU 1
[    0.436027] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.436029] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.436031] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.436036] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.436038] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.436040] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.436042] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.436044] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.436047] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.436049] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.436051] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.436053] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.436055] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.436057] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.436060] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.436062] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.436064] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.436066] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.436068] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.436070] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.436083] system 00:0d: iomem range 0xcea00-0xcffff has been reserved
[    0.436085] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.436087] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.436089] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.436092] system 00:0d: iomem range 0x6fee0000-0x6fefffff could not be reserved
[    0.436094] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.436096] system 00:0d: iomem range 0x100000-0x6fedffff could not be reserved
[    0.436099] system 00:0d: iomem range 0x6fff0000-0x7ffeffff has been reserved
[    0.471210] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.471213] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.471217] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfdefffff
[    0.471219] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.471225] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.471227] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.471230] pci 0000:00:0a.0:   MEM window: 0xfda00000-0xfdafffff
[    0.471233] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.471236] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.471239] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.471244] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.471248] pci 0000:00:14.4:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.471271] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.471274] pci 0000:00:0a.0: setting latency timer to 64
[    0.471281] bus: 00 index 0 io port: [0, ffff]
[    0.471282] bus: 00 index 1 mmio: [0, ffffffff]
[    0.471284] bus: 01 index 0 io port: [d000, dfff]
[    0.471286] bus: 01 index 1 mmio: [fdd00000, fdefffff]
[    0.471287] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.471289] bus: 01 index 3 mmio: [0, 0]
[    0.471291] bus: 02 index 0 io port: [e000, efff]
[    0.471292] bus: 02 index 1 mmio: [fda00000, fdafffff]
[    0.471294] bus: 02 index 2 mmio: [fdf00000, fdffffff]
[    0.471295] bus: 02 index 3 mmio: [0, 0]
[    0.471297] bus: 03 index 0 io port: [c000, cfff]
[    0.471298] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
[    0.471300] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
[    0.471302] bus: 03 index 3 io port: [0, ffff]
[    0.471303] bus: 03 index 4 mmio: [0, ffffffff]
[    0.471312] NET: Registered protocol family 2
[    0.484050] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.484274] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.484787] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.485028] TCP: Hash tables configured (established 131072 bind 65536)
[    0.485031] TCP reno registered
[    0.492081] NET: Registered protocol family 1
[    0.492173] checking if image is initramfs... it is
[    0.971542] Freeing initrd memory: 8017k freed
[    0.972314] audit: initializing netlink socket (disabled)
[    0.972331] type=2000 audit(1239833612.968:1): initialized
[    0.976263] highmem bounce pool size: 64 pages
[    0.976268] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.978232] VFS: Disk quotas dquot_6.5.1
[    0.978303] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.978387] msgmni has been set to 1748
[    0.978480] io scheduler noop registered
[    0.978482] io scheduler anticipatory registered
[    0.978484] io scheduler deadline registered
[    0.978492] io scheduler cfq registered (default)
[    1.804013] pci 0000:00:12.1: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    1.888028] pci 0000:01:05.0: Boot video device
[    1.888150] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    1.888172] pcieport-driver 0000:00:0a.0: found MSI capability
[    1.888197] pci_express 0000:00:0a.0:pcie00: allocate port service
[    1.888482] isapnp: Scanning for PnP cards...
[    2.242160] isapnp: No Plug & Play device found
[    2.271460] hpet_resources: 0xfed00000 is busy
[    2.271526] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.271656] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.272272] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.273963] brd: module loaded
[    2.274022] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.274125] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.274520] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.274525] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.274773] mice: PS/2 mouse device common for all mice
[    2.274887] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.274919] rtc0: alarms up to one month, hpet irqs
[    2.275034] EISA: Probing bus 0 at eisa.0
[    2.275051] Cannot allocate resource for EISA slot 4
[    2.275066] EISA: Detected 0 cards.
[    2.275069] cpuidle: using governor ladder
[    2.275071] cpuidle: using governor menu
[    2.275433] TCP cubic registered
[    2.275454] Using IPI No-Shortcut mode
[    2.275612] registered taskstats version 1
[    2.275705]   Magic number: 5:616:249
[    2.275732] tty ttyw5: hash matches
[    2.275849] rtc_cmos 00:05: setting system clock to 2009-04-15 22:13:35 UTC (1239833615)
[    2.275851] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.275853] EDD information not available.
[    2.276084] Freeing unused kernel memory: 424k freed
[    2.276131] Write protecting the kernel text: 2580k
[    2.276160] Write protecting the kernel read-only data: 940k
[    2.305418] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.412541] fuse init (API version 7.9)
[    2.508657] processor ACPI0007:00: registered as cooling_device0
[    2.508715] processor ACPI0007:01: registered as cooling_device1
[    2.718178] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.718194] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.718209] r8169 0000:02:00.0: setting latency timer to 64
[    2.718452] eth0: RTL8168c/8111c at 0xf8838000, 00:1f:d0:a3:ad:c5, XID 3c4000c0 IRQ 222
[    2.773688] usbcore: registered new interface driver usbfs
[    2.773711] usbcore: registered new interface driver hub
[    2.780967] usbcore: registered new device driver usb
[    2.795869] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.795916] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.795928] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.795971] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    2.796001] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02f000
[    2.809643] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.831178] No dock devices found.
[    2.856666] usb usb1: configuration #1 chosen from 1 choice
[    2.856692] hub 1-0:1.0: USB hub found
[    2.856703] hub 1-0:1.0: 3 ports detected
[    2.857950] SCSI subsystem initialized
[    2.870765] libata version 3.00 loaded.
[    3.064748] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.064763] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    3.064787] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    3.064806] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02e000
[    3.124115] usb usb2: configuration #1 chosen from 1 choice
[    3.124137] hub 2-0:1.0: USB hub found
[    3.124148] hub 2-0:1.0: 3 ports detected
[    3.200018] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.226126] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.226140] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.226174] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[    3.226201] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02c000
[    3.284118] usb usb3: configuration #1 chosen from 1 choice
[    3.284140] hub 3-0:1.0: USB hub found
[    3.284148] hub 3-0:1.0: 3 ports detected
[    3.368687] usb 1-1: configuration #1 chosen from 1 choice
[    3.388134] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.388143] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.388160] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[    3.388173] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02b000
[    3.448065] usb usb4: configuration #1 chosen from 1 choice
[    3.448083] hub 4-0:1.0: USB hub found
[    3.448091] hub 4-0:1.0: 3 ports detected
[    3.504517] usb 1-3: new full speed USB device using ohci_hcd and address 3
[    3.552144] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.552154] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.552170] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 5
[    3.552191] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    3.552210] ehci_hcd 0000:00:12.2: debug port 1
[    3.552229] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02d000
[    3.652017] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.652098] usb usb5: configuration #1 chosen from 1 choice
[    3.652118] hub 5-0:1.0: USB hub found
[    3.652125] hub 5-0:1.0: 6 ports detected
[    3.860175] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.860188] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.860206] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    3.860228] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    3.860246] ehci_hcd 0000:00:13.2: debug port 1
[    3.860267] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02a000
[    3.872059] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.872131] usb usb6: configuration #1 chosen from 1 choice
[    3.872151] hub 6-0:1.0: USB hub found
[    3.872158] hub 6-0:1.0: 6 ports detected
[    3.976158] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.976170] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    3.976189] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    3.976204] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe029000
[    4.036231] usb usb7: configuration #1 chosen from 1 choice
[    4.036409] hub 7-0:1.0: USB hub found
[    4.036419] hub 7-0:1.0: 2 ports detected
[    4.048016] usb 1-3: device not accepting address 3, error -62
[    4.104520] hub 1-0:1.0: unable to enumerate USB device on port 3
[    4.104528] usb 1-1: USB disconnect, address 2
[    4.141688] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.141786] scsi0 : pata_atiixp
[    4.141867] scsi1 : pata_atiixp
[    4.142781] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    4.142784] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    4.332966] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    4.332971] ata1.00: ATA-7: WDC WD3200AAKB-00UAA0, 00.02C01, max UDMA/100
[    4.332974] ata1.00: 625142448 sectors, multi 16: LBA48 
[    4.332990] ata1.01: ATAPI: PIONEER DVD-RW  DVR-115D, 1.13, max UDMA/66
[    4.349031] ata1.00: configured for UDMA/100
[    4.364920] ata1.01: configured for UDMA/66
[    4.520157] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKB-0 00.0 PQ: 0 ANSI: 5
[    4.526148] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-115D 1.13 PQ: 0 ANSI: 5
[    4.536096] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.536128] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    4.546107] Driver 'sr' needs updating - please use bus_type methods
[    4.551918] Driver 'sd' needs updating - please use bus_type methods
[    4.564082] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    4.576078] sd 0:0:0:0: [sda] Write Protect is off
[    4.576081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.582165] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.582170] Uniform CD-ROM driver Revision: 3.20
[    4.582185] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.582268] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    4.582277] sd 0:0:0:0: [sda] Write Protect is off
[    4.582279] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.582286] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.582295] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.582299]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    4.655644] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.848028] usb 1-1: new full speed USB device using ohci_hcd and address 5
[    5.017993] usb 1-1: configuration #1 chosen from 1 choice
[    5.091700] PM: Starting manual resume from disk
[    5.091703] PM: Resume from partition 8:7
[    5.091705] PM: Checking hibernation image.
[    5.091911] PM: Resume from disk failed.
[    5.120549] kjournald starting.  Commit interval 5 seconds
[    5.120559] EXT3-fs: mounted filesystem with ordered data mode.
[    5.280021] usb 1-3: new full speed USB device using ohci_hcd and address 6
[    5.446782] usb 1-3: configuration #1 chosen from 1 choice
[    5.448695] hub 1-3:1.0: USB hub found
[    5.450673] hub 1-3:1.0: 2 ports detected
[    5.740686] usb 1-3.1: new full speed USB device using ohci_hcd and address 7
[    5.848869] usb 1-3.1: configuration #1 chosen from 1 choice
[    5.928694] usb 1-3.2: new full speed USB device using ohci_hcd and address 8
[    6.037806] usb 1-3.2: configuration #1 chosen from 1 choice
[    8.868534] udevd version 124 started
[    9.158958] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.221284] shpchp: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[    9.221288] shpchp: shpc_init: cannot reserve MMIO region
[    9.221554] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.329689] ACPI: WMI: Mapper loaded
[    9.333882] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    9.364526] ACPI: Power Button (FF) [PWRF]
[    9.364597] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    9.396543] ACPI: Power Button (CM) [PWRB]
[    9.463261] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    9.463265] ACPI: Device needs an ACPI driver
[    9.463271] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.545915] parport_pc 00:09: reported by Plug and Play ACPI
[    9.545972] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.721894] Linux agpgart interface v0.103
[    9.805255] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.822825] [fglrx] Maximum main memory to use for locked dma buffers: 1653 MBytes.
[    9.822877] [fglrx]   vendor: 1002 device: 9614 count: 1
[    9.823308] [fglrx] ioport: bar 1, base 0xde00, size: 0x100
[    9.823320] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.823324] pci 0000:01:05.0: setting latency timer to 64
[    9.823998] [fglrx] PAT is enabled successfully!
[    9.824027] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[    9.927143] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.956929] usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04E8 pid 0x328F
[    9.962210] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.964138] usblp1: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x413C pid 0x5106
[    9.964156] usbcore: registered new interface driver usblp
[    9.999485] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.999504] HDA Intel 0000:01:05.1: setting latency timer to 64
[   10.317462] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.935551] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   11.859349] lp0: using parport0 (interrupt-driven).
[   11.941952] Adding 3903724k swap on /dev/sda7.  Priority:-1 extents:1 across:3903724k
[   12.487012] EXT3 FS on sda8, internal journal
[   13.165370] kjournald starting.  Commit interval 5 seconds
[   13.165625] EXT3 FS on sda9, internal journal
[   13.165631] EXT3-fs: mounted filesystem with ordered data mode.
[   13.510832] type=1505 audit(1239830026.732:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4039
[   13.656749] type=1505 audit(1239830026.880:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4044
[   13.656933] type=1505 audit(1239830026.880:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4044
[   13.785252] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.383616] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (2 cpu cores) (version 2.20.00)
[   14.383668] powernow-k8:    0 : fid 0x15 (2900 MHz), vid 0x9
[   14.383671] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xa
[   14.383673] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xc
[   14.383675] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xe
[   14.383676] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10
[   14.383678] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[   14.383680] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[   14.383681] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   14.852239] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   14.914232] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   14.914237] apm: disabled - APM is not SMP safe.
[   15.124274] ppdev: user-space parallel port driver
[   16.000523] Clocksource tsc unstable (delta = -133811718 ns)
[   17.508988] Bluetooth: Core ver 2.13
[   17.511174] NET: Registered protocol family 31
[   17.511184] Bluetooth: HCI device and connection manager initialized
[   17.511193] Bluetooth: HCI socket layer initialized
[   17.587957] Bluetooth: L2CAP ver 2.11
[   17.587971] Bluetooth: L2CAP socket layer initialized
[   17.621738] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.621750] Bluetooth: BNEP filters: protocol multicast
[   17.669036] Bridge firewalling registered
[   17.687084] Bluetooth: SCO (Voice Link) ver 0.6
[   17.687096] Bluetooth: SCO socket layer initialized
[   17.930922] Bluetooth: RFCOMM socket layer initialized
[   17.930954] Bluetooth: RFCOMM TTY layer initialized
[   17.930959] Bluetooth: RFCOMM ver 1.10
[   19.491688] NET: Registered protocol family 10
[   19.492734] lo: Disabled Privacy Extensions
[   20.680400] [fglrx] GART Table is not in FRAME_BUFFER range 
[   20.724109] [fglrx] CMM init INV FB MC:0xd0000000, length:0x8000000
[   20.724139] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.080944] r8169: eth0: link up
[   22.080963] r8169: eth0: link up
[   22.324333] NET: Registered protocol family 17
[   26.489412] hda-intel: Invalid position buffer, using LPIB read method instead.
[   32.624137] eth0: no IPv6 routers present
[  124.857077] ppdev0: registered pardevice
[  124.905077] ppdev0: unregistered pardevice
[  125.544223] ppdev0: registered pardevice
[  125.593075] ppdev0: unregistered pardevice
[  127.887146] ppdev0: registered pardevice
[  127.936026] ppdev0: unregistered pardevice
[/I]

(Needless to say!) this means nothing to me ... unless the "Unregistered pardevice" bits at the end are significant? 


Oli.

---

### Post by mgmiller on 2009-04-15
> User           %CPU            %MEM             COMMAND
root           8               4.5              Xorg
ogp            16              5.3              Firefox
ogp            3               0.9              gnome-system-mo
ogp            1               0.9              compiz.real

The Xorg one is very variable tho' - bringing up a window or two from the taskbar at the bottom of the screen and shrinking them again gets this up to between 40 and 50% very easily.

I think this suggests your video card is causing the problem. 

xorg, at idle with firefox, evolution, and  1 or 2 widows open, is running at 1 % cpu on my system, with an Nvidia geforce 8600 GT 256 MB ram.  If I start opening and closing windows, etc, it does not go above about 6-8%.

xorg, is responsible for your onscreen display and works closely with your video driver.  Since you are using ATI, it is not surprising that it is giving some problems.

Once you switch to Nvidia, I think you will see a very large difference.

AMD/ATI is slowly releasing source code for their cards so the Linux community can build a decent driver.  In the meantime, we are relying on their "binary blobs" which is the accelerated driver you are currently using.  As you can see, their Linux support can be "iffy".

The open source ATI driver, for example supports compiz effects.

By contrast, Nvidia does not release much data to the open source community, so the open source drivers are not as developed as the ATI ones.  
The only way to get compiz effects going is to install the proprietary driver.
The Nvidia "binary blobs", however, are very well done and Nvidia supports Linux very well.

Eventually, ATI may be the superior choice, because the community will have a chance to build us a really good driver.  Until then, Nvdia is the way to go.

---

### Post by crjackson on 2009-04-15
zcacogp,

Three key areas (provided you have no specific problems) directly affect your perceived performance.

1) Proper Video card drivers (not always available depending the model of your card)

2) Compiz or other compositing video manager (XP doesn't use this so turn it off if you are comparing with XP)

3) XP uses a prefetch cache. To have something similar in Ubuntu, open up a terminal and paste the following code:

```
sudo apt-get install preload
```

4) Make sure indexing is turned off. It's a HOG on most machines

There are many more performance tweaks but these are the most common and basic. If you video card isn't properly supported you will never be happy with Ubuntu's performance.

Equally supported hardware and equally tweaked OS's, Ubuntu runs nearly equal to XP-Pro. Some things are slower and some things are faster.

I suspect your main issue is video card related.

---

### Post by wookiehangover on 2009-04-15
This is a great thread and I can really relate.

I've been a linux user for almost a decade, but I ran into some real trouble a few years ago when I was gifted an HP Pavilion and immediately remove windows for Ubuntu. Everything was great for a while, especially for a computer with not enough ram and onboard video. I've been using this computer for a few years now, and I definitely feel your pain with onboard video woes. 

The best suggestion is to go with new video card in most cases. Even a modest, sub $50 card will make your system run a lot smoother. Just make sure that whichever card you choose has good linux drivers. All it takes is searching NewEgg, finding the video card you want and Googling "'card name' + ubuntu"

More RAM never hurts either.

---

### Post by DJonsson2008 on 2009-04-16
Much progress is noted here.

I found another slowdown on my system with a setting 
in my network settings, where I had attempted to link
my Windows LAN Workgroup to a domain name. The network
settings did not like this at all. This slowed things
down like getting a root terminal or any gksu or sudo su
task.

Removing this unavailable domain name from my network
settings sped things up quite a bit.

Ubuntu/ and especially Xbuntu is now running faster than XP for most things on this machine. 

Getting a new Video card has been a mixed blessing, although 
the card Nvdia 8400GS is clearly compatible with both the restricted and proprietary drivers, getting it to work has
been a bit difficult. The Vesa drivers with the Nvidia provides
much better performance than with the IBM onboard GPU Video
I was working with before.

I think the series 8 may be a little on the bleeding edge for 8.4 where with the 8.10 its supposed to be better, for now though I'm sticking with Hardy 8.4 LTS.

Preload is working well, the only layers of optimization I see
at this point is getting the nvidia drivers to work, and perhaps a faster hard drive with more cache. But even 8.4 on my WD 2MB cache/40 gig seems to be snappy for most desktop tasks.

---

### Post by zcacogp on 2009-04-17
Chaps, 

Thanks again for your input. 

Mgmiller - yes. Screen card is prime suspect, I think. So ... buy another one. Which is where I am wondering what to do - I was intending to build Ubuntu onto the machine as a free toy ... free software, and many happy hours spent getting to know it. But it's ending up costing me money! I may scour eBay and see whether there are some decent second-hand cards there, as I don't really want to spend money if I don't have to. I'll avoid ATI kit; any other pieces of advice? You speak of NVIDIA highly. I'll look out for one of those. (Ironically I had an NVIDIA built-in card in my last machine, which was replaced by the current machine!) 

crjackson, thanks. How do I turn off compiz, and how do I turn off indexing? (Indexing is always a pain in the neck. Google desktop was a great idea until people tried to run it, and realised it slowed their machines right down on account of the huge indexing overhead.) 

I have activated the prefetch cache, using your code, thanks. However it didn't make any noticable difference to the performance. Thanks anyway for trying. 

Wookiehangover (great name!) - I have a decent slug of RAM. I don't think this is the restriction. 

DJonsson ... I think it's the video card. Everything seems to come back to that. Ho hum. Better get my wallet out if I want to solve that one ... 


The other problem I am having is simply how to make Ubuntu work. I can make XP work pretty well - I know my way around it fine, and speak the language. Using Ubuntu is like I have just moved to Tokyo from London tho'. I don't know the language, I don't understand the alphabet, I don't know the customs. Something which is fine in London may cause massive offence in Tokyo, and I simply don't know what do to. Lots of people give me helpful instructions and I can follow them OK, but I don't understand what I am doing. I am reading the Beginners Guide to Ubuntu (linked to alot on these forums), but it's not getting me very far. (I am around 15 pages in and it's not terribly helpful.) Any suggestions? 

(For instance, I tried to listen to a radio station on the BBC website using Firefox on Ubuntu yesterday. I don't have Realplayer installed ... so I downloaded the Realplayer installation file, and now have something called 'realplayer11GOLD.bin' sitting on my desktop. If I was in XP I would double-click it and it would talk me through the install. In Ubuntu if I do this it tells me "There is no application installed for this file type". I just don't know where to start!) 


Oli.

---

### Post by mgmiller on 2009-04-19
> How do I turn off compizSystem > Prefrences > Appearance...go to the "Visual Effects" tab and click on "None".

> ... so I downloaded the Realplayer installation file,....This comes under the heading of living in Tokyo.....

As a general rule, as a newbie, don't download and install things from the Internet.  

What you want to do is use the Synaptic Package Manager to install all needed applications and codecs.  

If the app you are looking for is not there, you can usually add a trusted repository to it so it will be there.  In this case, for realplayer, you want to add the medibuntu repository.

Go here:   [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And follow the instructions for adding the gpg key and repository.  

To make things easier, I will give you the quick instruction set.

1) Add the repository and gpg key for Ubuntu 8.10 (Intrepid Ibex)

Open a terminal...   Applications > Accessories > terminal.
copy and paste the following line into the terminal and hit enter.  It will ask for your password, just give it your regular login password.  (You will not see anything echoed to the screen when you enter your password.)

This first bit of code adds the source repository to your package manager.
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```After it does it's thing, you will then cut and paste the following line of code to add the gpg key which tells Ubuntu that the repository is trusted...

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```After you hit enter at the end of that line, a bunch of stuff will scroll by.  When it's done and you have your name prompt back, just close the terminal.

**************************************************************************************************************************
As an aside, I know I could give the OP just a few more lines of "sudo apt get..." code in the terminal to install everything he needs, but I wanted to familiarize the OP with synaptic.  As a newbie coming from Windows, I wanted to use the terminal as little as possible.  Also, I know there is a gui way to add the repository and gpg info, but terminal is just so much easier for this.
*************************************************************************************************************************
Finally, to add the software you want, open the Synaptic Package Manager.
System > Administration > Synaptic Package Manager. Click the button that says "Search" (It has a binocular icon) and in the search dialog box that appears, type in the name of the application you want to add and click the search button.  In your first case, search for realplayer.  When you see it, right click it and select "Mark for Installation".  It that's all you want, you click the big green "Apply" check mark near the top left of the window.  If you want other things, you can search for and mark for installation all of them before hitting the "Apply" button.

Packages I recommend you install from here in addition to realplayer are as follows:

This first one is in the regular repositories, so it would work even if you don't add medibuntu as described above.

1) ubuntu-restricted-extras
(if you are using kubuntu, install the kubuntu-restricted-extras)
(if you are using xubuntu, install the xubuntu-restricted-extras)
This adds flash, java, mp3 playback and a bunch of other things.

2) libdvdcss2  
(allows playing DVD movies)

3) w32codecs 
    ( important.... install w64codecs   instead of w32codecs if you are using 64 bit Ubuntu)

4) acroread    
This adds the Adobe reader, which is more feature rich than the free open source pdf reader that is installed by default.

5) googleearth       
You will want to install the metapackage and the 4.3 and 4.3 data packages.

6) skype (if you want it)


Doing it this way, will keep all the applications and codecs updated along with the rest of your system automatically.


One final note. Because we are on the verge of an update from Intrepid to Jaunty, if you choose to update your 8.10 to 9.04, as part of the update process, the medibuntu repository will be disabled.  You need to turn it back on and tell it to use the newer jaunty versions.

AFTER THE UPGRADE...
To do this, go to System > Administration > Software Sources
Click on the "Third-Party Software" tab and look for the packages.medibuntu.org entries (there will probably be 2 of them)

On each of them in turn, left click it to select it, click again in the little check box at the beginning of the line to put in a check mark and then at the bottom of the screen click on "Edit"

On the "Distribution" line, change intrepid to jaunty, and click OK.

Once you have done this for both medibuntu entries, click "Close"  at the bottom of the window.  It may tell you that "The information about available software is out of date"  Just click on the "Reload" button.

This may take some time to close and may turn grey.  It is updating the repository information in the background.  When it is done, the window should close by itself.

You will be notified it there are any newer versions of installed software.  For example, if you installed google earth 4.3 in Intrepid, you will be upgraded to google earth 5.0 in jaunty.


Welcome to Tokyo.....

---

### Post by VastOne on 2009-05-01
> **zcacogp said:**
> Chaps, 

Thanks again for your input. 

Mgmiller - yes. Screen card is prime suspect, I think. So ... buy another one. Which is where I am wondering what to do - I was intending to build Ubuntu onto the machine as a free toy ... free software, and many happy hours spent getting to know it. But it's ending up costing me money! I may scour eBay and see whether there are some decent second-hand cards there, as I don't really want to spend money if I don't have to. I'll avoid ATI kit; any other pieces of advice? You speak of NVIDIA highly. I'll look out for one of those. (Ironically I had an NVIDIA built-in card in my last machine, which was replaced by the current machine!) 

crjackson, thanks. How do I turn off compiz, and how do I turn off indexing? (Indexing is always a pain in the neck. Google desktop was a great idea until people tried to run it, and realised it slowed their machines right down on account of the huge indexing overhead.) 

I have activated the prefetch cache, using your code, thanks. However it didn't make any noticable difference to the performance. Thanks anyway for trying. 

Wookiehangover (great name!) - I have a decent slug of RAM. I don't think this is the restriction. 

DJonsson ... I think it's the video card. Everything seems to come back to that. Ho hum. Better get my wallet out if I want to solve that one ... 


The other problem I am having is simply how to make Ubuntu work. I can make XP work pretty well - I know my way around it fine, and speak the language. Using Ubuntu is like I have just moved to Tokyo from London tho'. I don't know the language, I don't understand the alphabet, I don't know the customs. Something which is fine in London may cause massive offence in Tokyo, and I simply don't know what do to. Lots of people give me helpful instructions and I can follow them OK, but I don't understand what I am doing. I am reading the Beginners Guide to Ubuntu (linked to alot on these forums), but it's not getting me very far. (I am around 15 pages in and it's not terribly helpful.) Any suggestions? 

(For instance, I tried to listen to a radio station on the BBC website using Firefox on Ubuntu yesterday. I don't have Realplayer installed ... so I downloaded the Realplayer installation file, and now have something called 'realplayer11GOLD.bin' sitting on my desktop. If I was in XP I would double-click it and it would talk me through the install. In Ubuntu if I do this it tells me "There is no application installed for this file type". I just don't know where to start!) 


Oli.

Before buying a new card to replace your ATI HD3300 I do hope that you make sure you have the latest ATI 9.04 drivers installed.  I have this same card using it at HD settings and it flies

VastOne

---

### Post by DJonsson2008 on 2009-05-02
You don't have to go to the bank to get your hands on an Nvidia 
Series 7 card. You will want to check the Ubuntu Card compatibility list for exact fit. Even after checking that though I found my 8400 GS to be slightly out of scope for 8.4. It will work on a fresh install of 8.10 and 9.4 but on 8.4 it is a bit of a hassle to get working right unless you do a fresh install and even then. 

Whatever the case though attempt to get the ATI drivers loaded
and see if makes a difference, after about 1-3 hours though you
may find it simpler to buy a known and tested Series 7 or 8 card from Nvidia.

RealPlayer is a mixed blessing even on MS/Windows, for BBC listening on linux the BBC offers their Iplayer. The MythTV set of software for Ubuntu though seems to have internet radio, TV and video features that are likely better sculpted for Ubuntu. works great, XFmedia is a great little MP3 player. I heard 9.4 has some BBC functions builtin.

Also try Xubuntu which you can load on the same machine via synaptic, its become my prefered desktop. At first I would jump between Ubuntu and Xubuntu on the same machine now nearly 95%
of the time I simply run Xubuntu. Xfce's (AKA Xubuntu) App finder and XMmedia MP3 player have been the mix of elegance and functionality that I'm looking for in a desktop.

I suppose by now you have discovered boot up manager (bum) in 
synaptic, it allows some more control over services that are loaded at boot time.

Also if you have attempted setting up SAMBA you may try turning it off to see if perhaps something in its configuration is slowing network related items down. I found on one of my machines a faulty SAMBA set up was causing uneeded network activity that effected nearly every LAN and internet action.

There is a firefox plugin called FASTER FOX will allows you to toggle some network settings back and forth to eliminate some of those tweaks as possible performance boosters/sinks. I also use SwiftFox, which not sure I would recommend as it is a bit of a hassle to install, but it does add a little boost to browsing.

Towards getting some more understanding of the OS. On the internet you can down load a couple of a chapters of
"HOW LINUX WORKS". Chapter 3 How linux boots can be read in about 15-20 minutes. I also bought a copy of 'Ubuntu Unleashed' from Amazon UK which was on sale, its a big book 800 pages but I find just flipping through it over beer or coffee has been a big boost in getting some kind of comfort level with Ubuntu,
and highly leverages/integrates what time/experience I've spent hacking on Ubuntu/Xubuntu.

---

### Post by zcacogp on 2009-05-04
Chaps, 

Thanks for finding this thread and posting more useful answers on it. 

VastOne - do you mean to say that the graphics drivers on 9.4 are different to those on 8.10? I am on 8.10 and have yet to venture to 9.4 as I feel I am still only getting used to 8.10 maybe that's what I need to do. If I upgrade to 9.4 will I keep all the settings (and installed software) that I put onto 8.10? 

DJonsson, how do I attempt to get the ATI drivers installed? System > Hardware Drivers tells me that I am running an "ATI/AMD proprietry FGLRX graphics driver", and that this is activated. Should I be looking somewhere else, or for something else? 


Oli.

---

### Post by DJonsson2008 on 2009-05-04
zcacogp:

Curious what ATI card you have, PCI, PCI-E or onboard and
how many megs of RAM -- and if this is a new card if it 
had any noticable impact on your speed issues?

Whatever the case looks like you are fortunate enough to have your drivers recognized right off by Ubuntu, which is great that is  what you want. Some people jump out of the standard
interface in order to install beta drivers or later
editions but if you are served by the OS gui at this point,
there is little reason to hack any further.

---

### Post by Kubular on 2009-05-04
This sounds a LOT like the problem I'm having. Input devices are just SLOW. Chars are taking a noticable length of time to appear on screen and I'm having to type slowly to make sure it doesn't skip any. Mouse is slow too. Tried turning the sensitivity up and it just feels like it's on ice. It's lagging like a... well, it's lagging a lot.

I do get an error when I boot sda 1 and 3 fail to softreset? Something like that. I'll check the references when I restart again. I use an ATI Card HD 4850. Using the drivers from ATI's website. Inputs are slow no matter which driver package I use. The only difference with the ones from ATI's site is that gnome doesn't break when I use them.

Lots of RAM and plenty processor. Certainly for just running the desktop. However, I DO have a gigabyte motherboard. I have a feeling this may turn out to be a common denominator. I had trouble in XP with my Asus Xonar, turned out it was an issue with Gigabyte motherboards, Asus released a patch for the firmware. Could turn out not to be this at all ofcourse.

Oh and Video card is PCI-E Sapphire HD4850 Toxic, Xonar D2X is also PCI-E.

PS

I reported this as a bug the other day. Found an old report that sounded similar.
Bug #119084 in linux.

Might be worth anyone else suffering submitting a report too.

EDIT:

Just restarted and changed the HDD setting from Native IDE to SATA -> AHCPI?
Are there too many letters there?

Got softreset failed on ata1 and 3. BUT input devices seem faster. Mouse is not as smooth asI'd like and the keyboard is still lagging behind. But not by nearly as much. I can type at a fairly reasonble speed now and it doesnt miss _too_ many chars.

EDIT 2:

SUCCESS!

I flashed the BIOS and Ubuntu's now as fast as (you know it) a rat up a drainpipe. System Monitor is showing MUCH lower CPU usage that it was previously. My input devices are fine.

Gonna update the Bug Report, but I'll leave it open just for the sake of completeness. Also, incase flashing the BIOS doesn't have the same effect for everyone else they can jump on the same one.

---

### Post by zcacogp on 2009-05-05
DJonsson, the video card is a built-in job, part of the motherboard. The motherboard is a Gigabyte affair. I can look up some more specific details if that helps, or is that enough information? 

Kubular - interesting. Sounds like a very similar machine to mine! Can you give me more details about what you flashed the BIOS with? Presumably the latest version of the BIOS software, from the Gigabyte website? 

FWIW, I upgraded the system to 9.04 (JJ), and it has belped a little. It's still slow (noticably slower than running XP on the same machine), but a smidge quicker than 8.10 (II). Every little helps, and all that, and it is getting to the point of being usable so I'm getting happier. (Although a major improvement such as Kubular is talking about would be great!) 


Oli.

---

### Post by Kubular on 2009-05-05
> **zcacogp said:**
>  

Kubular - interesting. Sounds like a very similar machine to mine! Can you give me more details about what you flashed the BIOS with? Presumably the latest version of the BIOS software, from the Gigabyte website? 



Yeah, I used the @Bios app from Gigabyte, updated first then ran a check to see if there were any BIOS updates - found it, installed it. 

It has made a _major_ difference. Is a discreet video card though, as opposed to onboard. Be careful with flashing the BIOS though, if you install the wrong version or have it break midway through you won't be able to boot. You _could_ effectively brick your motherboard. I'm guessing you're comfortable with this though since you built your machine yourself, iirc.

---

### Post by zcacogp on 2009-05-06
Kubular, 

Thanks, and thanks for the PM as well. 

I did it. Flashed the BIOS. It worked. (Used the @BIOS thing, as you described, took a deep breath and pressed the "Go" button. This sort of thing gives me the willies, and shouldn't be done late at night after a few beers!) 

It has made a difference. I think. I didn't have much time to play around with it, but it feels crisper and the processor plots are showing less activity. I'll hopefully have more time for a bit more of a poke around this evening. The difference isn't *HUGE*, but it's significant, and each little step is an improvement. It's getting towards being a usable system now, which is definitely good news. 

So, thanks for your input. I'll see what future use brings, and may well post on this thread again if my befuddled perceptions of last night turn out to be false! 



Oli.

---

### Post by Kubular on 2009-05-06
If when you check again you're still having issues, it'd prolly be worth filing a bug report, they're a lot easier than I expected. There's a how-to here.
[http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

At least that way if it's an issue with the kernel or something it should get fixed. :)

---

### Post by zcacogp on 2009-05-08
Ha! It's amazing what you find out when you play around in here, isn't it? 

Playing around with the "Add to panel" command, I found an application called "CPU Frequency Scaling Monitor". 

Thinks I: "That looks interesting, let's put it on the panel". 

Upon installing it, I find that the CPU was throttled down to 1.0Gig. Kicking it up to 2.9Gig has made it run about three times quicker - it now goes like a raped ape.

Amazing!

So, I guess the question is how did the CPU frequency get scaled down so much? It's not a question I'm going to worry about too much, as I am very pleased that Ubuntu now goes as it should. 

Thanks for your help chaps! I'm now off to explore all the interesting custom animations I can now run which previously made the system run like cold treacle ... !

Do I need to 'close' this thread as it is now a solved problem? 


Oli.

---

### Post by chocolateboy on 2009-05-09
> **zcacogp said:**
> 
So, I guess the question is how did the CPU frequency get scaled down so much? It's not a question I'm going to worry about too much, as I am very pleased that Ubuntu now goes as it should. 


The "ondemand" governor should scale the frequency automatically, but it doesn't work on certain systems (mine included), so for the time being the "performance" governor must be used. See  [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/367739) and [here](http://jasondclinton.livejournal.com/72910.html) for more info.

---

### Post by zcacogp on 2009-05-09
Chcoclateboy, 

Thanks. I have it set to 'OnDemand' now, and it is sitting at 34% at the moment. I *think* I saw it notch up to something bigger yesterday, but am not sure. 

Maybe I ought to set it to 'Performance' and see how I get on with that. 


Oli.

---

### Post by mgmiller on 2009-05-09
I have been following this thread for a few days and I found it very interesting.  I have an AMD triple core 8750 black edition that seems to work well with the on demand setting.  

One thing to be aware of is that you need to monitor and set the scaling option for each core you have.  So in my case, I put 3 of the monitors in my top panel and set each for a different core.  Right click, select preferences and use the core drop down to select core 0, core 1, core2, etc. for each monitor.  You can watch the scaling go up and down and be distributed across all the cores.  If you only put up one monitor, you are only observing and changing the setting for that core, not the other(s).

You can set the scaling independently for each core, so you can have one set to run at 100% and the others set to on demand if you find some lag before the scaling kicks in.

---

### Post by zcacogp on 2009-05-10
mgmiller, 

Thanks very much for your long list of instructions. I have finally got around to trying all of them. They were helpful - thanks. I still need to understand what the package manager is, how you line up different sources for the package manager to search and the different means of installing stuff from the package manager (via the GUI or terminal etc), but I am making progress. 

My one point is that with this: > **mgmiller said:**
> Finally, to add the software you want, open the Synaptic Package Manager.
System > Administration > Synaptic Package Manager. Click the button that says "Search" (It has a binocular icon) and in the search dialog box that appears, type in the name of the application you want to add and click the search button.  In your first case, search for realplayer.  When you see it, right click it and select "Mark for Installation".  It that's all you want, you click the big green "Apply" check mark near the top left of the window.  If you want other things, you can search for and mark for installation all of them before hitting the "Apply" button.

... I wasn't able to install more than one thing at once. I 'searched', and selected packages I wanted to install (the *.pdf reader, for instance), but once selected it listed it on the left hand side of the screen and wouldn't let me search for any more packages. I ended up installing the packages one by one, closing and re-starting the package manager between each one. Not the end of the world, but it suggested that I am not understanding something (and the lack of understanding is the biggest irritation - I hate doing things without understanding what I am doing!) 

> **mgmiller said:**
> Welcome to Tokyo..... Thanks! For what it's worth, about three weeks after having arrived in Tokyo I am starting to enjoy it. Some way to go yet, but I think it's a promising place. 

[SIZE="1"](I have also just discovered both desklets and the desktop cube. OK, I know they are just toys, but they are pretty jolly cool!) 
[/SIZE]


Oli.

---

### Post by styven on 2009-05-10
Hi there,

The package manager basically gets your software for you and ensures that it is complete in respect to dependencies, and then installs it. The equivalent in Windows is the "install shield wizard".
If you want to install more than one app at a time, it does not get much easier than using applications/add-remove software. You just select each one you want then click apply. From here you can also change your source preferences. The above takes nothing away from synaptic, but add-remove cover most things.
I don't know if you have used the terminal to install software yet but once you have, using the various gui's will seem slow. If you want to know a couple of basic commands let us know.
To get you going try the following..........

sudo apt-get install k3b

enter your password when prompted.

this bit of software is a very good cd/dvd burning suite.

if it is not for you, simply do the following........

sudo apt-get remove k3b

enter your password when prompted.

Steve.

---

### Post by mgmiller on 2009-05-11
> ... I wasn't able to install more than one thing at once.That's odd.  After doing a search, right click the item and select "Mark For Installation".  You should then be able to go right back to the search button and search for something else and then mark it for installation, etc. till you have everything marked and then click Apply to install all of them.  Sometimes there is a slight delay till the "mark for installation" part finishes and you can get back to the search button, but on my system it's never more than a fraction of a second.  What happens if you give it a little time?  

You can experiment by searching for and selecting several packages at random.  Just don't click to "Apply" them and they won't install.

At the conclusion of the experiment, click on "Custom Filters" in the bottom left area and then click on "Marked Changes" in the list displayed above it.  Right click each of the items and select "Unmark".  This way you will be unmarking all the packages you had marked as well as all their dependencies.  

If you only go back and unmark the packages you searched for without doing the "Marked Changes" bit,  the unmet dependecies (think of them as extra files that the programs needed to run) would still be marked for installation.

Not everything you mark for installation will have these extra files, so you don't always see it.  When you do mark something for installation, if it needs extra files, it will show you what they are before you proceed.

---

### Post by gadolinio on 2010-03-21
> **mgmiller said:**
> Yes, I find that annoying also.  It's set that way by default to make it easier for coders to do stuff.  I am not a coder, so here is how you change to to use ctrl+c and ctrl+v:

Open a terminal window and at the top click on Edit > Keyboard Shortcuts

You will see the copy and past short cuts listed as the first 2.  Just click the one for cut once to high lite it then  click it again to change it to "New Accelerator..." and then hold down the ctrl key and click the letter c key and it should change to ctrl+c.

Do the same for paste and change it to ctrl v.

Thanks! That difference with the normal shortcuts was very annoying!

---

