---
title: "Ubuntu Jaunty Install Hangs"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by biggiemokey on 2009-05-05
Hey everyone, I have Ubuntu 8.10 in a dual boot with XP on my Dell XPS Gen 3 (Desktop).  Ubuntu 8.10 runs reasonably well (other than the seemingly unfixable noise problem) but I need a near perfect version of Ubuntu before I can fully switch to Linux and buy an Ubuntu laptop.  But I'm rambling.

When I try to install 9.04, the splash loading screen after you click install (on the Live CD) goes up to about 25% loaded and then freezes for about 10 minutes, after which it rapidly finishes.  Then it goes to a text screen and gets stuck on Starting Bluetooth, while Starting everything else has an [OK] next to it.  How do I get past this problem?  I think I hit Escape to exit the install, but even that didn't work as it was trying to close Bluetooth.  Help would be greatly appreciated.

---

### Post by Didius Falco on 2009-05-05
Did you hit Install from the first menu, or after booting the Live CD?

---

### Post by biggiemokey on 2009-05-06
I hit Install from the first menu, but booting to the Live CD didn't work either...it gave me the same error message.

---

### Post by k3lt01 on 2009-05-07
What are your system specifications, Jaunty seems to need more ram than Hardy and Intrepid do.

---

### Post by alxlabs on 2009-05-07
One of other forum members reported same issue (russian language, here is the  [link](http://www.razgovory.com/ru/forum/viewtopic.php?&p=496588#496588))

I found following after googling for a bit - 
[http://darinshaw.com/cs/blogs/darin/archive/2008/09/17/ubuntu-linux-boot-hangs-on-starting-bluetooth.aspx](http://darinshaw.com/cs/blogs/darin/archive/2008/09/17/ubuntu-linux-boot-hangs-on-starting-bluetooth.aspx)

Ubuntu boots normally after fix suggested in the article above was applied but seems there is a problem with specific set of h/w

Here is lsusb and lspci

alexl@ubuntu:~$ lspci 
00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2) 
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2) 
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1) 
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2) 
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1) 
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1) 
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2) 
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1) 
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1) 
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1) 
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1) 
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1) 
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) 
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) 
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) 
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) 
00:0e.0 RAID bus controller: nVidia Corporation MCP73 SATA RAID Controller (rev a2) 
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2) 
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0) 
02:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1) 
alexl@ubuntu:~$ lsusb 
Bus 001 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 004: ID 03f0:3d17 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by alxlabs on 2009-05-07
Here is the quotation..

[quote="darinshaw.com"]
The problem:

After installing Ubuntu linux on an Acer Aspire M1640 the boot sequence would hang at the Starting Bluetooth line.

 

The solution:

Add a "noapic" switch to the boot command line.

If you haven't installed Ubuntu yet, when the CD loads hit F6 (other options) and add "noapic" without the quotes at the end of the line.

Once Ubuntu is installed, on the boot screen hit ESC when it gives you the option to enter the menu. Select the kernel and hit 'e' to edit the options. Add "noapic" without quotes at the end of the line and hit enter. Then hit 'b' to finish booting with the new option. 

 

To make these changes permanent so you don't have to do this every time you boot:

Open the terminal and type "sudo gedit /boot/grub/menu.lst"

After the "END DEFAULT OPTIONS" line you'll see the boot menu and options. At the end of the "kernel" line place your "noapic" parameter at the end of the line and save the file.

Then to actually update the grub loader with your new information, in the terminal type "sudo update-grub".

[/quote]

---

### Post by biggiemokey on 2009-05-11
Thank you for all the replies

@alxlabs - that fix didn't work for me.  When I pressed F6, a little menu popped up with noapic and some other options.  I hit enter on noapic and a little x showed up next to it - I couldn't see how to get to the actual command line.  After trying with that little x next to noapic the same problem happened (hanging on Starting Bluetooth).

@k3lt01 - 2 GB RAM, 3.6 GHz Pentium 4.  2 GB is more than enough, right?

---

### Post by Bölvaður on 2009-05-11
> **biggiemokey said:**
> 2 GB is more than enough, right?

it's a overkill... on my laptop I have 512MiB and it doesn't need half of it... but it would still be sluggish at times with less than 320MiB, specially when you have multiple programs opened and editing photos in gimp.

If you have usb stick I recommend making a live cd from it with the option in 8.10 found in System&#8594;Administration&#8594;Create a USB startup disk

That will eliminate chances that the cd has data corruption.

If you do not have a usb stick to do that with then download the cd image again and make sure there was no corruption of data by doing the checksum.
Then burn it with a program that takes the checksum of it before and after burn to make sure there was no corruption. Burn at SLOW speed, like 4x


This is the only explanation I can give in your situation, only very old computers with bad cd drive or low ram does this, but only when it is far in the process, not this early.

---

