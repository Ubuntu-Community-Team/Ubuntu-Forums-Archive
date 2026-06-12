---
title: "Failed 8.10 install: grub error 18"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-12-29
Hi Ubuntu Community:

I was unable to upgrade my P4 from 8.04 to 8.10, so I decided to just do a clean install of 8.10. My mobo is ASUS.

After the install, 8.10 will not boot: I get the "grub error 18."

Grub error 18 is: "Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)." ([http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors"))

I don't know what this means.

Also, I scoured the forum and found helpful links like: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

I looked for a bios upgrade on the ASUS website, but can't find one (this isn't to say that one isn't there... I just can't navigate the ASUS web site).

I need help! Can anybody recommend what I should do to get this machine working?

Thanks,
Phil Smith
Duluth, GA

---

### Post by mikeyphi on 2008-12-29
If you previously ran 8.4 on your computer - you shouldn't have any problems with 8.10.

Check the CD for errors and if none do a fresh install......
Perhaps you should confirm to us the type of install you did - full disk? or other?

---

### Post by shearn89 on 2008-12-29
I'd go for a complete reinstall, or if you're feeling brave, 
> 
1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty. (ctrl-alt-f2)
3. Type "grub"
4. type "find /boot/grub/stage1"
5. Type "root (hd0,6)", or whatever the above command returns for (hdx,y)
6. Type "setup (hd0)", or whatever hdx was.
7. Quit grub by typing "quit".
8. Reboot.


---

### Post by Old Jimma on 2008-12-29
Hi:

Thanks for your reply.

I did a check on the CD and the code corresponded exactly.

To load 8.10 I used the entire disk.

I'm using the live CD now and checked that HD with gparted. Here is what it shows:

/dev/sda1 rxt3 166GiB
/dev/sda2 extended 2.89GiB
/dev/sda3 linux-swap 2.89GiB

Thanks,
Phil

---

### Post by Old Jimma on 2008-12-29
shearn89:

When I typed "find /boot/grub/stage1" the computer replied "file not found"

Phil

---

### Post by caljohnsmith on 2008-12-29
A Grub error 18 typically happens when you have a BIOS that can't access anything on a HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. Thus if Grub's boot files or Ubuntu's boot files lie outside of that range, you would get a Grub error 18; that could be your case since your Ubuntu partition is 166 GB. Usually the way you can fix it is to create a /boot partition at the front of the drive, and then all of the Grub/Ubuntu boot files should be easily accessible by the BIOS. To do that, I would recommend reinstalling, but create a ~200 MB ext3 partition at the front of the disk, and then when you go through the installer, simply set the mount point on that partition as "/boot". How about giving that a shot and let me know how it goes. :)

---

### Post by Old Jimma on 2008-12-29
Hi caljohnsmith:

I've seen your manyreplies to similar problems other users have had. Thank you for your reply.


Here is what I've done to follow your instructions:

Started a new reinstall.

When I got to the partition editor, I chose "manual."

I partitioned the table to look like this:

/dev/sda1 ext3 /boot 197MB
/dev/sda5 swap          8MB
/dev/sda6 ext3 /     159844MB

The partitioner accepted these choices. Then I continued the install... and it worked!!

Looking back over my notes I could see that the install using the entire disks put the root partition first. THe "file not found" errors were telling me that it couldn't find grub, and the grub error 18 was telling me that it couldn't look much further than so far on my HD to find grub.

You rearranged the order of the partitions so that grub was the first partition and would be seen first within the limits of what my bios could read on the HD.

I understand your solution. Than you caljohnsmith. Feel free to come by for dinner any time. We are having saurbratten, cabbage, mashed potatoes, and Spatten Optimator this evening. I hope you do not live to far away. Send a private message if you'd like to join us this evening.



Very best regards,
Phil Smith
Duluth, GA

---

### Post by caljohnsmith on 2008-12-29
I'm really glad to hear creating a /boot partition fixed your problem. About coming by for dinner, your menu sounds wonderful, but being here in California I would have a bit of a hard time making it there on time tonight. :) If I'm ever in Georgia though, I'd love to take you up on your invitation if it still stands. Cheers and have fun with Ubuntu.

---

