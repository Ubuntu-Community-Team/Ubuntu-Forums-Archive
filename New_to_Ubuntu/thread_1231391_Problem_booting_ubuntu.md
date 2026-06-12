---
title: "Problem booting ubuntu"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by KakDela on 2009-08-04
I installed Ubuntu 9.04 using wubi. I had a bunch of driver issues but i've fixed them and it runs fine; when it boots. Fairly often, when I try to boot ubuntu, it freezes while booting. 

Here's what happens: I boot normally, when the menu comes up I select Ubuntu. Ubuntu starts to boot, and shows the following:
> 
Booting ' Ubuntu 9.04, kernel 2.6.28-14-generic'

Filesystem type is ntfs, partition type 0x07
The current working direectory(i.e., the relative path) is /ubuntu/discs
    
    [Linux-bzImage, setup=0x3000, size=0x350fb0]
    [Linux-initrd @ 0x7f878000, 0x777b8e bytes]
Normally it prints a bunch of other stuff and then goes to the ubuntu splash screen. However, fairly often it stops after printing what I wrote above, with the flashing cursor on the next line. Here I usually also hear my CPU fan loudly. The only way I seem to be able to get out of this is by doing a hard shutdown. Also, if I try to reboot immediately after I do the hard shut down, my computer often shuts itself down as soon as it turns on; its also pretty hot, so I assume this is because of overheating, but I might be wrong. It starts normally if I wait for about a five minutes after shutting it down.

any help?

---

### Post by KakDela on 2009-08-16
Anybody? Also, sometimes removing the battery (this is on a laptop) before booting seems to help.

---

### Post by jsast21 on 2009-08-16
I had the same problem when I tried wubi back in 2007 when I first switched over to linux. I gave up after several times locking up and just installed ubuntu as a dual boot. That ran a lot smoother and its easy enough to remove if you change your mind and want to go back to just windows.

Regards,

Joe.

---

### Post by nhasian on 2009-08-16
I also think you will have a better ubuntu experience if you installed Ubuntu into its own partition or drive instead of using wubi.

I know its a bit scary, but there are lots of how to guides with step by step instructions and even screenshots!  just backup any critical data like docs, music, etc before resizing your drive to be on the safe side.

---

### Post by KakDela on 2009-08-16
ok, not exactly what I was looking for,  but thanks anyway. I'll get around to installing linux in its own partition later on, but for now I'll just live with wubi.

---

### Post by ottosykora on 2009-08-27
I have installed abt 10 wubi of different flavours, but now I am also getting similar problems on wubi 9.04.

It is not able to create propper disks, creates logfile in TEMP instead with infinite size, on boot it ends up with the grub 'bash' which can not find its kernel and other things.

Some supprt here from the authors would be very nice.

---

