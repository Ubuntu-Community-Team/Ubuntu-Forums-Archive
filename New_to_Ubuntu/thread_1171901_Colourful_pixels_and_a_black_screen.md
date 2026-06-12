---
title: "Colourful pixels and a black screen"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by gwolff on 2009-05-27
Hi, I'm new to Ubuntu and I have a problem. 
I was running XP and downloaded and burnt the 9.04 iso. I booted from disk but every time I either tried to just run the live CD or install it would go to a loading screen and then go black with colourful pixels at the top of the screen and freeze there.

After some searching I found [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters) and by deleting quiet splash-- and putting acpi=off I was able to boot and run the live CD.

I then installed from within the live CD and it told me to restart but upon restarting I still come to a black screen with colourful pixels at the top. Boot Parameters told me I would have to make permanent changes in the file /boot/grub/menu.lst after the installation has completed but I'm not sure how to get there or what changes to make.

Your help would be appreciated.

---

### Post by chickenlinux on 2009-05-27
On bootup, for the Grub loader, there should be a few messages at the bottom. One of them should be something like "Press 'n' to enter bootup parameters" (I dont' know if it's n, I forgot what it is, sorry :( It should say though) then you just enter what you had to do to boot the liveCD.)

If that doesn't work for you, burn yourself a recovery disk, mount your hard drive, and open /boot/grub/menu.lst and edit it with vi or textedit or some other pure text editor of your choice.  I'm a slacker myself... (LILO, not grub... :P) It should have a section, I would guess, that has something like

#Put your boot params on this line!
boot_params: (just type them here)

Does that help?

---

### Post by BZF on 2009-05-27
[SIZE=1][COLOR=Blue]can i have the specs? it would help because then i can see if its ur computer[/COLOR][/SIZE]

---

### Post by chickenlinux on 2009-05-27
> **BZF said:**
> [SIZE=1][COLOR=Blue]can i have the specs? it would help because then i can see if its ur computer[/COLOR][/SIZE]

Well, if it worked with the Live CD after he passed the params to it, it's just a problem with the GRUB loader getting the params, not a problem with the computer. He'll just need to edit the file so it has them, or enter them at boot.

---

### Post by gwolff on 2009-05-27
I'm running an AMD 64 athlon CPU, Soyo dragon k8usa motherboard, ATI sapphire 2600 pro, and 2GB ram

---

### Post by BZF on 2009-05-27
[SIZE=1][COLOR=Blue]ATI graphics cards usually don't work right for ubuntu OS's. get nVidia, always will work[/COLOR][/SIZE]

---

### Post by anewguy on 2009-05-27
Right now I wouldn't worry about switching video cards.  Do as was suggested earlier by another poster:

at boot, watch the screen closely.  It will tell you to press ESC (I think that's what it is in Ubuntu - haven't had to reboot in a long time). Then follow the screen - it should give you the choice of what you want - try recovery mode.  That should get you a text-based window and a log on prompt.  Log on with your normal user name and password, then type the following:

cd /boot/grub <press enter>  This will change the default directory (folder in GUI terms) to /boot/grub

sudo cp menu.lst menu.lst_good <press enter>  When asked, just enter in your normal password.  This will save a copy of the existing file so if you get it messed up too much you can always restore it.

sudo vi menu.lst <press enter>  This should open the menu.lst file for editing, but be forwarned: vi is not what could be termed a "normal" editor by any means, and it requires a knowledge of commands to work with.

At this time it probably says something like "Press enter to continue editing menu.lst" or some such thing at the bottom of the window - just press enter.

Using the page down key, scroll down until you see a section something like this:

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=d15db333-4f39-4ca2-8474-33e7720fc0a9 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            d15db333-4f39-4ca2-8474-33e7720fc0a9
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Now use the arrow keys to position the cursor on the space before the word "quiet" on the first "kernel" line.

Press the delete key until "quiet splash" have been removed.

Press the insert key.

type:
<spacebar>ACPI=off

Press the ESC key.

Hold down the shift key and press ":" (no quotes).  You will see a little ":" at the bottom of the screen

type:
write<press enter>

Hold down the shift key and press ":" (no quotes).  You will see a little ":" at the bottom of the screen

type:
quit<press enter>

This should return you back to the command prompt.  Type:

sudo shutdown -r now<press enter>  type your regular password if prompted.  This tells the system to shutdown now (basically kill all processes without waiting) and "r"eboot.

Let us know if you at least get to the gui screen now - then we can work on seeing if there is a driver for your video card or not.

Dave :)

---

### Post by gwolff on 2009-05-28
Okay I did that and upon startup it brings me to a black screen again with a few pixels at the top.

---

