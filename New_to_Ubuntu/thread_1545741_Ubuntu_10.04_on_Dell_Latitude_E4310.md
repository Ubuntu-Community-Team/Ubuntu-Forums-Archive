---
title: "Ubuntu 10.04 on Dell Latitude E4310"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by tduccuong on 2010-08-04
Hi all,

I have got a new Dell E4310 and it comes with Windows 7 Pro preloaded. However I dont like Windows and want to install Ubuntu 10.04 on it. When I insert the DVD installation disk and turn on the laptop, the monitor shows normal process and suddenly it goes off. The laptop seems to freeze as it shows nothing, completely black. I have to hard-reboot by pressing the power button to come back to windows! I tried both the 32bit and 64bit versions, none of them worked. Can anyone give me a clue?

Thank you...
Cuong

ps: Sorry for my broken English!

update: I think the problem is with the new graphic card, I tried install OpenSuse 11, and with the failsafe option I was able to get to the graphical interface. Does anyone know if newest X11 driver works with this new Intel Graphic Card?

---

### Post by Zorgoth on 2010-08-04
Maybe your DVD drive isn't good?  Try a USB stick.

---

### Post by tduccuong on 2010-08-04
I tried both USB sticks and DVD. They didnt work at all! Any other suggestion? Thank you...

---

### Post by tduccuong on 2010-08-09
Does anyone else have the same problem with Dell E4310? Allo...

---

### Post by anewguy on 2010-08-09
I have no idea what video chipset you have - if you know could you please post it?  

In the mean time, if you know it to be an Intel 855 chipset, try the following (might work for others also - I don't know):

From the LiveCD:
1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6 and then Esc. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Press Enter to boot the LiveCD. 

From an installation:
1) Hold down Shift while booting to enter the GRUB menu. 
2) Press 'e' to edit. 
3) Add "i915.modeset=1" after "quiet splash". 
4) Ctrl+x to boot. 

