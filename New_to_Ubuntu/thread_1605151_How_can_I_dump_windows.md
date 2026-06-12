---
title: "How can I dump windows?"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by waxteeth on 2010-10-24
This is the right forum for me..."absolute beginner".

I wound up getting some sort of virus that I could not stop on my windows XP system and after some time of fighting it I decided to give up, save some files, and load Ubuntu.

After a few days I've decided there is nothing I need from Windows so I'm thinking I need to dump it.

My question is if I can do that from where I am at or not. I used the Windows installer option and have a dual boot system currently. I did not save a start up disk...it never asked me to. I downloaded everything off the Ubuntu main page using that Windows installer link.

Is there a simple way I can clear out Windows now or do I have to take some other steps?

Thanks!

By the way, I am digging everything about Ubuntu. I'm not very computer literate but have been able to stumble my way around so far.... So any advice is appreciated.

---

### Post by GabrielYYZ on 2010-10-24
i'd say do a fresh install. 

back up everything you need and install ubuntu from scratch without anything windows in there. 

that's what i did, but you might want to see if someone else has a better/different idea.

---

### Post by Cuddles McKitten on 2010-10-25
EDIT: Missed the bit about the Wubi install.  Whoopsie!

This part is still valid though:
If you do decide to go the fresh install route, I'd recommend having a separate partition for /home for easier upgrades.

---

### Post by beew on 2010-10-25
First of all, you need to make sure that your hardware is compatible with ubuntu (main things are wireless and graphic cards, I am sure others would suggest more) If the hardware is ok and you are sure that you really don't need windows then you need to do a clean install. 

You said you use a Windows installer to install Ubuntu, that means you are running Wubi, that is not a true dual boot. wubi is a Windows program running off a file in Windows. If Windows is gone it is gone as well. So you can't just delete the Windows partition as you would with a true dual boot (there are complications  too actually, but those don't concern us)

To install Ubuntu with a live usb, check out the tutorial here for creating the live usb.
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

Ubuntu 10.10 is the latest but 10.04 is probably more stable and less buggy.

After you have made the live usb, boot the computer off the usb and choose "install Ubuntu". Since you are installing Ubuntu on the entire hard disk it is quite easy, you can do everything just using the default setting. The only thing is make sure you have internet connection during installation.

The process takes about 15-20 minutes and unless you need proprietary drivers, you don't need to install any driver manually.

(Or you can boot into the live usb and choose "Try Ubuntu" and then you can choose the install option inside Ubuntu, in that case you can even surf the internet while you are installing)

BTW, I choose automatic login when I was asked to choose user name and password. It is most hassel free as I am the only person  who uses the computer.

P.S. Yes, if you want a separate /home partition then you would have to choose manual in step4(?)  so set the size and file type for the / , /home and swap partitions.

---

### Post by SuaSwe on 2010-10-25
Seconding the others' opinions.

Best way I'd say is to back everything up that you need to keep, boot into a LiveCD, select Install, then when you reach partitioning opt for 'manual', then delete all partitions (so that you're working with the whole HDD, provided you don't have any other OS's knocking about on there), and finally split it up so that you have:

/ --- root partition - 10GB suffices for me
swap --- at least the size of your RAM - see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
/home --- whatever space remains!

I personally found GParted a little bit intimidating at first, so it could be worth reading around on it a bit first. :) 

Some reading material: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by uRock on 2010-10-25
> **Cuddles McKitten said:**
> You can delete your Windows partition with "gparted" and add the space it was taking up to your current partition, but that's relatively risky as you can lose data.  Make sure to back up before attempting.

If you do decide to go the fresh install route, I'd recommend having a separate partition for /home for easier upgrades.
The OP says he/she used the Windows Installer, so it was a Wubi install. 

A clean install is the only way to go. First burn your data to disk, as you will be writing over the hard drive.

---

### Post by beew on 2010-10-25
Actually he/she doesn't need to use gparted, he can do the partition with the installer. My root partition is 18G but then I install all kind of crap (most things you install in Ubuntu goes to the root partition so make sure you have enough space)

---

### Post by SuaSwe on 2010-10-25
> **beew said:**
> Actually he/she doesn't need to use gparted

To clarify, by "GParted" I meant "the partitioner during the install that looks and behaves just like GParted". :D

---

