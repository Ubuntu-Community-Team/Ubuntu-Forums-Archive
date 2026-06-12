---
title: "Ubuntu 10.04 no longer boots"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by Mikhail Weiss on 2011-02-01
[FONT=Verdana, sans-serif]Hello, all.[/FONT]
 
[FONT=Verdana, sans-serif]**Ubuntu 10.04 no longer boots**. Get only a black screen with a blinky cursor in upper left hand corner.[/FONT]
 
 [B][FONT=Verdana, sans-serif]Can't boot from live CD.[/FONT]
[/B]  
 [FONT=Verdana, sans-serif]Ubuntu is installed on a homemade machine with a 64-bit AMD Phenom Quad-Core chip in a M3A78-T motherboard.[/FONT]
 
 [FONT=Verdana, sans-serif]**How do I boot this thing up again, in safe or any other mode?** (Using SHIFT to boot in safe mode no longer seems to work.)
[/FONT]
 [FONT=Verdana, sans-serif]Activity before crash:[/FONT]
 
 [FONT=Verdana, sans-serif]Installed all automatic updates.[/FONT]
 
 [FONT=Verdana, sans-serif]Ran machine as LAMP server, writing a small php script in gedit. Tested php output in Firefox. Tried to look again at php in gedit, but gedit was blank. Closed that. Closed Firefox. Closed all open windows. Tried to open php file in gedit again, but only blank. Tried to shut down computer, all screen icons vanished. Nothing else happened. After five minutes of no response from machine, manually powered it off. After that, every attempt at rebooting failed.[/FONT]
 
 [FONT=Verdana, sans-serif]Upon trying to boot from live CD, saw this:[/FONT]
 
 [FONT=Verdana, sans-serif](process: 396): Glib-WARNING **: getpwid_r(): failed due to uknown user id(0)[/FONT]
 
 [FONT=Verdana, sans-serif]Upon trying to boot to safe mode (holding SHIFT key upon bootup), saw this:[/FONT]
 
 [FONT=Verdana, sans-serif]error: hd0,1 out of disk.[/FONT]
 
[FONT=Verdana, sans-serif]My LINUX / UBUNTU EXPERIENCE: almost none. I'm pretty much a rank beginner.[/FONT]
 
 [FONT=Verdana, sans-serif]One more thing: this setup worked fine till today.

Your help on this sticky wicket will be greatly appreciated.
[/FONT]

---

### Post by cogier on 2011-02-01
If the computer was OK and now wont even boot with a live CD I would start by looking for a hardware fault.

After taking all the necessary precautions......I suggest you remove the video card and any others, check for clean connections and refit, even take out and reinstall the memory, check all wiring is correctly and firmly installed, power cables to the drives correctly located and give it another boot.

Good luck and I hope it helps.

---

### Post by Mikhail Weiss on 2011-02-01
Hmm. Interesting. No video card installed.

Just tried rebooting from flash drive, using something called a [Universal USB]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") Installer, got this:

[COLOR=Blue]error: hd0, 1 out of disk.
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/bf8f2b1e-1587-4150-a830-3d39ce42e67d does not exist. Dropping to a shell!

Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/COLOR]

Typing in 'help' yields this:

[COLOR=Blue]Built-in commands:
----------------------
. : [ alias break cd chdir command continue echo eval exec exit export false getopts hash help let ... zcat[/COLOR]

...In other words, a crapload of commands, in which I don't see anything about booting, booting in safe mode, or, well, anything else I might use to get things up and running.

I'd reinstall the OS, except the live CD never gets past the screen that says Ubuntu and shows the little dots. (Of course I'd rather save some of the data on the HD, if possible, too.)

Thanks for the ideas, though. May have to give them a whirl.

---

### Post by cogier on 2011-02-02
If you can check your Live CD and/or USB boot stick in another computer and one of both work then I suggest you again look at a hardware fault.

---

### Post by Mikhail Weiss on 2011-02-02
Checked all connections. Everything looks good. Booted into BIOS and all hardware seemed tip-top.