If adding "i915.modeset=1" to your boot parameters allows you to boot successfully, you then need to make the change permanent. Let us know how it goes and we can tell you how to make it permanent if needed (no need posting now if it doesn't work for you).

Dave

---

### Post by tduccuong on 2010-08-10
hi Dave,

Thank you for your reply. Unfortunately it didnt work :( Well it got a little better with the "i915.modeset=1", I got to the Ubuntu Splash with the progress bar running. But after that the monitor just went black just like before!

Can you tell me how to get what the video chipset is so that I can post in here?

Cuong

---

### Post by rickye on 2010-08-10
hey, i had the same problem but with a latitude d505, typeing "i915.modeset=1" helped me, could you post how to make it a permanent

---

### Post by skomp on 2010-08-17
I own a Latitude E4310. The lspci gives 

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

for  the graphics adapter. It is running ubuntu 10.04, which I installed  from DVD without any problems. X runs flawlessly if compiz is not used  and freezes otherwise. Another problem is: The system freezes if I plug  an external monitor directly to the laptop. External monitor makes no  problem using the port replicator.

For the installation I didn't pass any kernel module parameters.

Currently I'm using proposed and unsupported updates.

So basically the driver works but there are some things that still seem broken.

Hope that helps,

regards, skomp

---

### Post by tduccuong on 2010-08-18
Hi Skomp,

What DVD do you mean? Did you download the ISO and burn to DVD? If so can you tell me which ISO did you download, or point me to the right place where I can get the DVD? Thank you.

Regards,
Cuong

---

### Post by skomp on 2010-08-18
Actually it was the simple and stupid ISO download. Maybe it helps if i tell you: 32bit, so the x86 build was what I installed.

edit: the 10.04 ISO I wanted to add :)

---

### Post by tduccuong on 2010-08-18
Its weird because I started first with the 32bit version. Then I realize that my preloaded Windows 7 is 64bit, so I thought lets download the 64bit ISO. But it didnt work too!

I dont understand, my E4310 features Intel core i5 proccessor, 8GB Ram and 500GB harddisk. Is there any difference to yours?

Regards,
Cuong

---

### Post by Kixtosh on 2010-08-18
I'm just wondering, have you verified your ISO image download with MD5?
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by tduccuong on 2010-08-19
I did not! But with this same ISO, I had no problem installing it on my Lenovo Ideapad S12. Also for the Dell, I tried several other Linux flavours e.g., OpenSuse, SystemRescueCD, PuppyLinux,... They did not work too, eventhough they are all at their newest version. The same problem happened at the time the graphic screen is about the start. All go black and the computer hangs...

Regards,
Cuong

---

### Post by skomp on 2010-08-20
The difference seems to be minimal, i got 4 GB ram and 250 GB HD and also the core i5. 

this is my full lspci output:

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation Device 3b57 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by tduccuong on 2010-08-26
Since I cannot get to a running Linux-based OS on my Dell, I dont know how to get my own lspci. So I went into the BIOS page, and wrote down these info. Hope that may help someone in here analyze:

System Information
BIOS = A03
Service Tag = 1MPRQM1
Asset Tag = {none}
Ownership Tag = {node}
Manufacture Date = 07/26/2010
Ownership Date = 08/04/2010

Processor Information
Processor Type = Intel(R) Core(TM) i5 CPU M540@2,53GHz

Memory Information
Installed = 8192MB
Available = 8120MB
Speed = 1067MHz
Channel Mode = Dual InterLeave
Technology = DDR3 SDRAM
DIMM A Size = 4096 MB
DIMM B Size = 4096 MB

Device Information
Video Controller = Intel GMA HD
Video BIOS Version = 1994v24
VIdeo Memory = 32MB
Panel Type = 13,3" HD
Native Resolution = 1366x768

Audio Controller = IDT 92HD81


@Skomp: Can you pls check if any BIOS info difference to ur laptop? Thanks...

Regards,
Cuong

---

### Post by tduccuong on 2010-08-31
hi, 

Problem solved! Turns out the external monitor was connected at the time the laptop was booting with the LiveCD. Ubuntu 10.04 could not detect the monitor right so the laptop just hung. However with the DVI connector everything went smooth.

@Skomp: Did you find a way around the Mic issue? The internal mic doesnt work at all...

Regards,
Cuong

---

### Post by mdvz0r on 2010-09-08
> **tduccuong said:**
> hi, 

Turns out the external monitor was connected at the time the laptop was booting with the LiveCD. Ubuntu 10.04 could not detect the monitor right so the laptop just hung. However with the DVI connector everything went smooth.



I've got exactly the same problem with my DELL E4310

Specs:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation Device 3b57 (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series/3400 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```This is really annoying when giving presentations etc. Does anyone know about a solution? 

Regards,
mdvz0r

---

### Post by skomp on 2010-09-09
Actually I didn't try to use the internal Mic so far. But as you me pointed that out to me I tried it and yes, its not working correctly. I'll have try configuring that and tell you if I found any Solution.

For the VGA Problem I didn't find find any solution, too. I think I might be trying building my own kernel and grab a set of graphics drivers from CVS or git or whatever they use. There has to be a solution for this. The situation for presentations really pisses me off, too. I didn't get a laptop for carrying around the docking station everywhere I go and hope they have a DVI  beamer...
 
Regards
skomp

---

### Post by mattlach on 2010-09-11
> **tduccuong said:**
> hi, 

Problem solved! Turns out the external monitor was connected at the time the laptop was booting with the LiveCD. Ubuntu 10.04 could not detect the monitor right so the laptop just hung. However with the DVI connector everything went smooth.

@Skomp: Did you find a way around the Mic issue? The internal mic doesnt work at all...

Regards,
Cuong

Your E4310 has a DVI connector?   Mine only has a traditional analog VGA connector.  Are you using an adapter?  Please let me know.

Thanks,
Matt

---

### Post by borth92 on 2010-09-11
try the alternate install iso and report how it works

---

### Post by skomp on 2010-09-13
> **mattlach said:**
> Your E4310 has a DVI connector?   Mine only has a traditional analog VGA connector.  Are you using an adapter?  Please let me know.

Thanks,
Matt
No, it does not have a DVI connector, but the docking station has two of them. I'm not using any adaptor.

So far I didn't get the internal Mic to work.

Unfortunately I can not just reinstall the system, so using the alternate install DVD is out of scope. The system is in productive use despite all problems. For every day work that's OK.

Regards
skomp

---

### Post by skomp on 2010-10-01
I just updated to 10.10, external monitor via VGA works with that. Unfortunately I'm having trouble with a flickering laptop monitor (with and without a secondory monitor connected).

---

### Post by xycmu on 2010-10-19
> **skomp said:**
> Unfortunately I'm having trouble with a flickering laptop monitor (with and without a secondory monitor connected).

I have the same problem and following the thread:
[http://ubuntuforums.org/showthread.php?t=1559264](http://ubuntuforums.org/showthread.php?t=1559264)

Only a temporary fix has been identified (page 3 of the thread)

---

### Post by etienne.mon on 2010-10-22
Hello,
I have seen your post. Here is my problem, may be you can help me
I am quite a beginner in ubuntu. I am sorry to post such a thread but I did not find a solution.
I bought an Dell Latitude E4310 with video card intel GMA HD.
When I start ubuntu 10.04 on a usb key not problem eth0, wifi and even the integrated webcam works!
Then I decide to install it on the whole disk. Everything was ok, but  when I restart I get a black screen and I hear the little music that  means that I am on the login window. 
What is really funny is that if I put an externa screen on the VGA port,  it is detected so that I can do everything on this external screen. 
The amazing thing is that if I remove the plug, the internal screen of  my labtop works fine and I can do everything without any problems...
Is there any way to get the internal screen be detected by default ?

I also try the i915.modetest=1 but it does not work
 I am quite lost.
Etienne

---

