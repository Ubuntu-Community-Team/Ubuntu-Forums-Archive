---
title: "Operating system not found"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by Friwise on 2010-11-26
Hi!!!!!
Today when I turned on the laptop (a HP pavilion ze5375us) it was really slow and finally told me that operating system not found.
I tried to change boot order and when I turned it to default order it finally gave me options to choose between some 5 ot 6 options that I unfortunately dont remember and now when I restart it(I have to turn it on holding for some seconds the turn on button) it doesnt give any message hust black page with one **-** lighting.

Please help me!!!!
Thanks in advance

---

### Post by dhiman33 on 2010-11-26
U need to provide more information for people to help. What operating systems did u have? Can u guess what might cause this problem?(things u did last time that might cause this.)

---

### Post by Friwise on 2010-11-26
Hi!!!
Thanks for answering!
I have Linux Ubuntu 10.10.
Last time I was using it I was trying to connect to a wireless network (with no result) so I shut it down.
This laptop has 2,40Ghz and 487MB ram and 40GB
I really need help!
Thank you again

---

### Post by sikander3786 on 2010-11-26
First of all make sure that Bios is properly configured to boot from the hard disk that contains the OS.

If thats not the problem, please post the output of bootinfoscript as per instructions here. You'll need to boot off an Ubuntu Live CD.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap the output using proper code tags # from the post menu. [/code] at the end and [code] at the beginning.

It would tell us nearly everything related to your boot setup and therefore we'll be able to advise accordingly.

Thanks.

---

### Post by dhiman33 on 2010-11-26
Here's a link that might help u---this describes the ways of restoring grub.."http://ubuntuforums.org/archive/index.php/t-24113.html". Hope this helps u.

---

### Post by Friwise on 2010-11-26
I chose Hard Disk to be first in Boot order and it when it reboot it gave me the message error: invalid environment block.

---

### Post by sikander3786 on 2010-11-26
> **Friwise said:**
> I chose Hard Disk to be first in Boot order and it when it reboot it gave me the message error: invalid environment block.
Ok. Please boot from a Live CD and post the output of bootinfoscript as mentioned in my above post. Only then we'll know the problem exactly...

---

### Post by Friwise on 2010-11-26
Thanks Sikander!
I have no Live CD at the moment! Is there any other solution?

---

### Post by sikander3786 on 2010-11-26
Live USB. (if your Bios supports boot from USB)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbooin.sourceforge.net](http://unetbooin.sourceforge.net)

You'll need an Ubuntu image for that.

And you definitely need a Live CD/USB in order to diagnose or fix that.

---

### Post by Friwise on 2010-11-26
The image I have now is:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/8a0b75c3-8f66-47a2-9a14-4eca2401317a does not exist.
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initfrands)

---

