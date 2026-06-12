---
title: "After 10.04 Upgrade Can't boot into Vista or Recovery Hard Drive"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by iGuitar on 2010-05-02
I just upgraded from 9.10 to 10.04. Now when I try to select either windows vista or the recovery hard drive from the grub menu, then I get a blinking cursor and it does not boot. It is essential for me to dual boot and I don't have a clue how to fix this.

---

### Post by GameDog(A) on 2010-05-02
I'm having the exact same problem.

---

### Post by iGuitar on 2010-05-02
I think it is a grub error but I don't know anything about grub. Hopefully someone will know.

---

### Post by clhsharky on 2010-05-02
HI

Known issue with grub not updating at proper time

Run code in terminal.
```
sudo update-initramfs -u -k all
sudo update-grub
```

restart

Sharky

---

### Post by GameDog(A) on 2010-05-02
Thank you, worked like a charm.

---

### Post by iGuitar on 2010-05-02
Hmm I tried that and I still get the blinking cursor when I try to boot vista and it doesn't boot.

---

### Post by iGuitar on 2010-05-02
Can anyone help?

---

### Post by igorcarajo on 2010-05-03
Same issue here. Windows XP on hd0,1. Ubuntu on hd1,1. Upgraded Ubuntu from 9.10 to 10.04. When I select "Windows XP" from the list, I get a black screen with a blinking cursor and nothing else happens.

I tried the code supplied above by sharky and it didn't fix the problem.

---

### Post by bcbc on 2010-05-03
You might have installed grub to your windows partition and overwritten the bootsector. Here's a link to diagnose and fix: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by arod on 2010-05-03
I had the same problem.

I updated from 9.10 to 10.04 via System > Administration > Update manager. After reboot, my Windows 7 partition install would not boot up.

In my case, the first option [clhsharky]("http://art.ubuntuforums.org/member.php?u=543156") mentioned (updating grub) did not fix my problem.

After following [bcbc]("http://art.ubuntuforums.org/member.php?u=946783")'s advice and following [the link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") provided, I got it to work. The *testdisk* route got me nowhere (I used the one from the repository, not the latest ver). Mind you, in 6th screen, the instructions say that if the "Backup BS" option (tab) does not show up, you might be suffering from a different problem. Well, it DID show up in my run, but it didn't work anyway.

I fixed it by following the Windows CD route. Since mine is Windows 7, you boot into a command prompt and type *bootrec /fixboot *(there's a typo in the original article that goes *bootrecT*. Remove the last "t").

Problem solved.

-a

---

### Post by igorcarajo on 2010-05-03
Update:

I tried to fix the windows boot sector by booting the Windows XP and going into the recovery console, but it said it didn't find any windows installation and that was the end of that road. I then tried running the "testdisk" app as described in the link above. Followed the directions and was able to fix the problem. What testdisk did was to find a backup of the windows boot sector (made by whom?) and copied it to the boot sector.

---

### Post by jacklsw2008 on 2010-05-08
hey guys, i've tried all of the methods that are mentioned here but stil i can't boot vista properly. so i tested editing the /etc/default/grub file.

this particular line seems to be causing the boot issue for me:
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

i just uncomment that part and everything is okay again :)

---

### Post by flyfishingphil on 2010-05-08
FYI from somebody that is NOT well versed in "computer talk".

Decided I'd check and see if I could get in to Vista. Click on the Vista (loader) (on /dev/sda3) thinking that would open it. Instead got a bunch of different actions calling for searches, etc, and never got in to Vista. Restarted, clicked on the Vista Recovery line, just below the Vista loader line, and got into it with no problem. It did take it while to get up to speed but everything seems to work fine.

Maybe you can try this and see what happens.

---

### Post by NoobJeremy on 2010-05-16
The SoureForge link worked great for me...after a while.  My problem was I was taking step 5 "Select the Windows System partition" to mean i had to select the partition i had created for windows (partition 2 see below).  I actually had to select the first partition ending in [System Reserved].  I believe this first partition was created by windows as well.

My TestDisk Screen Shot.

     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]  ---??? I thought was grub
 2 P HPFS - NTFS             12 223 20  5226 227 57   83763200                            ---Windows 7
 3 P Linux                 5227   0  1  9688 254 63   71682030                                    ---Ubuntu 10.04
 4 P HPFS - NTFS           9689   0  1 30393 254 63  332625825 [Storage]          ---Shared Storage

[FONT=monospace]I know I'm a noob but there has got to be other noobs out there that are doing the same thing.  Just sharing what I found.[/FONT]

---

### Post by Mark Phelps on 2010-05-17
> **NoobJeremy said:**
> The SoureForge link worked great for me...after a while.  My problem was I was taking step 5 "Select the Windows System partition" to mean i had to select the partition i had created for windows (partition 2 see below).  I actually had to select the first partition ending in [System Reserved].  I believe this first partition was created by windows as well.

It's not unusual today for vendors to install their machines with a separate boot partition and OS partition.  The boot partition is generally seen as "system reserved".

With a separate boot partition, you can't boot from the OS partition because the boot loader files are no longer stored there.

---

### Post by ubklrigas on 2011-01-18
Thanks the problem solved

---

