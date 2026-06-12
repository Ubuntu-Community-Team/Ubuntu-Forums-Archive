---
title: "How to turn off auto dimming in 11.04?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2011-05-14
On my HP Pavilion laptop i just bought I installed 11.04 and it keeps auto dimming the screen, any way to turn that option off..?? Thanks..

---

### Post by fox-mulder on 2011-05-15
hi

I have searched the whole freaking world wide web to no avail, I even found threads dated back to 2008 with no answers thats just lame.

the auto dim option that make you log out is stupid and pointless for some, and it seems like no Linux guru out there wanna share the secret to turn it off, sad.

so my fellow natty user gl on the search..

---

### Post by coffeecat on 2011-05-15
@JDM_SOHC, open the "Power Management" app. Untick the "Dim display when idle" tickbox. There's one in the AC Power tab and a second in the Battery Power tab. Untick either or both according to your preference.

---

### Post by Quackers on 2011-05-15
Power Management?

---

### Post by coffeecat on 2011-05-15
> **Quackers said:**
> Power Management?

Not where I used to work! :wink:

---

### Post by Quackers on 2011-05-15
> **coffeecat said:**
> Not where I used to work! :wink:

You can remember? :-)

---

### Post by dwhite on 2011-05-15
screenshots illustrating coffeecat's suggestion

---

### Post by fox-mulder on 2011-05-16
no, didn't work.

---

### Post by fox-mulder on 2011-05-17
just lame..

---

### Post by Prince Valiant on 2011-05-17
Try this:

use Alt-F2 to open gconf-editor, and there should be an entry for controlling the backlight dimming.  You'll probably have to look around a bit, but it might be under apps/gnome-power or something like that.

Have fun!

-Val

---

### Post by el_koraco on 2011-05-17
> **fox-mulder said:**
> just lame..

You need to change the "put display to sleep when idle" to never, so you will not have to enter your password :D

---

### Post by frncz on 2011-05-17
> **Prince Valiant said:**
> Try this:

use Alt-F2 to open gconf-editor, and there should be an entry for controlling the backlight dimming.  You'll probably have to look around a bit, but it might be under apps/gnome-power or something like that.

Have fun!

-Val

Perfect!
in Natty
Alt-F2 and enter gconf-editor
click on apps in left column
click on gnome-screensaver
untick the 'idle_activation_enabled' box

problem solved on my HP 6735s laptop

---

### Post by dcsoldschool53 on 2011-05-17
> **coffeecat said:**
> @JDM_SOHC, open the "Power Management" app. Untick the "Dim display when idle" tickbox. There's one in the AC Power tab and a second in the Battery Power tab. Untick either or both according to your preference.

I am just asking a dumb question here. After you had made the changes that coffeecat had suggested, did you click on the button called Make default to make all changes permanent. When I first made my changes, I know that I had forgot to do it. I'm not a noob. I just forgot, so this is why I am asking you. Did you.

---

### Post by fox-mulder on 2011-05-17
> **frncz said:**
> Perfect!
in Natty
Alt-F2 and enter gconf-editor
click on apps in left column
click on gnome-screensaver
untick the 'idle_activation_enabled' box

problem solved on my HP 6735s laptop


dude, thanks.

finally!

---

### Post by coffeecat on 2011-05-18
> **frncz said:**
> Perfect!
in Natty
Alt-F2 and enter gconf-editor
click on apps in left column
click on gnome-screensaver
untick the 'idle_activation_enabled' box

problem solved on my HP 6735s laptop

You can also use System Settings > Screensaver and untick the "Lock  screen when screensaver is active" box. And  untick the "activate  screensaver when computer is idle" as well if you wish.

There are two different issues mentioned in this thread. The one where  the screen dims after a few seconds of inactivity is dealt with by the  Power Management utility. This dimming only affects laptops, not desktop  machines.

Where the screen blanks entirely and you have to enter your password to  unlock it is the screensaver kicking in. If the screensaver is set to  the default blank screen, then the screen simply goes black. This is not  dimming but blanking, but I can see where the confusion arises.  Personally, I find the default behaviour irritating, but I don't use my  computer in an environment where this is a useful security feature, so I  can understand why the default is set this way.

---

### Post by GnuSense on 2011-12-07
My friend has an HP 6735s which I upgraded from 11.04 to 11.10. The screen was too dull, I guess the backlighting was off, oddly, it would brighten up when the power plug was disconnected, but was still to dark. We were able to fix the issue in 11.04 with changes to /etc/default/grub, but I played with all kinds of versions of those modifications in 11.10 to no effect. Changes to /etc/rc.local didn't help, gconf-editor, xorg.conf, the proprietary driver, etc. ad nauseum.

I fixed it by upgrading the BIOS to the most current version. That is, I believe that is what fixed it. It is possible that upgrading to libcolord1 0.1.12-1ubuntu2.1 may have fixed the issue (I did a dist-upgrade that upgraded libcolord1 just before I flashed the new BIOS). 

I downloaded and extracted this file, then burnt the rom.iso file in the ISO subdirectory to a CD-R and booted from the optical drive.

[ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45715.exe](ftp://ftp.hp.com/pub/softpaq/sp45501-46000/sp45715.exe)

[http://h20000.www2.hp.com/bizsupport...tem=ob-77904-1](http://h20000.www2.hp.com/bizsupport...tem=ob-77904-1)

What a pain.

---

