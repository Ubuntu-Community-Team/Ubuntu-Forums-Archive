---
title: "I get a blank desktop..........."
date: 2009-03-19
forum: New to Ubuntu
---

### Post by blandman3 on 2009-03-19
I have tried to run the ubuntu cd live, and have tried to install it on my computer.  For some reason, I cannot access ubuntu after I input my username and password.  It just comes up blank, and everything stops running, like it is frozen.  The CD is fine, because it works in another computer.  Is there something else I should do, maybe in BIOS, that would enable me to access ubuntu after the password screen?  Do I need to update my graphics card?  I don't think I would need to do this, only because it loads and everything on the screen, but there is nothing after I input a password.  I appreciate anyone who can help.

---

### Post by Helios1276 on 2009-03-19
Sounds like a bad install despite the CD working elsewhere, this might shed some light:

[http://forums.majorgeeks.com/showthread.php?p=1112850](http://forums.majorgeeks.com/showthread.php?p=1112850)

---

### Post by blandman3 on 2009-03-19
Ahh, sounds like a good theory.  I just have one question for you then, why won't it run LIVE then?

by the way, thank you for your immediate reply!:popcorn:

---

### Post by ugm6hr on 2009-03-20
This does sound like a graphics card problem.

Try booting into the Recovery terminal and logging in from there.  If that works, clearly there is a problem with X / graphics.

Also... At what stage does the LiveCD hang?

And when you say it comes up blank: what do you see on screen?  Nothing, or a brown background?  Do you have a mouse pointer?  Do you hear the login sound?

---

### Post by sdbrogan on 2009-03-20
Sounds a bit like the trouble I had.  It might be worth trying changing the boot options if you haven't already (see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)).  I found that this combination worked :

noapic nolapic acpi=off irqpoll pci=noacpi

---

### Post by blandman3 on 2009-03-20
Ok, to sum it up guys here is a walkthrough:

I put cd in tray
I reboot machine
CD loads Ubuntu
I come to a language screen
;)then try to install without changing settings on my computer
;)after I hit enter it comes to an orange screen
:othen it comes to a password screen with the desktop in the  background, but no other title bars up top
:(after I press enter, or have also just let time run out that is when I come to a black screen sometimes with the cursor, and sometimes without
:(I tried in safe mode but get nothing all of the time (black screen)

I will try the other tactic and update you on any progress

P.s. my system clock resets to an odd time, so when I get back into Windows XP, my clock is ahead by 3 or 4 hours.

---

### Post by ugm6hr on 2009-03-20
Whether it works in another computer or not, that is a bad CD burn.

There is no other explanation for why the LiveCD would ask for a password to log in.

Check the md5sum and run the Check for errors.  Or just use Torrent to check the iso file, then burn at as slow a speed as allowed.

---

### Post by blandman3 on 2009-03-20
also, yes I do hear the sound, just don't see anything on the screen just black.

---

### Post by Kareeser on 2009-03-20
The reason the time settings are messed up is because Ubuntu tends to set the system time to UTC, and adjust it based on your time zone. Windows sets the system time according to the local time zone.

Both have their advantages, but they don't work well together. There should have been an option to allow the time settings to work properly.

Try pressing "Ctrl-Alt-F1", do you get a command prompt now?

---

### Post by ramadaus on 2009-03-20
I also get a blank sreen on live CD for ubuntu 8.10 and 9.04 alpha on my Vaio PCG-R600HMPD. My laptop is fine as I dual boot with XP and everything works in windows. If I boot safe graphics mode I get a small screen in the centre of the monitor.

---

### Post by blandman3 on 2009-03-20
I tried to do it in safe mode, but it gave me a fuzzy screen at first, then it went black.  I will try ctrl alt f1

thanks guys for your input.

---

### Post by blandman3 on 2009-03-20
Hey guys, here is a little more information I found when trying to boot ubuntu.

error message "unable to load description tables"

and when I pressed ctrl alt F1, I got a screen (after typing a menu command) that gives me some information I hope you guys find helpful:

Booting command-list
Filesystem type is ntfs, partition type 0x07
The current working directory (i.e., the relative path) is /ubuntu/disks
[Linux-bzImage, setup=0x3000, size=0x220cb0]
[Linux-initrd @ 0x1efd3000, 0x80c6b0 bytes]
[ 0.031326] BIOS bug, local APIC #0 not detected!...
[ 0.031374] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[ 0.070021] pci 000:01:09.0: BAR 5: error updating (0xec000000 !=0x2000024)
[ 0.070074] pci 000:01:09.0: BAR 0: error updating (0x00c401 !=0x2000010)
[ 0.070119] pci 0000:01:09.0: BAR 1: error updating (0xec000020 !=0x20000)

---

### Post by blandman3 on 2009-03-20
Here is an update for those of you who are following this problem:

I have successfully loaded my LIVE CD!

The problem:
I would get to a screen with a password, then I would press enter and no desktop, but I could hear it loading (the music in the beginning), in turn, it never loaded the screen.  It was blank, and the cursor would freeze as well.

The solution: (temporary anyway)
At the main menu, I hit F6 for more options
I then typed the following:
hw-detect/start_pcmcia=false netcfg/disable_dchp=true irqpoll xforcevesa

Now, I am not sure if I typed irqpoll or not.

Because I have to input these commands before it loads, how can I install this and make sure those commands are saved so I won't have to type them in every single time I run Ubuntu 8.10?

---

### Post by Shadey4 on 2009-03-20
I was having this problem as well and it was one of the things that caused me to go to other distributions. I want to go back to Ubuntu and give it a go. The way I got around this was to use safe graphics mode and I was able to install it that way. I soon ran into other issues once in Ubuntu. By using other distributions I have learned a little more and it has encouraged me to try Ubuntu again.

---

### Post by ugm6hr on 2009-03-20
> **blandman3 said:**
> I would get to a screen with a password...

Again.

There is a problem here.

The Ubuntu LiveCD does not have a password.

---

### Post by blandman3 on 2009-03-20
believe me ugm6hr, I know it shouldn't have a password, what I was saying was that in order for me to load the CD Live, I had to input those commands at the menu where you can hit F6 to input extra boot commands, and it brought me right into ubuntu without the password screen. I think it might be my graphics card that needs updated because the desktop looks wide, but I have the resolution set to the highest.  This is a brand new monitor, but I don't think I installed the driver that came with the monitor. Maybe if I do that, it would fix the situation?

I am having trouble running media on this, I guess because I am running it live?

---

### Post by blandman3 on 2009-03-20
Yeah shadey, I have tried to run it in safe also, but it was doing the exact same thing.  Thank you guys so much for your help.  I would like to learn more on commands that way I could help somebody sometime.

---

### Post by blandman3 on 2009-03-20
Also, I did the CD check or ms5sums, and everything was ok, no problems at all.

---

### Post by kansasnoob on 2009-03-20
> **ugm6hr said:**
> Whether it works in another computer or not, that is a bad CD burn.

There is no other explanation for why the LiveCD would ask for a password to log in.

Check the md5sum and run the Check for errors.  Or just use Torrent to check the iso file, then burn at as slow a speed as allowed.

Or a bad drive! Smoke loves to cloud things!

---

### Post by trebor on 2009-03-21
I was having the same problem with a Dell GX270.  I found that by removing all the PCI cards except for what was needed for the computer run, the live CD booted just fine.  I think it has something to do with a IRQ conflict.

---

### Post by blandman3 on 2009-03-22
makes sense trebor, plus there are a lot of I/O errors, plus the description tables won't run.

I am still pondering why my system won't go past the login screen though.  I have it installed, but everytime I input my password and username, it goes to a blank orange screen, and I am able to move my cursor.

---

### Post by tyreafus on 2009-03-22
blandman, I get the same exact problem:  Blank desktop with the mauve background, NO desktop image(the brown-scale skull/penguin depending on how you look at it), just solid mauve.  just a mouse cursor, which I can move.

I'm trying to install on an old Dell Inspiron 1100 Laptop.

---

### Post by blandman3 on 2009-03-22
> **tyreafus said:**
> blandman, I get the same exact problem:  Blank desktop with the mauve background, NO desktop image(the brown-scale skull/penguin depending on how you look at it), just solid mauve.  just a mouse cursor, which I can move.

I'm trying to install on an old Dell Inspiron 1100 Laptop.

I don't know if this will help you, but I did receive a lot of help here:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tyreafus on 2009-03-22
Update:

I updated the motherboard to the latest BIOS(see [here]("http://www.geocities.com/randomnumbergenerator2001/").)

Also, I realized that the first time I installed Intrepid, I had to do a dpkg before it would display properly.  I tried this and realized that it wasn't seeing the servers.  Checked my /etc/network/interfaces', realized that it didn't have a configuration for my NIC card.  I must have left the network cable out when I did the install.  I added the following to this file using nano /etc/network/interfaces at the root terminal(started in recovery mode)
```

auto eth0
iface eth0 inet dhcp
```

I then re-ran dpkg from the recovery menu.  It's downloading now, will update when it finishes.  Hopefully I'll have a working system then...

---

### Post by tyreafus on 2009-03-22
And we are a GO!

After the updates finished, did a reboot, didn't have to do anything with the boot command, it brought up the full GNOME.

Apparently the 8.10 base install doesn't work with my laptop, but the updates fix that.

---

