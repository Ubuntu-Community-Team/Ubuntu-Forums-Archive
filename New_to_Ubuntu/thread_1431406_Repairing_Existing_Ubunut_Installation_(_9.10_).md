---
title: "Repairing Existing Ubunut Installation ( 9.10 )"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by subodh.rohilla on 2010-03-16
Is there any way to repair existing installation of ubuntu ( In which i am not able to boot ) . I do not want to format again and loose my data. There is no option for repair when i insert ubuntu CD

---

### Post by oldsoundguy on 2010-03-16
the initial boot off the HD should take you to Grub.  There you can select which kernel you wish to use to boot .. and under each kernel is a repair option.

---

### Post by s3a on 2010-03-16
For future reference, _use a home partition_. This allows you to re-install with all user settings and data intact.

---

### Post by xtremesupremacy3 on 2010-03-16
We don't have enough information to go on in order to help you.
What exactly is the error you get, do you have the option to select a kernel image from the grub menu (The black screen right at start up)?

And then there is also the question of how much was installed on your pc.
The reason I ask this is because if your pc wasn't too perfectly set up to your liking yet, then it might be just easier to start from scratch, however if it was to your liking then repair by all means.

It's true a 'repair' option is not available, that's because the installation CD is a Live CD, What I would do first of all is use that to gain access to my personal data to backup perhaps to a USB.

If you can give us more details of your exact problem, we will do our best to help

---

### Post by lidex on 2010-03-16
If you can't boot let's start there. Boot into a LiveCD session, click on the boot-info script link in my sig and follow the instructions there. Upload the results into your next post.

---

### Post by subodh.rohilla on 2010-03-17
@s3a thanks for your suggestion , Although i have formatted the ubuntu partition and I copied my data by manually mounting it. My root partition was corrupted due to sudden power failure and there is no simple tool to repair the boot sector . Thanks also for the bootinfo script but due to emergency i formatted that partition.
 I am curious that is there any tool to repair linux boot sector like "fixboot" and "fixmbr" commmands in windows xp rather than a following a long sequence of commands. ( i.e. a  single command to completely reinstall bootsector) .Keeping /boot in seprate parttion will do any help ??

---

### Post by coffeecat on 2010-03-17
> **subodh.rohilla said:**
>  My root partition was corrupted due to sudden power failure and there is no simple tool to repair the boot sector .

You are confusing two different things. There is no "boot sector" in Unix land in the way Windows understands it. If your root partition was corrupted, this is a filesystem problem, nothing to do with the bootloader. There is a simple tool to repair the filesystem; it's the terminal command 'fsck'.

> **subodh.rohilla said:**
>  I am curious that is there any tool to repair linux boot sector like "fixboot" and "fixmbr" commmands in windows xp rather than a following a long sequence of commands. ( i.e. a  single command to completely reinstall bootsector)

Again, you are betraying Windows-influenced thinking by referring to the 'boot sector'. Grub is a sophisticated utility (it's more of a mini-operating system) designed to boot up a number of different operating systems. It is not Linux specific. If you want to know more, start with this wikipedia article:

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

Specifically, read what it says about stages 1, 1.5 and 2. Stage 2 you will find in /boot/grub in your root partition (unless you have a separate /boot). By the way, that link is a little dated as it doesn't cover grub2, but it's a good start.

Because there are a zillion different ways grub could be configured, it's far too simplistic to demand the simplistic Windows approach of "fixboot". You need a number of commands, but there are GUI tools for configuring legacy grub for those afraid of terminal commands and I should imagine a GUI configuration for grub2 is not far away, if not already available.

> **subodh.rohilla said:**
>  .Keeping /boot in seprate parttion will do any help ??

Not really.

Last point: you are making criticisms of the way Linux works totally coloured by your experience of Windows. They are utterly different OSs. Another link for you:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

