---
title: "Mount of filesystem failed"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-02-20
[COLOR=Black][FONT=Arial Black]Ok,I am a newbie to Linux,mainly cause I got a pc without a hard drive,and decided to install Linux on it.Well,this old pc wouldn't install[/FONT][/COLOR] [FONT=Arial Black]it,so I took the hd out,put it in my other pc,installed Linux on it and it ran great,even on the net.But when I tried the hd in the old pc,I got this mount problem.It ends with"rootBen:~_ .But I have no idea what commands to use to fix this.I first did a search and found out I could try "fsk -y /dev/sda" to fix system files.But,seems that may not be the problem since the Kubuntu 9.10 install ran well on my other pc.Please someone help.I may go try the fsck thing before I get a reply here,thanks for any help....[/FONT]

---

### Post by jmite on 2010-02-20
Is the hard drive SATA or IDE? Did that particular hard drive come with the old computer? Has it ever worked with the old computer?

When it says "failed to mount," where are you booting from? Are you booting from a CD, or is it booting from the hard drive?

If it's booting from CD, my guess is that this is not a linux problem but a BIOS problem. Figure out how to get into your BIOS (it's different for each computer, it should say when you boot up, if not google it). Look and see if it has any settings about attached disks and boot media and such. Also, if the drive is IDE, look and see how its jumpers are set. It's a little plasic piece physically on the hard drive, that designates if its "master" or "slave." If it's set to slave, and you've only got one hd in the computer, that could likely be causing your problem.

---

### Post by nos09 on 2010-02-21
ok i had similar problem someday before and i tried to unmount all the drives.

the code is 

> umount -ah

and try umount --help for more option. i m sure u will find one of the appropriate if the previous one does not work.

---

