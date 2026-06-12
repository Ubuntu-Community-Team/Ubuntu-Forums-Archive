---
title: "Grub disk counting compared with partitionmanager"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by yozgoesdigital on 2009-04-27
Hi people,
I have a dual boot kubuntu 9.04 and xp and a free 10g partition for testing different distros. The third distro I want to manually add to my original grub menu (on kubuntu 9.04 disk). But in order to get a hold on grub I encountered the following problem: 

My BIOS says:
- win xp disk in second slot
- linux disk in third slot (first slot is empty)

Kubuntu partition manager gives:
- xp disk as sda
- linux disk as sdb
* grub is installed on kubuntu partition (sdb2, which is the linux disk)

Up to here I can see a logic, but if I start my 9.04 kubuntu from grub it says something that it is booting from (hd0,1) and a long number, which should be according the documentation my xp disk?

Why does grub say it is booting from hd0 and not hd1 since linux disk is my second disk?

---

### Post by Herman on 2009-04-27
It's not your mistake, but an old problem that has never been able to be solved.

The problem happens mostly when there are different kinds of hard disks mixed together on the same motherboard. Some BIOSes will give preference to all SATA drives, and others prefer to number IDE first when they list the drives. I even have seen a few computers that will automatically put any USB drive(s) at the top of the list if one is present during boot-up. Most BIOSes count USB drives last.

I don't know what sign or signal GRUB looks at in the BIOS to try to guess the hard drive order.  Apparently, whatever it is, in some BIOSes it's one way and in other BIOSes it's the opposite. GRUB is set to try to be correct for most BIOSes, (meaning, more than half of the BIOSes in the world). However, I have read, if they did change GRUB to be the other way around, then the other half, (or more than half), of people whose computers have SATA and IDE drives will complain.

To make matters even more complicated, it seems like Linux uses some different way of deciding the hard disk order than GRUB, but that's not always right either, because my old Linux installations view my hard disks one way, and my newer Linux installations view them in a different order.

The only think I can suggest is to just grin and bear it. Or laugh loudly. Take hard drive numbering with a grain of salt. Don't expect anything to be perfect or you'll go crazy.

The best way to determine which way GRUB sees your hard drives is ask GRUB.
When your computer is booting up, press your 'c' key from a GRUB menu for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). 

[How to use GRUB's Command Line]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer") - to investigate a computer.
               
You can also do many of the same commands after Ubuntu is booted, from [the GNU/GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell").

Regards, Herman :)

---

### Post by yozgoesdigital on 2009-04-27
Hi Herman,
Thanks for your reply and great links!! As I read from your reply it is sometimes a bit confusing.
I the end I managed to get what I wanted by changing the menu.lst with kate inside kubuntu and reboot. But your solution of using the grub command lines looks like a much better solution (and quicker), So I will remember it for next time!


Greetings Jos

---