### Post by sidzen on 2010-10-25
download & burn [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") at 8X or less
boot to the LiveCD just created
at the prompt just before/at instructions to type either "wizard" or "startx" enter
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP] and wait for it to wipe out everything on your hard drive, including viruses and all other junk
then do clean install

---

### Post by beew on 2010-10-25
> **sidzen said:**
> download & burn [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") at 8X or less
boot to the LiveCD just created
at the prompt just before/at instructions to type either "wizard" or "startx" enter
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP] and wait for it to wipe out everything on your hard drive, including viruses and all other junk
then do clean install

Huh?? Don't you wipe everything with a clean install anyway?

---

### Post by waxteeth on 2010-10-25
> **beew said:**
> First of all, you need to make sure that your hardware is compatible with ubuntu (main things are wireless and graphic cards

This is going to sound dumb but how do I do that?

I understand now that I'm going to have to make a clean install so I'll go get a 2mb usb stick for that and read all the directions before proceeding. I'll read about setting up the partitioning and get ready before puling the plug...

But yeah, I would like my graphics card and wireless network to be compatible once I start wiping things out. :shock:

How do I check that before finding out the hard way?

---

### Post by mastablasta on 2010-10-25
> **waxteeth said:**
> This is going to sound dumb but how do I do that?
... 
How do I check that before finding out the hard way?
 
 
the easiest way is to boot the system from LiveCD or to cretae a live USB and boot from USB. that way you can try the system without making any changes to your current system as everything badically loads in RAM in live session. anything you do or install wont' be saved. sometimes live session is much slower (especially if you run it/boot computer from CD)
 
If everything goes well and loads propperly (check the sound, if you have notebook your touchpad, wireless,graphics...) then chances are everything will work upon install as well. in fact it will work "out of the box". 
 
even if small thing is not working in Live session you could ask here and see if it can get corrected upon install (using some command or performing certian upgrades and instalation such as special drivers for wireless).
 
Just a note here you will need to install codecs to get Mp3 files and xvid video to work. can be done after system is installed.
 
also have a look at Linux Mint (based on ubuntu) that comes with many things already preinstalled and also is more similar to windows making transition easier. but it does need a little bit more resources than Ubuntu.

---

### Post by mikewhatever on 2010-10-25
> **sidzen said:**
> download & burn [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") at 8X or less
boot to the LiveCD just created
at the prompt just before/at instructions to type either "wizard" or "startx" enter
[PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP] and wait for it to wipe out everything on your hard drive, including viruses and all other junk
then do clean install

Why would one do that before a clean install that requires formatting anyway?

---

### Post by migs73 on 2010-10-25
> **mastablasta said:**
> the easiest way is to boot the system from LiveCD or to cretae a live USB and boot from USB. that way you can try the system without making any changes to your current system as everything badically loads in RAM in live session. anything you do or install wont' be saved. sometimes live session is much slower (especially if you run it/boot computer from CD)
 
If everything goes well and loads propperly (check the sound, if you have notebook your touchpad, wireless,graphics...) then chances are everything will work upon install as well. in fact it will work "out of the box". 
 
even if small thing is not working in Live session you could ask here and see if it can get corrected upon install (using some command or performing certian upgrades and instalation such as special drivers for wireless).
 
Just a note here you will need to install codecs to get Mp3 files and xvid video to work. can be done after system is installed.
 
also have a look at Linux Mint (based on ubuntu) that comes with many things already preinstalled and also is more similar to windows making transition easier. but it does need a little bit more resources than Ubuntu.

OP is already running a WUBI install. Wouldn't that suffice to know if the hardware is compatible?

---

### Post by mastablasta on 2010-10-25
> **migs73 said:**
> OP is already running a WUBI install. Wouldn't that suffice to know if the hardware is compatible?

good point! :-)
totally overlooked that. i guess the fever got the best of me.

if it runs in wubi it will run even better in a propper full install.

---

### Post by sidzen on 2010-10-27
My experience has been it is not worth having to install twice.  And I've seen Slackware-based distros refuse to install unless I do this first, which tells me some Windoze junk may remain to corrupt a "clean install" if it is not truly _clean_!  I can trust this to give me a fresh hard drive to work with.  If any doubt remains, I change the **bs=4096** to **bs=1024** and do it again!

BTW I do not use wubi and do not dual-boot.  Pane-free is the way to go!

---

