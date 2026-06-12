---
title: "Help with installation."
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Guffmeister on 2009-11-17
Hi there! As you can probably tell since I'm posting here, that I am an absolute beginner. I apologise in advance for the lengthy post, and hope that someone here has the time to read it and advise me.

First of all, I had a single SATA hard drive in my computer, which I had split into two equal partitions. On one partition I have Windows XP. I also have a DVD-ROM drive attached to the motherboard via an ATA cable, which is first in line for the booting procedure, before my hard drive. I then recently found another hard drive, which I set to slave, and attached to the free ATA slot on the cable that goes to the DVD-ROM. Right...ok.

I then decided to install Ubuntu onto the other partition of the first hard drive. It recognised the first hard drive as sdb1 and sdb2, and the new one as sda1. I split the second partition so I had one for the swap partition, and proceeded to install.

It installed fine, and I restarted. My computer booted straight into Windows, and gave me no choice. I was told by a friend that Grub would install automatically, and I wonder if it had something to do with my hard drives being in a funny order. I then found a link on this forum, about installing Grub ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) so I followed the instructions. /boot/grub/stage1 was located on (hd1,2). I completed the rest of the instructions to the letter, even the setup line to (hd0), which I now realise would be my new, slave hard drive. I restarted, and this time got an error that boot.ini was corrupted, or something like that (it only flashes up for less than a second), and says it will proceed to boot from C:/WINDOWS, before loading Windows again.

Realising I'd setup grub on the wrong hard drive, I followed the previous instructions, this time setting it up on (hd1). I restarted, and success! Grub loads! But wait...

None of the options load. If I boot Ubuntu I get an 'Error 22: no such partition'. However, if I edit the lines, I see that it's trying to boot from (hd1,2), which must exist, since that's where I loaded stage1 from. If I change this to (hd0,2) it works, and Ubuntu loads!

If I boot Windows, it says it is booting from (hd1,0), which is right, but there are also two line mapping hd0 to hd1 and hd1 to hd0. If I just boot this normally, I get 'Starting up... NTLDR is missing Press Ctrl+Alt+Del to restart'. If I delete the two mapping lines, Windows proceeds to the boot.ini corruption error, before loading Windows fine.

So, my questions are:

Does anyone know what has happened here? Why does Ubuntu suddenly think it is installed on (hd0,2) when it was on (hd1,2)?

How can I edit the Grub loading sequence so that changes I make are saved? I can get Ubuntu and Windows to load, even though I don't know how or why, but I have to edit the boot code every time I boot. I also want to change the order, so that Windows is at the top (sorry...I know how much you guys love Linux, but I'd rather Windows be the default...for now at least).

Finally, how do I undo the first error I made by installing Grub onto (hd0)? While Windows loads fine, I'd like to get rid of the corrupt boot.ini message. Maybe it's a Windows issue.

If anyone can help, or be bothered to even read this post I will be very grateful. I'm sure it's not a difficult problem, but I can't work out what's going on.

Thank you for your help.

---

### Post by mprince on 2009-11-17
> None of the options load. If I boot Ubuntu I get an 'Error 22: no such partition'. However, if I edit the lines, I see that it's trying to boot from (hd1,2), which must exist, since that's where I loaded stage1 from. If I change this to (hd0,2) it works, and Ubuntu loads!

According to this site: [http://www.brighthub.com/computing/linux/articles/36648.aspx](http://www.brighthub.com/computing/linux/articles/36648.aspx)
hd1,2 would refer to the **3rd partition** on the second drive.


>  GRUB calculates the disk numbers and partition numbers by starting from 0. So a disk named hd1,2 will be referring to the third partition on the second disk, which Linux would refer to as /dev/hdb3 or /dev/sdb3. Please find out the correct disk numbers before saving the GRUB configuration file.


Have you tried updating grub automatically?

---

### Post by Guffmeister on 2009-11-18
Yes, that is correct. The first partition is Windows, second is the swap partition, third is Ubuntu.

So Ubuntu is indeed installed on (hd1,2).

How do you mean updating grub automatically?

---

### Post by wrgb2 on 2009-11-18
To update grub manually, in a terminal window (Applications > Accessories > Terminal) type:

```
sudo update-grub
```

To adjust the order of the items in the menu, install startup-manager:

```
sudo apt-get startup-manager
```

---

### Post by Guffmeister on 2009-11-18
Great! Thanks.

What does updating Grub actually do?

---

### Post by wrgb2 on 2009-11-18
It causes it to go out and check for installed OS's again and puts them in the menu.

---

### Post by Guffmeister on 2009-11-18
Thank you very much for your help! I will try this tonight when I'm home and report back to see if it has solved my problem.

Thanks again.

---

### Post by Guffmeister on 2009-11-19
OK, I tried updating Grub, and nothing new happened. Exactly the same options are available, and all the same warnings and problems.

Hmmm.

Does anyone have any other ideas?

:)

---

