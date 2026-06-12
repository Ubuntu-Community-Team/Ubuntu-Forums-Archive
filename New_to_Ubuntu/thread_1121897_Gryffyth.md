---
title: "Gryffyth"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by gryffyth on 2009-04-10
I recently installed a copy of Linux Ubuntu from a CD on to a second comuter which had been running Windows XP. All went well for a couple of weeks, but now I'm unable to boot up. The on-screen messages I get are:
Auto-detecting Pri Master -- not detected
Auto-detecting Pri Slave -- not detected
Searching for ACSI -- not detected.

The screen then scrolls down to

Boot failurReboot and select proper Boot devicea
or insert Boot Media in selected Boot device
Press any key when ready.

At this point the keyboard is active, but not the mouse.
I have tried to re-install Ubuntu from the CD but the partitioning details are greyed out.
If anyone can help me resurrect this machine I'd be most grateful

---

### Post by jdackle on 2009-04-10
That's NOT a problem with Ubuntu, rather with your BIOS setup!

Those are messages from the BIOS (before booting the OS, Linux, Windows or whatever) telling you IT CANNOT FIND YOU HARDDISK(S).

That's also why the partitioning running from the CD is greyed: YOU HAVE NO DISK! At least one you could detect...

You, or someone else, have probably played around with the BIOS setup and accidentally un or mis configured your harddrive...

Try and get into the BIOS setup (normally by pressing ESC, DEL, F1 or something like that during boot) and correct your harddisk settings.
If you don't know which is the correct one, try "Automatic" if such an option exists. If there isn't, you'll just have to try around...

---

### Post by gryffyth on 2009-04-11
Thanks for your help, and guiding me in the right direction.

---

### Post by roger_1960 on 2009-04-11
Hi

If its not the BIOS, it could be a loose disk drive ribbon cable connector.......

---

### Post by kamitsukai on 2009-04-11
> **roger_1960 said:**
> Hi

If its not the BIOS, it could be a loose disk drive ribbon cable connector.......

Much more common than you'd imagine as well:lolflag:

(amount of times of kneed my PC when sitting down and then having to open it up to reconnect something;))

---

