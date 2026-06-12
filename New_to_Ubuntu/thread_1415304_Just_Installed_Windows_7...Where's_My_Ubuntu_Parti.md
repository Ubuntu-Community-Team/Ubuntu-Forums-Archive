---
title: "Just Installed Windows 7...Where's My Ubuntu Partition?"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-02-24
Hi, all.

I'm hoping this didn't end up badly.  Otherwise I will be sorely disappointed in myself.

I just upgraded from Vista to 7 and made sure to do the Custom jibberjabber so I could manually point out to it to only install 7 on the correct partition (I have a severe distrust for automation).  Etc, etc, now I have Windows 7.

On startup, however, I don't have my boot options like I used to...the computer just goes straight into 7.  I know I didn't replace my whole system with 7, because the C:/ drive only has ~80GB (which is how much space I left Vista with, my HDD space is 500GB).  I'm hoping that Windows just has some stupid :):):):)ing, monopolizing, evil corporation override that is easily turned off.  

Worst case scenario, I just wiped my entire HDD clean.  Please, God, let's hope that's not the case.

---

### Post by Ozymandias_117 on 2010-02-24
Windows 7 most likely overwrote your MBR (Master Boot Record) which is where GRUB is. You will have to reinstall GRUB to be able to access ubuntu again... Let me try to find you the link

Edit: Here >> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by sandyd on 2010-02-24
> **Wataru8675 said:**
> Hi, all.

I'm hoping this didn't end up badly.  Otherwise I will be sorely disappointed in myself.

I just upgraded from Vista to 7 and made sure to do the Custom jibberjabber so I could manually point out to it to only install 7 on the correct partition (I have a severe distrust for automation).  Etc, etc, now I have Windows 7.

On startup, however, I don't have my boot options like I used to...the computer just goes straight into 7.  I know I didn't replace my whole system with 7, because the C:/ drive only has ~80GB (which is how much space I left Vista with, my HDD space is 500GB).  I'm hoping that Windows just has some stupid :):):):)ing, monopolizing, evil corporation override that is easily turned off.  

Worst case scenario, I just wiped my entire HDD clean.  Please, God, let's hope that's not the case.
You didnt.
I had the same problem.
boot up using a livecd.
chroot into your current installation
```

sudo mount -t ext4 /dev/sdax/ /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
```
grub-install /dev/sda
update-grub


replace /dev/sdax with your partition.

---

### Post by terabyte1 on 2010-02-24
Dear Wataru8675,

You need to boot up with an Ubuntu  live disk and then chroot it.

What you did when you installed Microsoft 7 is over-write your grub-loader with microsoft's. Your partitions are still there but the M/soft 1 doesn't see it being a bit thick like :rolleyes:. Booting up with a live disk allows you to put the grub back to the way it was.

Put this code in the terminal that is in Applications > accessories > Terminal in the live disk:

sudo mount -t ext4 /dev/sdax/ /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt


then type (as above): grub-install /dev/sda
update-grub  ,also in the terminal and press enter/return


Hope that helps!

terabyte :guitar:

---

### Post by Wataru8675 on 2010-02-24
Thank you graciously for your swift replies!  I just want to make sure of one thing...I'm mounting the partition that I boot from, correct?  I mean, that only makes sense...but do I have to do my /home partition, too?  Or will that be taken care of after I boot from /?

ALSO.  I just got an announcement from my LiveCD terminal that bash command "--bind" was not found...

ALSO2.  In the first post's walkthrough (at help.ubuntu.com), my LiveCD doesn't seem to want to mount any volumes......

ALSO3.  If anyone's actually following my edits, I tried mounting my /home partition instead......  Seems to be working now.  I'll let you know after reboot. *crosses fingers*

Aha.  Worked.  Thank you folks. =3

---

### Post by waynefoutz on 2010-02-24
Wataru,

I just had the same problem yesterday, the windows install on my wife's computer needed a repair install, which wiped out grub.
I used this guide to get it back.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

It worked without a hitch for me. It tells you what to do if you get an error like you did as well.

---

