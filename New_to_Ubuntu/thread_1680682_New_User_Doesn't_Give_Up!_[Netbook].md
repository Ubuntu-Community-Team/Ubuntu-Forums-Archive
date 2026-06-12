---
title: "New User Doesn't Give Up! [Netbook]"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Lt. Surge on 2011-02-02
[CENTER]_To skip this introduction please look for [COLOR=Red]**P**[/COLOR] [COLOR=Black]further down the post.[/COLOR]_
[/CENTER]

Okay, so my name's Lt. Surge. I have an ongoing understanding of computers, networks and operating systems being forged on a daily basis. And I am a new user who's dabbled into Ubuntu before but never seriously attempted to have it on a computer and keep it there.

I've acquired a used *Toshiba NB-305* (Netbook). First time I ever got a Netbook.
[http://www.toshibadirect.com/td/b2c/pdet.to?poid=501033](http://www.toshibadirect.com/td/b2c/pdet.to?poid=501033)
[I]It's got 1GB DDR3 Memory, 
250GB HDD,
Intel Atom 1.6GHz CPU[/I]

And it comes with this god-awful Starter Version of Windows 7 that is filled with the usual pre-built laptop crap programs that basically do nothing and just waste space(this is not new to me but it isn't a nice reminder of dumb business practices, either).

So, I got to thinking... why not I finally brush off the latest version of Ubuntu I got in the mail and try it out?

At the start, everything seemed to go smoothly. With version 10.04 (Live Disk) in an external DVD drive, the installation process was cooperating. I was able to finish installing Ubuntu 10.04 and restarted. 

-This is where the trouble begins. 

**<>** When I complete the POST from the BIOS, suddenly I get a blank black screen with the GRUB (Linux equivalent of DOS?) sitting there basically doing nothing. When I attempt to type anything nothing happens, either. So naturally I press ctrl+alt+del and try again (even though I had to hold the buttons for it to work). Same thing. So this time, I wait a little, and wait, and wait some more. Then I pressed del and suddenly the login screen appears and everything is hunky-dory. Only after restarting does this problem resurface.

SO, I go online to find Version 10.10. I downloaded it and used the recommended Universal USB Installer to install it on my Corsair 2GB Flash Drive. That went well.

[B][COLOR=Red]P
[/COLOR][/B][COLOR=Red][COLOR=Black]So this is where the fun begins.

I plug in the Flash Drive and begin the installation process (with intents to do a clean install). And the speed at which this starts is HORRIBLE. In fact, pressing keys and tapping the trackpad(mouse) acted as "triggers" as each installation process initialized. idk why, but for some reason I had to tap the trackpad every ten seconds to keep it moving.

When the installation completes(after about two hours of constant tapping of the trackpad, pressing random keys, even unplugging the AC Adapter cord), I restart, unplugging the Flash Drive before doing so as prompted.

And then... THIS... THING... HAPPENS... AGAIN. (refer to <>)
Only this time, I get this after waiting

[/COLOR][/COLOR]```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0b673276-0552-42eb-92cd does not exist. 
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```Before I go any further I desperately need advice. I'm using the **Ubuntu Version 10.10, Netbook Edition**. 

After spending hours trying to get something to work and fumbling through related (if not spot-on) topics regarding this annoying issue, the linux jargon is making me dizzy. I am a Windows User but I'm trying to expand my horizons learning linux through a relatively easy-looking flavour of linux to start on my handy-dandy Netbook. But I can't seem to get past this! :(

Also, is there a way to prevent this thing from taking so long to load/requiring manual intervention just so it gets to the login screen ever again?

And yes, I am prepared to be told "Eh lol dude just enter [insert miracle command here] and you'll be good to go." My pride in being even remotely good at computers is all but lost.

Sincerely,
~Lt. Surge
[COLOR=Red][COLOR=Black]
EDIT: "exit" does nothing.
[/COLOR][/COLOR]

---

### Post by Sealbhach on 2011-02-02
OK, first thing to try is to reinstall Grub, see if you can follow the procedure here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just boot from the DVD again and follow the instructions in that section of the Wiki. There's just 7 steps, stop when you get as far as Method 2.



.

---

### Post by Lt. Surge on 2011-02-02
> **Sealbhach said:**
> OK, first thing to try is to reinstall Grub, see if you can follow the procedure here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Just boot from the DVD again and follow the instructions in that section of the Wiki. There's just 7 steps, stop when you get as far as Method 2.



.

Thank you thank you for posting so quickly... only I officially began at Version 10.10 booting from the USB Flash Drive. I don't have a Live CD...

---

### Post by Sealbhach on 2011-02-02
> **Lt. Surge said:**
> Thank you thank you for posting so quickly... only I officially began at Version 10.10 booting from the USB Flash Drive. I don't have a Live CD...

Same thing, it doesn't matter, should work anyway. When you run fdisk -l your USB will appear as /dev/sdb so ignore it.

.

---

### Post by Lt. Surge on 2011-02-02
> **Sealbhach said:**
> Same thing, it doesn't matter, should work anyway. When you run fdisk -l your USB will appear as /dev/sdb so ignore it.

.

Alright, starting...

EDIT: Just mounted the partition with Linux on it...

EDIT 2: > Installation finished. No error reported.
Rebooting...

---

### Post by sandyd on 2011-02-02
> **Lt. Surge said:**
> [CENTER]_To skip this introduction please look for [COLOR=Red]**P**[/COLOR] [COLOR=Black]further down the post.[/COLOR]_
[/CENTER]

Okay, so my name's Lt. Surge. I have an ongoing understanding of computers, networks and operating systems being forged on a daily basis. And I am a new user who's dabbled into Ubuntu before but never seriously attempted to have it on a computer and keep it there.

I've acquired a used *Toshiba NB-305* (Netbook). First time I ever got a Netbook.
[http://www.toshibadirect.com/td/b2c/pdet.to?poid=501033](http://www.toshibadirect.com/td/b2c/pdet.to?poid=501033)
[I]It's got 1GB DDR3 Memory, 
250GB HDD,
Intel Atom 1.6GHz CPU[/I]

And it comes with this god-awful Starter Version of Windows 7 that is filled with the usual pre-built laptop crap programs that basically do nothing and just waste space(this is not new to me but it isn't a nice reminder of dumb business practices, either).

So, I got to thinking... why not I finally brush off the latest version of Ubuntu I got in the mail and try it out?

At the start, everything seemed to go smoothly. With version 10.04 (Live Disk) in an external DVD drive, the installation process was cooperating. I was able to finish installing Ubuntu 10.04 and restarted. 

-This is where the trouble begins. 

**<>** When I complete the POST from the BIOS, suddenly I get a blank black screen with the GRUB (Linux equivalent of DOS?) sitting there basically doing nothing. When I attempt to type anything nothing happens, either. So naturally I press ctrl+alt+del and try again (even though I had to hold the buttons for it to work). Same thing. So this time, I wait a little, and wait, and wait some more. Then I pressed del and suddenly the login screen appears and everything is hunky-dory. Only after restarting does this problem resurface.

SO, I go online to find Version 10.10. I downloaded it and used the recommended Universal USB Installer to install it on my Corsair 2GB Flash Drive. That went well.

[B][COLOR=Red]P
[/COLOR][/B][COLOR=Red][COLOR=Black]So this is where the fun begins.

I plug in the Flash Drive and begin the installation process (with intents to do a clean install). And the speed at which this starts is HORRIBLE. In fact, pressing keys and tapping the trackpad(mouse) acted as "triggers" as each installation process initialized. idk why, but for some reason I had to tap the trackpad every ten seconds to keep it moving.

When the installation completes(after about two hours of constant tapping of the trackpad, pressing random keys, even unplugging the AC Adapter cord), I restart, unplugging the Flash Drive before doing so as prompted.

And then... THIS... THING... HAPPENS... AGAIN. (refer to <>)
Only this time, I get this after waiting

[/COLOR][/COLOR]```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0b673276-0552-42eb-92cd does not exist. 
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```Before I go any further I desperately need advice. I'm using the **Ubuntu Version 10.10, Netbook Edition**. 

After spending hours trying to get something to work and fumbling through related (if not spot-on) topics regarding this annoying issue, the linux jargon is making me dizzy. I am a Windows User but I'm trying to expand my horizons learning linux through a relatively easy-looking flavour of linux to start on my handy-dandy Netbook. But I can't seem to get past this! :(

Also, is there a way to prevent this thing from taking so long to load/requiring manual intervention just so it gets to the login screen ever again?

And yes, I am prepared to be told "Eh lol dude just enter [insert miracle command here] and you'll be good to go." My pride in being even remotely good at computers is all but lost.

Sincerely,
~Lt. Surge
[COLOR=Red][COLOR=Black]
EDIT: "exit" does nothing.
[/COLOR][/COLOR]
Installation from USB drive is supposed to be slow.

Can you post the output of
```

sudo fdisk -l
blkid
```
from the liveusb installation?
(Terminal is at Applications -> accessories -> terminal)

---

### Post by readable on 2011-02-02
I am a newbee too.

Search the forums for nb305 Toshiba.

There a few bios settings that will end the wait and increase the boot time. Plus some other great info.

Good luck

---

### Post by Lt. Surge on 2011-02-02
Sealbhach, just wanted to let you know Method 1 has failed...

> **sandyd said:**
> Installation from USB drive is supposed to be slow.

Can you post the output of
```

sudo fdisk -l
blkid
```from the liveusb installation?
(Terminal is at Applications -> accessories -> terminal)

Oh, I didn't know that. Sowwies!

K hold on...

I will look into that, readable. Thx

---

### Post by Sealbhach on 2011-02-02
> **Lt. Surge said:**
> Sealbhach, just wanted to let you know Method 1 has failed...x

Did the sudo grub-install command not work?

What happens when you reboot?

.

---

### Post by Lt. Surge on 2011-02-02
> **Sealbhach said:**
> Did the sudo grub-install command not work?

What happens when you reboot?

.

After rebooting upon the completion of supposedly successful re-installation, I just get the blank screen again if I wait for the boot from the Hard Drive to kick in. Same code as original (gave up waiting for root device).

---

### Post by Sealbhach on 2011-02-02
Ah, OK, it looks to be a problem specific to your hardware, I just found this here:

[http://ubuntuforums.org/showthread.php?t=1548618](http://ubuntuforums.org/showthread.php?t=1548618)


.

---

### Post by Lt. Surge on 2011-02-02
> **Sealbhach said:**
> Ah, OK, it looks to be a problem specific to your hardware, I just found this here:

[http://ubuntuforums.org/showthread.php?t=1548618](http://ubuntuforums.org/showthread.php?t=1548618)


.

OMFG Thank you very much guys :grin:. After setting the SATA Controller to Compatibility from ACHI, the only problem now is this:

Anything following the POST is still slow and sluggish. I may restart a few times more to confirm this.

---

### Post by Sealbhach on 2011-02-02
That's good. There may be more tweaks you have to do to get it up to speed. Just Google a bit for Ubuntu + Toshiba NB 305

You should find all the tips and tricks you need.

.

---

