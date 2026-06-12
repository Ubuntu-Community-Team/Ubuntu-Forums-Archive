---
title: "Ubuntu Won't shut down completely"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by landy rover on 2009-07-15
**Hi everyone):P**
 
**i have ubuntu 8.10 intrepid ibex installed for two weeks already but i am having dufficulty with shutting down because when i press shut down the bar only goes halfway and then i just see a white line flasing then my pc power is still running.**
**when i had xp or vista or the other windows it shut down completely.**
**i like the funcionality of ubuntu and actully everything about the great OS but just have the shut down problem that is putting me off about ubuntu can anybody help?**
 
**apm=power off command line i tried in boot modules.lst but no luck:KS**
 
**LINUX ROCKS !!!!:guitar:**

---

### Post by marcopalla on 2009-07-15
I haven't understood if does it work terminal command

# sudo poweroff

?

---

### Post by themusicalduck on 2009-07-15
It might be worth trying to shutdown from the command line to see if any weird messages come up.

Save anything you're doing and then press ctrl+alt+f1 and then login.
At the command prompt type sudo shutdown -h

Hopefully it'll give you a rundown of what's happening when it shuts down and you can see if it stops on any particular message.

---

### Post by marcopalla on 2009-07-15
just in case.... 
if you push your power button for 5 seconds the pc power will turn off (of course is not a sweet shutdown... so is not suggested)

---

### Post by koleoptero on 2009-07-15
> **themusicalduck said:**
> It might be worth trying to shutdown from the command line to see if any weird messages come up.

Save anything you're doing and then press ctrl+alt+f1 and then login.
At the command prompt type sudo shutdown -h

Hopefully it'll give you a rundown of what's happening when it shuts down and you can see if it stops on any particular message.

I did this and figured that my laptop had some issues with the bluetooth packages, so I removed them and fixed the incomplete shutdown problem for myself.
You should try to see where the shutdown stops responding too.

---

### Post by landy rover on 2009-07-15
thank you so much everyone i tried shut down through the command line by typing in sudo shutdown -h and the ctrl+Alt+f1 command and then sudo shutdown -h there but all i seem to manage is to press the power button for 5 seconds ..

all my friends at their shutdown their status bar goes 100% then it shuts down mine goes 50% then it give's me that flashing light they told me i must se my BIOS to factory settings and that i've done but no luck 

THANX everybody but can it maybe be a hardware problem????????:guitar:

gigabyte motherboard
3.01ghz intel single core prosseser
256mb ati ddr3 graphics card 
1.5gig ram:KS

---

### Post by landy rover on 2009-07-15
i also tried to disable my graphics card and tried to shutdown completeley but no luck?:lolflag::p

---

### Post by themusicalduck on 2009-07-15
I did a bit of searching and it seems like a lot of posts say adding acpi=force onto the kernel line of the grub menu.lst can fix the problem.

If you don't know how to do this then follow these steps:

Open up a terminal from Applications > Accessories > Terminal.

Make a backup of your grub menu.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

It'll ask you to enter your password then hit enter. Then type:

```
sudo gedit /boot/grub/menu.lst
```

A text file will appear. Scroll down pass all of the commented text until you find a line near the bottom that will look something like this:

```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
```

Under that line look for another line that starts with kernel and at the end of that line add "acpi=force" with no quotes and a space before it.

So that it looks something like this:

```
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=0340f345-e195-4822-8635-e932308edd1b ro quiet splash vga=773 acpi=force
```

Reboot. It might not work straight away so you'll probably have to switch it off the first time, but hopefully it'll work after the second time switching it on.

---

### Post by landy rover on 2009-07-16
[B]hi everyone:)

i tried to add acpi=force to boot/menu.lst but i think I may have found the problem maybe?
while i was in ubuntu i added acpi=force to boot menu .lst and then I Went to the shutdown menu and said log off...then at the login screen i said shut down there and when you shut down that way it says: 
stopping GNOME Display Manager                          [OK]
Stopping services                                                     [OK]
Stopping Alsa Mixer                                                 

then after ten-twenty minutes it doesn't say   [OK]

Can It Not be the Alsa Driver that is causing the problem??????????


Thanx You Everybody for your Help :D:D[/B]**:D:D**

---

### Post by landy rover on 2009-07-16
> **themusicalduck said:**
> I did a bit of searching and it seems like a lot of posts say adding acpi=force onto the kernel line of the grub menu.lst can fix the problem.

If you don't know how to do this then follow these steps:

Open up a terminal from Applications > Accessories > Terminal.

