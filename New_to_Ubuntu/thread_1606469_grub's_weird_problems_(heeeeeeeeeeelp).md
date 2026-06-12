---
title: "grub's weird problems (heeeeeeeeeeelp)"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by 29732 on 2010-10-26
ok so...
I've resized my mother's Vista partition to install Win7 on it and when I did, (well... it didnt finish quite yet) it rebooted, and BURG was gone. Poof.
It showed me the windows boot manager, but still no BURG.
I've tried to reinstall GRUB from my liveCD and now when it did, I rebooted, and it showed me with the command prompt saying "grub>" (it said that it was in a "minimal enviroment" or something)
Help

---

### Post by 29732 on 2010-10-26
Update:
I tried to install it again and it showed me this: 
```
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 

```
i am kinda thinking that I tried something else to install GRUB.... just don't remember what

---

### Post by janpol on 2010-10-26
Here you have a guide with different methods to restore grub, I recommend you to use method Nº2: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")

> 2).Using Ubuntu 9.10 livecd or higher
Here assuming the Ubuntu partition is sda7,and /boot partition is sda6 (if you have a separate /boot partition).
Boot up ubuntu from the livecd,open terminal and run:
```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda
```

If you miss “grub.cfg” file,use following to recreate:

```
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```

After you restore grub succesfully, log into Ubuntu and run:

> sudo update-grub

Hope it helps

P.D: I am assuming you are using Lucid Lynx like your profile says, because this is for Grub 2. If you are running and older version of Ubuntu, maybe you need to restore Grub, not Grub 2

---

### Post by 29732 on 2010-10-26
> **janpol said:**
> Here you have a guide with different methods to restore grub, I recommend you to use method Nº2: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)



After you restore grub succesfully, log into Ubuntu and run:



Hope it helps

P.D: I am assuming you are using Lucid Lynx like your profile says, because this is for Grub 2. If you are running and older version of Ubuntu, maybe you need to restore Grub, not Grub 2



[ATTACH]173555[/ATTACH]
Can't update-grub and can't mount /dev/sda3

---

### Post by janpol on 2010-10-26
You should mount /dev/sda5, not the extended partition.

---

### Post by 29732 on 2010-10-26
> **janpol said:**
> You should mount /dev/sda5, not the extended partition.
Already did

---

### Post by janpol on 2010-10-26
So, you should boot from the livecd and run the following:

```
sudo -i
mount /dev/sda5 /mnt
grub-install --root-directory=/mnt/ /dev/sda
```

If you miss &#8220;grub.cfg&#8221; file,use following to recreate (it is likely that you don't need to do this):

```
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```

After that, **_reboot_**, remove the livecd, boot from the hard drive, log into your ubuntu installation using your restored Grub, and then:

```
sudo update-grub
```

---

### Post by Quackers on 2010-10-26
If you are in a Live cd environment you need to mount your root partition, which looks like sda5 to me. sda3 is an extended partition which holds sda5 & sda6

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by 29732 on 2010-10-26
Whew, thanks man, 
I'll reinstall BURG from there ;)

---

### Post by janpol on 2010-10-26
And only mount /dev/sda5....in that screenshot you mounted everything into /mnt!!!

---

### Post by Quackers on 2010-10-26
You've referred to BURG several times and GRUB as well. Which do you have, and which do you want to re-install?

---

### Post by janpol on 2010-10-26
Oh, so BURG it's a customized GRUB....just found that out xD

I recommend to use GRUB, you don't need a pretty boot loader (specially if you are only going to see it once for a few seconds on every boot) and it's not the best idea to use a boot loader that is not officially supported (see:updates xD).

---

### Post by Quackers on 2010-10-26
Yes, it gives a pictorial selection of OSes instead of just text.

---

