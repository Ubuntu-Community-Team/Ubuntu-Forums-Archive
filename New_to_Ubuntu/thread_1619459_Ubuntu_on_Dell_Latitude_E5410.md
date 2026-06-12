---
title: "Ubuntu on Dell Latitude E5410"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by japhyr on 2010-11-11
Hello,

I am trying to install 10.04 on a Dell Latitude E5410 laptop.  I have used this install disc on numerous machines successfully, so I know the disc works.  When I boot from the disk on the latitude, I see the little computer=human logo, then a blinking cursor, then a blank screen.  The blank screen never activates.

Is there a way to access a non-gui installer from a normal liveCD?  If not, is there something else I can try?

---

### Post by sandyd on 2010-11-11
> **japhyr said:**
> Hello,

I am trying to install 10.04 on a Dell Latitude E5410 laptop.  I have used this install disc on numerous machines successfully, so I know the disc works.  When I boot from the disk on the latitude, I see the little computer=human logo, then a blinking cursor, then a blank screen.  The blank screen never activates.

Is there a way to access a non-gui installer from a normal liveCD?  If not, is there something else I can try?

press esc when you get to the screen with a human at the bottom.
select "other options" using F11 (is it that key? )
select nomodeset.

---

### Post by japhyr on 2010-11-11
Pressing escape as you described got me to the old style liveCD menu.  I tried running without installing, and got the same blank screen.  I heard the startup music, but never saw anything on the screen.

I tried pressing F6 for other options, then selected nomodeset.  It seemed like it was going to work; I saw the big ubuntu logo on the screen and the progress dots, but then the screen went blank as well.  I notice that the caps lock and some other symbol are flashing now.

Any more suggestions, or does it look like I will have no luck installing ubuntu on this laptop?  I don't find much in forum or google searches about this either.  I will be particularly disappointed if this doesn't work because these are school computers, and students would have the chance to use Linux or Windows on each machine.  I hate to leave students with Windows as their only option.

---

### Post by sandyd on 2010-11-11
> **japhyr said:**
> Pressing escape as you described got me to the old style liveCD menu.  I tried running without installing, and got the same blank screen.  I heard the startup music, but never saw anything on the screen.

I tried pressing F6 for other options, then selected nomodeset.  It seemed like it was going to work; I saw the big ubuntu logo on the screen and the progress dots, but then the screen went blank as well.  I notice that the caps lock and some other symbol are flashing now.

Any more suggestions, or does it look like I will have no luck installing ubuntu on this laptop?  I don't find much in forum or google searches about this either.  I will be particularly disappointed if this doesn't work because these are school computers, and students would have the chance to use Linux or Windows on each machine.  I hate to leave students with Windows as their only option.the flashing scroll/caps lights are
 an indication of a kernel panic.

---

### Post by japhyr on 2010-11-12
> indication of a kernel panic
That doesn't sound very good.  :(

---

### Post by japhyr on 2010-11-12
Are there any other distros I might try, or does a kernel panic imply that most distributions are unlikely to work as well?

---

### Post by lastguy on 2010-11-22
I got exactly same problem. E5410 BIOS A6, cannot install Ubuntu 10.04/10.10, need a urgent help!!!

---

### Post by lastguy on 2010-11-22
it seems to be the windows7 100MB partition causes problem, seeking a way to delete it

---

### Post by japhyr on 2010-11-22
Are you installing from scratch, or do you need to have a dual-boot setup?

---

### Post by japhyr on 2010-12-06
I have a student who brought in a liveCD of Arch Linux, and it appeared to work on the E5410.  Before we start doing a bunch of Arch Linux installations, does this suggest any other distros that might be worth trying?  I have no idea what is unique about Arch Linux that would make it work on this computer, where Ubuntu does not.

---

### Post by ubudrummer on 2011-01-30
Here's what worked for me:

Dell E5410, Ubuntu 10.04 installed via wubi.

1) Let the installation run with black screen for a while (~1/2 hour)
2) Reboot, you should get to the GRUB, then select failsafe mode
3) Select failsafe graphics mode to boot once - this got me to the Ubuntu login page
4) After login, open a terminal and copy /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf
5) edit /etc/default/grub, change GRUB_CMDLINE_LINUX_DEFAULT by changing "quiet splash" to "nomodeset" (don't forget to run update-grub after the edit)
6) Reboot. Everything works OK.

All of these steps are documented elsewhere. The solution for me was just to put the pieces together in the right order.

Best luck.

---

### Post by lastguy on 2011-03-02
Ha now 03/11, I just tried on Ubuntu 10.10 live, same black! Free!
sb suggests modify grub, I have black screen how to modify? press Ctrl-Alt-F1 no use.
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0

Documented elsewhere? seems not easy to find? anyway why not update?

---

### Post by japhyr on 2011-03-02
I was able to install Linux Mint without a problem.  If you're unfamiliar with Mint, it's a derivative of Ubuntu.

I have an install script that I run on ubuntu machines after installing the os.  The install script loads all the programs we use, and copies configuration files as well.  When I ran the script as-is on Mint, everything worked.  The machine ended up looking like an ubuntu machine that says Mint.  You might give it a try.

---

### Post by nahumet on 2011-04-15
> **japhyr said:**
> Hello,

I am trying to install 10.04 on a Dell Latitude E5410 laptop.  I have used this install disc on numerous machines successfully, so I know the disc works.  When I boot from the disk on the latitude, I see the little computer=human logo, then a blinking cursor, then a blank screen.  The blank screen never activates.

Is there a way to access a non-gui installer from a normal liveCD?  If not, is there something else I can try?
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

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

If adding "i915.modeset=1" to your boot parameters allows you to boot successfully, you then need to enter the command above into a terminal to make the changes permanent.

You should try this, it worked finde for me on the same laptop.

---