Make a backup of your grub menu.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```It'll ask you to enter your password then hit enter. Then type:

```
sudo gedit /boot/grub/menu.lst
```A text file will appear. Scroll down pass all of the commented text until you find a line near the bottom that will look something like this:

```
title        Ubuntu 9.04, kernel 2.6.28-13-generic
```Under that line look for another line that starts with kernel and at the end of that line add "acpi=force" with no quotes and a space before it.

So that it looks something like this:

```
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=0340f345-e195-4822-8635-e932308edd1b ro quiet splash vga=773 acpi=force
```Reboot. It might not work straight away so you'll probably have to switch it off the first time, but hopefully it'll work after the second time switching it on.


[B]i tried to add acpi=force to boot/menu.lst but i think I may have found the problem maybe?
while i was in ubuntu i added acpi=force to boot menu .lst and then I Went to the shutdown menu and said log off...then at the login screen i said shut down there and when you shut down that way it says: 
stopping GNOME Display Manager                          [OK]
Stopping services                                                     [OK]
Stopping Alsa Mixer                                                 

then after ten-twenty minutes it doesn't say   [OK]

Can It Not be the Alsa Driver that is causing the problem??????????


Thanx You Everybody for your Help :grin::grin:[/B]**:grin::grin:**

---

### Post by JasonHippy on 2009-07-16
Afternoon all, 
I've been messing about with Ubuntu and a few other flavours of Linux for a few months now, basically trying out various live CDs to get a feel for Linux.

I recently installed Ubuntu 9.04 on my RM Tablet PC. It's fully up to date, I've installed a few little extras (VLC media player, blender, g++, Idle and the wxPython libraries). Certainly nothing that should've caused any problems. But whenever I attempt to shut the system down, the system appears to shut down, but the battery light stays on. Then a few seconds later the PC restarts itself....Very odd!

I've tried using acpi=force in /boot/grub/menu.lst, but with no luck. At the moment, the only way I've found to get the PC to shut down is by waiting for it to do one of it's weird restarts, pressing esc to get into GRUB, opening up a command-line and entering 'halt'...which isn't ideal!

I don't think it's a hardware issue or bios setting as Windows XP (which I've got on a separate hard-drive) can actually shut the system down with no problems.

Note: This isn't a dual boot, I have two small-ish hard-drives, but I only have enough space in my tablet PC for one drive. So my plan is to use the Ubunbtu drive for everyday use, but I can also remove it and insert the XP drive in those rare instances when I need to boot into Windows for something...

Bizarrely, if I boot the tablet PC using a Ubuntu LiveCD the system seems to be able to shut down with no problems...It seems that the native install just won't shut down at all (apart from the GRUB thing)!

Anybody got any ideas??

I've also noticed some gfx issues...These are probably slightly off-topic, but I'll mention 'em anyway....

Under Windows I can run 3D apps like Blender with no problems on the Tablet, but under Linux the display is seriously messed up (loads of noise on the screen) and eventually the system crashes (display freezes and the system won't respond to any form of stimuli!). 

Likewise in windows, VLC will play .AVI and .FLV files with no problems, but in Linux I get a few seconds of playback before the display freezes and the system becomes completely unresponsive.

The onboard gfx card is an integrated Intel VGA compatible 82852/855GM (rev 02). 
The graphics seem fine for most things, but anything involving video or openGL in Linux seems to be out of the question at the moment. I'm assuming that it's probably a driver issue or a bug somewhere else in the system.

Anybody know of any workarounds??

Cheers for now,
Jas.

---

### Post by themusicalduck on 2009-07-16
landy rover, the only info I can find that sounds like it relates to your problem is this bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/274995](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/274995)

Apparently the problem is something to do with the network manager, so to see if it's the same problem you could try disabling networking, or unplugging any ethernet cables/disconnecting wireless and see if you can shutdown after that.

There are some fixes listed on the bug report which might help to fix it, although it's possible that the bug has already been fixed in 9.04. So upgrading might help, though if you'd rather not there's bound to be something else you can do.

JasonHippy, not sure about the shutdown problem, but your graphics might be down to the poor Intel graphics support that 9.04 has at the moment. It might be worth booting into an 8.10 live CD to test and see if you have the same problems.

EDIT: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) might be worth reading too for JasonHippy.

---

### Post by landy rover on 2009-07-17
[B]HI Everyone 

Thank you to everyone who tried to help me thank you but themusiclduck said i must try to disconnect ethernet or dsl cable from my pc......AND IT WORKED YIPEEEEEE:P:P:P:P
I have A adsl hub that runs through a ethernet cable when i choose in the start menu bar at the networking icon just before shut down i disable networking and my pc shuts down beutifully......... thank you everybody who helped me i appriecate it ....
[/B]
[B]so all that i do before i shut down is disable networking then the pc shuts down..
when i start up again i dont have to enable it because it is automatic and voila 


:):):):)
[/B]

---

### Post by JasonHippy on 2009-07-17
> **themusicalduck said:**
> 
JasonHippy, not sure about the shutdown problem, but your graphics might be down to the poor Intel graphics support that 9.04 has at the moment. It might be worth booting into an 8.10 live CD to test and see if you have the same problems.

EDIT: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) might be worth reading too for JasonHippy.

Thanks themusicalduck,
I stumbled across the thread you've posted a link to whilst scouring the forums a few minutes after I posted my original message yesterday afternoon. I tried all three configurations (safe, optimal and bleeding edge) when I got home last night. All three versions of the fix improve the stability, but don't completely solve the issue. 

I've reverted it back to the optimal version for now. Video playback has improved, the PC doesn't lock up and crash like it did, but the display is still messed up when using openGL. (I get lots of random noise on the lower portion of the screen and some GUI related issues in Blender and Wings3D appears as an undecipherable, unusable mess!)

As for the shutdown problem, I'm still none the wiser!

But I'll give 8.10 a go when I get home this evening and see how it behaves!

Cheers for now,
Jas.

---

### Post by JasonHippy on 2009-09-07
I've got a bit of an update on the weird problem where my tablet pc restarts on shutdown....

As my tablet PC only has two USB slots, I've been using a 'Trust' USB Hub to enable me to plug in my mouse, keyboard and other assorted USB peripherals (webcam / removable drives / printer etc).

The reason I mention this is because I've noticed that I'm only getting the shutdown problem when the USB Hub is plugged in on shutdown.

It seems that the OS isn't powering the USB hub down properly, which in turn seems to be preventing the PC from shutting down completely, causing it to restart.

However, if I shut the pc down without the USB hub attached the PC will shut down correctly.

For now I'm just having to make sure that I disconnect the hub and any hardware that is attached to it before shutting down... A minor inconvenience, it's true, but I would prefer not to have to unplug everything each time I shut down! 

I'd be surprised if this was a driver related thing, as I thought that USB hubs (and most other USB devices) are pretty generic devices. So could this be a Kernel issue? 
Is anybody aware of any known problems with regard to composite USB devices in Ubuntu 9.04? 

I don't think it's at all likely but is there any possibility that the infamous intel graphics card kernel bug could be having an impact on this?? (seeing as my tablet PC is affected by this bug too!)

Cheers for now,
Jas.

---

### Post by Shannon_VanWagner on 2010-02-08
I was using acpi=off to make my machine boot properly and then it wouldn't shutdown, only "System Halted" with power still on.

So then I tried some different things besides acpi=off as a kernel start option and finally using pci=noacpi in lieu of acpi=off fixed the problems for me. Now my machine shuts off perfectly! Actually test on two machines - one of them is a Gateway motherboard, the other is the Dell Inspiron 2650 laptop - both running Ubuntu 9.10 GNU/Linux.

So my suggestion is to test some different power management options in your boot process such as what is mentioned by Michael Dougherty at  [this article]("http://www.brighthub.com/computing/linux/articles/39504.aspx#ixzz0exKTUV6F"). Here's some of the different options from the article:
---quoted from article--
    *  Try booting with the "acpi=off" kernel parameter:  This will disable ACPI support. If the error is the same with acpi enabled and disabled, you are probably not having an ACPI issue. If that is the case, please see the section of this article titled "Other Possible Solutions".
    * If "acpi=off" allows the system to boot, you will need to isolate the ACPI issue by trying each of the following boot parameters.
    * Try booting with "acpi=ht": This disables all of ACPI except just enough to enable Hyper Threading. If acpi=off works and acpi=ht fails, then the issue is in the ACPI table parsing code itself, or perhaps the SMP code.
    * Try booting with "pci=noacpi": This disables ACPI for IRQ routing and PCI scanning.
    * Try booting with "acpi=noirq": This disables ACPI for IRQ routing.
    * Try booting with "pnpacpi=off": This disables the ACPI component of the Linux Plug and Play code.
    * Try booting with "noapic": This disables the IO-APIC for IRQ routing or PCI scanning.
    * Try booting with "nolapic": This disables the local APIC.
--end quote--

Cheers!
Shannon VanWagner

---