### Post by anewguy on 2009-05-28
At that screen, hold down Ctrl Alt and press F1.  This will get you to another terminal window.  Log on as before, then type the following:

lspci<press enter>  This will list all known pci devices on your system.  This will help us identify what video adapter and chip set you are using.

Copy and paste the output from that back here.

Type:

cat /boot/grub/menu.lst<press enter>  Post back the output here beginning with the ## ## End Default Options ## line to the end.  Just want to be sure how your boot looks.

exit<press enter> to close the terminal window.

It's interesting you could get it to work with the same parameters in your testing, but it didn't work otherwise.  I think you can also add something like vga=744 or some such number on the boot line, but right now I don't remember the exact number combinations.  Perhaps someone else can post those back if I can't fine them.

Dave :)

EDIT:  the option would be vga=771  You could put this on the same kernel line you edited before and then try rebooting.

---

### Post by gwolff on 2009-05-31
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 20)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 03)
00:0e.0 IDE interface: ALi Corportation M5229 IDE (rev c5)
00:0f.0 USB Controller: ALi Corportation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corportation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corportation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corportation USB 2.0 Controller (rev 03)
00:18.0 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Orteron] HyperTransport Technology Configuration 
00:18.1 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Orteron] Address Map
00:18.2 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Orteron] DRAM Controller
00:18.3 Host Bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Orteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 PRO AGP [Radeon HD 2600 PRO AGP]
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
02:0c.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6122 Gigabit Ethernet Adapter (rev 11)

---

### Post by gwolff on 2009-05-31
## ## End Default Options ##

title         Ubuntu 9.04, Kernel 2.6.28-11-generic
uuid         b6d6644a-94c4-480c-a070-53d5482b53f7
kernel      /boot/vmlinuz-2.6.28-generic root=UUID=b6d6644a-94c4-480c-a070-53d5482b53f7 ro acpi=off vga=771
initrd       /boot/initrd.img-2.6.28-11-generic
quiet

titile        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        b6d6644a-94c4-480c-53d5482b53f7
kernel     /boot/vmlinuz-2.6.28-11-generic root=UUID=b6d6644a-94c4-480c-a070-53d5482b53f7 ro  single
initrd       /boot/initrd.img-2.6.28-11-generic

title         Ubuntu 9.04, memtest86+
uuid        b6d6644a-94c4-480c-a070-53d5482b5f7
kernel     /boot/memtest86+.bin
quiet

## END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by gwolff on 2009-05-31
It will boot up now but the colours are all distorted and I can't tell where anything is.

When booting up I get an error that says: 

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) AIGLX error: Calling driver entry point failed(EE)
AIGLX: reverting to software rendering

---

### Post by anewguy on 2009-05-31
Well, the next step I would try is envng.  Use synaptic package manager to install it, then look under applications to find it and run it.  It has been a while, but I think it gives you the option of uninstalling your current driver - you should probably do that, then be sure to select the option to install the ATI drivers.  ATI's driver support has changed, so it may not support your card, but it's worth a shot.

Let me know what happens.

Dave :)

EDIT:  just realized I dropped a y in the spelling - it's envyng

---

### Post by gwolff on 2009-06-01
Where do I find envyng? With the colour distortion I can make my way around applications but not read the words very well. It kinda looks like a rainbow exploded on the desktop.

---

### Post by anewguy on 2009-06-01
Ahhh, sorry about that.  This is what I would try:

open a terminal window

type:

sudo apt-get install envyng<press enter>  This should install envyng.

When it finishes installing, type:

sudo envyng -t<press enter>  If I remember correctly this is how to start envyng in terminal mode.  Be sure to tell it to remove your old driver and also that your want the ATI driver installed.

When that finishes, type:

sudo shudown -r now<press enter> and wait for the system to reboot.  Let us know if it helps or not, or if you have any questions.

Dave :)

---

### Post by gwolff on 2009-06-01
It says:
E: Couldn't find package envyng

---

### Post by anewguy on 2009-06-01
Try envyng-core instead and see if that works.

Sorry
Dave :)

---

### Post by gwolff on 2009-06-02
Same thing, couldn't find package.

---

### Post by anewguy on 2009-06-03
EDIT:  removed original text, added the following:

I did a little searching and appears their may not be direct support for your video card anymore.  Please see this link and then perhaps open a post with "9.04 ATI RV630 - HELP!" and see if someone with experience directly on that card can help you.  It may be that you might need to try installing 8.04 instead of 9.04 - I'm really out of ideas here myself, and opening a thread with that specific title might get you better help.

Sorry I could not help you more!

Dave :)

---

### Post by gwolff on 2009-06-05
Thanks very much Dave. I appreciate all the help you have given me. I would have been more then lost without you.

Greg

---