### Post by mprince on 2009-05-11
You can check to make sure that the ubuntu CD doesn't have errors by booting with it and selecting 'Check disk for Defects' on the screen with the ubuntu logo.

---

### Post by biggiemokey on 2009-05-11
I did run the CD error check, that didn't seem to find anything...

Should I still make the USB startup disk?  I just don't think it will work and it's kind of a pain to get a USB drive right now.

---

### Post by mprince on 2009-05-11
The LiveCD is probably OK then.

This thread may help:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1151663](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1151663)

It is unclear if what was suggested worked, but it is probably worth a try.


Poster HyRax recommended renaming the bluetooth init script (effectively preventing it from starting). 
By booting into Recovery mode w/ the LiveCD. then running these commands

```

sudo mv /etc/init.d/bluetooth /etc/init.d/bluetooth_old
sudo update-rc.d bluetooth remove
```

Then:
```
sudo reboot
```

---

### Post by k3lt01 on 2009-05-12
> **biggiemokey said:**
> @k3lt01 - 2 GB RAM, 3.6 GHz Pentium 4.  2 GB is more than enough, right?That should be enough by a long shot. My 2 GB P4 only has 1 GB of RAM and it was ok with 2 GB of SWAP.

> **Bölvaður said:**
> it's a overkill... on my laptop I have 512MiB and it doesn't need half of it... but it would still be sluggish at times with less than 320MiB, specially when you have multiple programs opened and editing photos in gimp.I disagree, I do a bit of video type work and my Desktop needs its 1 GB Ram and 2 GB SWAP. My Laptop has had 512 MB of RAM and it desperately needs its 2GB of SWAP when I use Firefox and OpenOffice at the same time.

> **Bölvaður said:**
> This is the only explanation I can give in your situation, only very old computers with bad cd drive or low ram does this, but only when it is far in the process, not this early. Again I disagree, I had no problem installing 9.04 on my Laptop but my Desktop which is much younger and better equipped took days to get it onto, even after replacing the HDD.

I do agree with downloading the iso again and would suggest you download it via the Torrent option I find there is less chance of cd corruption with the torrent download.

---

### Post by biggiemokey on 2009-05-18
Stupid question but - how do I boot to recovery mode?  I booted up the CD and saw "Safe Graphics Mode" but no Recovery Mode - booting to safe graphics didn't give me a terminal...

And thanks for all the help hopefully this will work.  In the meanwhile I'll re-d/l the iso

---

### Post by biggiemokey on 2009-05-21
*bump* Please?

---

### Post by mprince on 2009-05-21
-

---

### Post by Nachowarrior on 2009-05-31
actually the original command that he was telling you i think is "noacpi" not 'napic' also on some machines you need to include 'pci=noacpi' so for instance on a socket A machine i would have to hit esc from the live cd then type in "live noacpi pci=noacpi" then hit enter to get it to run properly. However this did not fix the hang on "starting bluetooth" that i got as well. still hangs for me, i will try using the second method listed... and essentially you can just boot from the live cd and use terminal to run these commands i believe.

---

### Post by Nachowarrior on 2009-05-31
okay i've got the problem solved on my machine using only what's in this forum thread.

start your system normally only when it says "loading grub stage 1.5" or whatever hit the 'esc' key. You will then be able to choose from different kernals click the "generic recovery" one. it'll then load up several options. select one of the two that says "root shell" this is where you will type in these commands one at a time hitting enter after each line. do not include the dollarsign just the parts starting with "sudo".  This fixed it for me, no more hanging on bootup at the "starting bluetooth" section.

$ sudo mv /etc/init.d/bluetooth /etc/init.d/bluetooth_old
$ sudo update-rc.d bluetooth remove
$ sudo reboot

if this doesn't work for you then i dunno what to tell you i'm not really that knowledgeable with linux but i can get it to work if it's in front of me. 

thanks for all the input on this thread that helped me fix my problem.

---

### Post by biggiemokey on 2009-07-10
I'm sure the command will work for me, but how do I put it in?  I have 9.04 installed now, used the upgrade tool from 8.10, but I can't boot into it.  Still hangs on bluetooth.  Also, the splash screen, with the Ubuntu logo and loading bar, takes FOREVER!  I would like to try the command but how do I get to a terminal?  I can't boot from the Live CD.  I can't boot to Recovery Mode from GRUB - when I try there's a problem with my video card I think.  Don't know the exact message, have to check again.

---

### Post by biggiemokey on 2009-07-11
This is what booting into recovery mode says:

```
IRQ 17
[   12.731019] Installing spdif_bug patch: Audigy 2 ZS [SB0353]
[   14.164011] phy0: device does not respond!
```

I know Audigy 2 as in Audigy 2 SoundBlaster, my audio software...not sure if that's the name of the audio card as well.  So does that mean my audio card is the problem?  Any way to fix this?

---