Computer booted this morning and looked good to go. Ran it for a few hours and then noticed that a Wine application, PaintShop Pro, wouldn't load. Then noticed GIMP wouldn't either. Or a web browser. Tried shutting down and all of the screen icons vanished. Everything else looked normal (task bars top and bottom still there).

Seems like the OS is suddenly unstable, but not sure how to determine if that is, indeed, the case, or if it's a hardware issue. As mentioned, BIOS manager had no trouble detecting the hardware, and all indications are that the hardware gadgets remain okay.

My present theory: whatever the latest updates were (and that I didn't check) somehow wonkered something.

Any smart ideas for how to fix this issue, or is this starting to resemble a reformat/reinstall solution? 
:mad:

P.S. When the system started crapping out and all the on-screen icons vanished, I noticed the HDD activity light remained constantly lit up. After five minutes of no worky computer, I manually powered down. Could this be a source of trouble, too? (In fact, I just rebooted a moment ago and get, once again, the BusyBox message.)

---

### Post by sydbat on 2011-02-02
How long ago did you build the box? 

Is the inside clean? If not, vacuum time.

Turn off the power supply button, unplug the power cord, open it all up and reseat everything, including your AMD CPU. Make sure you use the recommended amount of heat sink compound (aka thermal paste), because too much or too little can cause overheating problems with the processor.

If all that fails, and the parts are really new and under still under warranty, bring the assembled box back to where you bought the parts and see if they can diagnose any hardware problems. If any are bad, the store should give you replacements without hassle.

---

### Post by Mikhail Weiss on 2011-02-02
Looks like I put it together Jan 2009. Yesterday I did as you suggested (except for reseating/regooing the cpu, and the innards didn't strike me as very dusty at all).

Found this article about the BusyBox black screen problem, which is what I encountered yesterday and today (after today's crash), and it looks potentially useful, but as earlier stated, I'm pretty much new at all this:
[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/]("http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/")

How's that strike you? Seem like a likely fix?

P.S. I booted from the live CD and tried to browse the HDD, received this message:
Unable to mount 990 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful ifo is found in syslog - try dmesg | tail or so

---

### Post by sydbat on 2011-02-02
> **Mikhail Weiss said:**
> Looks like I put it together Jan 2009. Yesterday I did as you suggested (except for reseating/regooing the cpu, and the innards didn't strike me as very dusty at all).

Found this article about the BusyBox black screen problem, which is what I encountered yesterday and today (after today's crash), and it looks potentially useful, but as earlier stated, I'm pretty much new at all this:
[http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/]("http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/")

**How's that strike you? Seem like a likely fix?**

P.S. I booted from the live CD and tried to browse the HDD, received this message:
Unable to mount 990 GB Filesystem
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful ifo is found in syslog - try dmesg | tail or soPossibly, at least for the busy box bit. However, that would not account for the seemingly random "freezing" and loss of desktop icons / panels. Something else is going on that, to me, points to a hardware issue.

Dumb question time - in your BIOS, how have your set disc access? Connecting your HDD via SATA, you should have the option of [ACHI]("http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface") or [IDE]("http://en.wikipedia.org/wiki/Parallel_ATA"). That might make a difference, especially if, at some point, you changed it from one to the other then back again.*

*A client did this once, while tinkering, and suddenly it showed "wrong fs type". Something obviously corrupted and we had to do a reinstall.

---

### Post by Mikhail Weiss on 2011-02-02
I managed to boot up again after several failed attempts.

Opened up System/Administration/Disk Utility, and the SMART data declares the "Disk is healthy." Is this to be trusted?

[INDENT]Dumb question time - in your BIOS, how have your set disc access? Connecting your HDD via SATA, you should have the option of ACHI or IDE. That might make a difference, especially if, at some point, you changed it from one to the other then back again.*[/INDENT]

Hmm. Have no idea about BIOS disc access settings. Will have to check on that and get back to you. Presently backing up files in case all is otherwise lost.

Thanks for you help, though. I continue working to solve the problem.

---

### Post by Mikhail Weiss on 2011-02-10
Well, it now works fine. Have no real idea why, though perhaps unplugging some hardware and plugging it back in helped.

Meanwhile, thanks for the suggestions.

---

