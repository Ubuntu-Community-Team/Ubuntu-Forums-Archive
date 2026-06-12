---
title: "Using external HDD for Karmic testing"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-03-29
I was wondering if I could install 9.10 in an external HDD (have a Maxtor OneTouch 4 Mini 160GB), add in programs until I have everything I need, transfer files that I work with, get everything tested and workable, then format my main and transfer everything from the external. (Would love to completely drop the Windogs Viscus OS)

I'm NOT 'puter literate so any help would need to be in a step-by-step style written for a total beginner that has:
Toshiba L350-S593 32 bit OpSys
ACPI x86 based
Intel Pentium T3400 @ 2.16GHz
RAM   3.00GB
BIOS Version 2.10
Wi-Fi network & printer
224 GB HDD (currently at 156GB free)
CD/DVD r/w
Mobile Intel 4 series Express Display adapters

Tested with Live CD last night and everything seemed to work except the Canon MP560 printer. (Found thread that listed [TurboPrint]("http://www.turboprint.info") as a great resource for Linux printer drivers (Cost US$40 +/-) and found it covers mine. (Anybody know of a "free" Linux driver resource for the Canon printers?)

Have printed out: HowToMD5SUM, BurningISOHowTo, (both worked great) Installing Software in Ubuntu,A Newbie's Initiation to Linux,Ubuntu Karmic Koala Bible (avail at [makeuseof.com]("http://www.makeuseof.com"))(Now all I have to do is read it a bunch, until it makes sense!)

Any help greatly appreciated.

Phil:redface:

Just went searching and found a great resource for those having problems with their Canon printer drivers and Linux. If you have a Canon go to [Canon Asia]("http://support-asia.canon-asia.com/"),enter the printer info requested and go to their driver download page and get what you need. Haven't had a chance to try my download yet so will post if it doesn't work. No post = works fine.

---

### Post by uRock on 2010-03-30
If your BIOS allows booting from external drives, then it shouldn't be a problem.

---

### Post by sgosnell on 2010-03-30
Just install to the external HDD.  It needs to be connected before booting the Ubuntu LiveCD, but otherwise it's straightforward.  Just choose that drive for the install.  When you want to use your internal drive, you can just copy /home to /home on the internal drive.  I prefer having /home on a separate partition so it doesn't get wiped during upgrades or reinstalls, but that's not mandatory.  You could repartition your internal HDD now, and put /home on the new partition if you want, and then just use that when you install Ubuntu on the internal drive, but that's certainly optional.

---

### Post by flyfishingphil on 2010-03-30
[FONT="Comic Sans MS"][SIZE="4"][/SIZE][/SIZE][/FONT]t

Call it SOLVED

Tried several times but couldn't get Ubuntu to offer the option of installing in external so went ahead and did a dual boot. Took a couple of hours to do the download and install of the 247 update package files, but it seems to be working pretty well. Will spend a few hours "investigating" and see what works and what doesn't. Already found that it recognizes the Canon MP560, connected with USB, but nothinbg happens when I tell it to print something. Mess with that for a while and see what I can figure out. 

Thanks for the assist and I'll check later for anything I can't get to work.

---

