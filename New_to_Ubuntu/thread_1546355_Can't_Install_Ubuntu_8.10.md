---
title: "Can't Install Ubuntu 8.10"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Rick B. on 2010-08-05
Had a Windows desktop which started rebooting out of nowhere. Couldn't repair or re-install Windows XP Pro.

Tried to install Ubuntu 8.10 from disk. Reached the screen where it read:

Installing System...Partitions Formatting

It became stuck at 5%. Nothing was happening. The keyboard lights were blinking. The HDD light on front of the CPU was not on or blinking.

Any ideas on this? Could it be a bad HDD? Thanks.

---

### Post by LowSky on 2010-08-05
It does sound like a failing hard drive. But open your case and check for a loose connection first, sometimes its as easy as that to fix

---

### Post by jerenept on 2010-08-05
Maybe it is a bug that was fixed in a later release? the current release is at [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download").

---

### Post by Rick B. on 2010-08-05
I don't think it is a bug in 8.10. It installed perfectly on my IBM Thinkpad.

---

### Post by Nerflander on 2010-08-05
use Ultimate boot cd to check your HD for faills or something. Might work.

---

### Post by lukeiamyourfather on 2010-08-05
> **jerenept said:**
> Maybe it is a bug that was fixed in a later release? the current release is at [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download").

Ditto, why are you installing Ubuntu 8.10? Support has already ended for that release. Either way there's probably a hardware specific bug preventing the installing from continuing. Trying another version is the best way to go.

---

### Post by Rick B. on 2010-08-05
Where available or what is Ultimate Boot CD? Can I get online? Thanks.

---

### Post by snowpine on 2010-08-05
Hi Rick, if you can't install Ubuntu OR Windows that points to a problem with your hardware. 

First of all you should be using the current release 10.04 as mentioned already because 8.10 is no longer supported in any way.

Next check the [Ubuntu hardware requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") to make sure your hardware is up to the challenge: 

> The Recommended Minimum System Requirements, here, should allow even an inexperienced user to easily install a usable system with enough room to be comfortable. A good "rule of thumb" is that machines that could run Xp, Vista, Win7 or x86 OS X will almost always be a lot faster with Ubuntu. Simply try Ubuntu Cd as a LiveCd first to check the hardware works.

Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

Next, boot from the Live CD and test drive it "with no change to your computer" for a while. You can run all kinds of tests from the Live CD of your RAM, hard drive, etc. 

Only once you are satisfied the Live CD is working no problem should you proceed to an install.

If it's a hardware problem like bad RAM, hard drive, etc. those parts are fairly inexpensive to replace these days.

---

### Post by LowSky on 2010-08-05
> **Rick B. said:**
> I don't think it is a bug in 8.10. It installed perfectly on my IBM Thinkpad.

These forums prove nearly every day that what works on one machine may not work on another.

---

### Post by Rick B. on 2010-08-05
Yes. I am aware of these things, thank you.

About how long does it take with GParted running from the CD to partition a 250 GB drive? So far it has been running for 90 min. Thanks.

---

