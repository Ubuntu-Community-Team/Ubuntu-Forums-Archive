---
title: "[SOLVED] Booting Ubuntu question"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by sdim on 2009-01-04
Hi,everyone,and Happy New Year.
I made an installation of Kubuntu on the same hard drive where I have Ubuntu installed,and after checking it out for a bit,I decided to uninstall it.I reinstalled Ubuntu Grub so as to keep Ubuntu's initial Grub Menu,and using GParted I deleted and resized the hard drive so as to keep only Ubuntu (and a swap of about 2 GB's).
Since then,whenever Ubuntu boots up,I get the normal orange bar in the beginning (about 5 seconds),but instead of it getting filled up completely and then getting the login screen,the orange bar (and the Ubuntu logo initial screen) disappear,and a series of sentences appear (probably checks performed to boot the system).After about 10 seconds,it comes to the login screen normally.
The system is super,no hang-ups,but I'd rather get the normal boot up screen back,if possible,i.e.,the orange bar filled up completely,and then the login screen.
I made a full description so as to give the accurate picture.
Thank you.

---

### Post by Bachstelze on 2009-01-04
Please paste the output of [font="monospace"]ls -l /dev/disk/by-uuid[/font] and the contents of [font="monospace"]/etc/fstab[/font].

---

### Post by sdim on 2009-01-04
Sorry for the delay and thank you for the answer.I attach two screenshots of what you asked.

---

### Post by tomtom1982 on 2009-01-04
Had have the same problem. 

Try to open a terminal and type in:

```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sdxX
sudo blkid -c /dev/null
```

for "sdxX" you have to type your Swap-Partition (/dev/sda1 for example).

Hole thread that helped me:
[http://ubuntuforums.org/showthread.php?t=1021981&highlight=disappears](http://ubuntuforums.org/showthread.php?t=1021981&highlight=disappears)

Oh, and please NEVER make screenshots for terminal outpouts. Your second screenshot (which shows the menu.lst) doesn't shows anything. Type

```
sudo gedit /boot/grub/menu.lst
```

in terminal and give us the hole output (via copy and paste).

---

### Post by Bachstelze on 2009-01-04
> **sdim said:**
> Sorry for the delay and thank you for the answer.I attach two screenshots of what you asked.

Disregard the message above.

In your /etc/fstab, replace the line

[font="monospace"]UUID=ea5507ac-2a43-46e9-a5fa-23d70662d485 none swap sw 0 0[/font]

with

[font="monospace"]UUID=8ab1f832-4a65-40e6-96a2-5cc23ac71900 none swap sw 0 0[/font]

Then try to reboot, the problem should be gone.

---

### Post by sdim on 2009-01-04
Tried pasting the line,but it doesn't let me,saying I don't have the rights to do this.How do I go root on that one?

---

### Post by caljohnsmith on 2009-01-04
I would recommend running the commands that tomtom1982 gave, because if you simply update your fstab with the new swap UUID, that will not help you get back your splash screen; you would also have to regenerate all your initrd images. How about instead running these commands, and please post the output:
```
sudo swapoff -a
sudo mkswap -U $(awk -F"=" '{print $3}' /etc/initramfs-tools/conf.d/resume) /dev/sda5
sudo blkid -c /dev/null
cat /etc/fstab
```

---

### Post by sdim on 2009-01-04
Thanks for the help.After running the commands you suggested,I get this:

```
Setting up swapspace version 1, size = 2449876 KiB
no label, UUID=ea5507ac-2e43-46e9-a5fa-23d70662d485

/dev/sda1: UUID="2b4ea913-bdba-417c-9b35-5476d249def0" TYPE="ext3" 
/dev/sda5: UUID="ea5507ac-2e43-46e9-a5fa-23d70662d485" TYPE="swap" 
/dev/sdb1: UUID="FA54BFF754BFB52B" TYPE="ntfs" 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2b4ea913-bdba-417c-9b35-5476d249def0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ea5507ac-2e43-46e9-a5fa-23d70662d485 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by caljohnsmith on 2009-01-04
Looks good, how about rebooting and let us know how it goes. :)

---

### Post by sdim on 2009-01-04
I just did,before seeing your last post,and it has come back normally...
Great work,guys,all of you!
I'll just reboot one more time,and I'll get back to you.

---

### Post by sdim on 2009-01-04
Great work indeed,guys!You really know what you're doing.;)
I would like to express my thanks to all of you who took the time to answer and help.
Thank you.:)

---

