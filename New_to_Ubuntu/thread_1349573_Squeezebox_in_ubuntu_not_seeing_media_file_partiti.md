---
title: "Squeezebox in ubuntu not seeing media file partition"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by mcbry on 2009-12-08
Hi,

I have just installed ubuntu 9.1 in a dualboot configuration with XP.  My media files are in a third partition (FAT32). I was running Squeeze Server in XP, and I have now set it up to run in Ubuntu.  The problem is that the Squeeze Server does not see my media files partition, even though it is mounted in /media.  Any thoughts?

Thanks in advance for reading and any help you can provide.  I am a newbie, but very excited ot be joining the Ubuntu community.

Bryan

---

### Post by wanye on 2009-12-18
i'm having the same issue. had everything working fine with squeezecenter and ubuntu 9.04, but then did a clean install of 9.10 and squeezeboxserver, and now the only mounts in /media i can see are /media/cdrom and /media/cdrom0

any suggestions?

---

### Post by nothingspecial on 2009-12-18
I`m using squeezecenter, or squeezebox server or what ever they call it at the moment.

Can you please elaborate on your problem. When you say it doesn`t see your media files partition, what do you mean?

---

### Post by wanye on 2009-12-18
when i go to select the usb drive with my music store on (/media/700gb/mp3) then it isn't viewable/accessible in the new squeezebox setup screen. i'm assuming it is something to do with permissions (the new squeezeboxserver creates a user of its own, im pretty sure previous versions didnt do that)

heres the last few lines of when i set up squeezeboxserver (and the contents of my /media folder)

> Setting up squeezeboxserver (7.4.1) ...
Adding system user `squeezeboxserver' (UID 118) ...
Adding new user `squeezeboxserver' (UID 118) with group `nogroup' ...
Not creating home directory `/usr/share/squeezeboxserver'.
 * Reloading AppArmor profiles                                                                           Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox-3.5

wanye@babydweezil:/media$ ls -al
total 48
drwxr-xr-x  6 root   root    4096 2009-12-18 09:32 .
drwxr-xr-x 21 root   root    4096 2009-12-18 12:42 ..
drwx------  1 wanye wanye  8192 2009-11-19 19:22 1tb
drwx------  1 wanye wanye 24576 2009-11-19 14:16 700gb
lrwxrwxrwx  1 root   root       6 2009-05-23 15:15 cdrom -> cdrom0
drwxr-xr-x  2 root   root    4096 2009-05-23 15:15 cdrom0
drwx------  4 wanye wanye  4096 1970-01-01 01:00 EOS_DIGITAL
-rw-r--r--  1 root   root       0 2009-12-18 09:30 .hal-mtab


ive tried adding the new user to various usergroups:

> wanye@babydweezil:/media$ sudo adduser squeezeboxserver wanye
Adding user `squeezeboxserver' to group `wanye' ...
Adding user squeezeboxserver to group wanye
Done.
wanye@babydweezil:/media$ sudo adduser squeezeboxserver root
Adding user `squeezeboxserver' to group `root' ...
Adding user squeezeboxserver to group root
Done.


screenshot of SBS attached showing what i mean by "not seeing"

---

### Post by wanye on 2009-12-18
hmm. not the most elegant of fixes, but it seems to work so far:

edit fstab:
sudo pico /etc/fstab

and add in:
/dev/sdc1 /media/700gb ntfs-3g rw,exec,utf8 0 0

(this will vary depending on what device the drive is mounted, drive format, etc)

reboot, and squeezeboxserver seems to see the mount ok.

---

### Post by lucbra on 2009-12-28
Hello,
I tried this tweak but it can't see my mounted USB drive (Iomega_HDD)

The only amps that I can see under media are cdrom, cdrom0, floppy and floppy0.

any help?

Thanks

---

### Post by arkid77 on 2010-01-08
hi all

im having exactly the same problem having installed ubuntu 9.10 fresh today. i installed the latest squeezebox server 7.4.1 and in unbutu i see my usb mounted drive under the /mount folder with no problem. however from the web interface in the server setup only 2 cdrom folders appear under /mount when i go to select my music location.

---

### Post by wanye on 2010-01-08
> **arkid77 said:**
> hi all

im having exactly the same problem having installed ubuntu 9.10 fresh today. i installed the latest squeezebox server 7.4.1 and in unbutu i see my usb mounted drive under the /mount folder with no problem. however from the web interface in the server setup only 2 cdrom folders appear under /mount when i go to select my music location.

have you tried adding the drive in your fstab as i detailed above?

you just need to find out the actual devicename of the drive (ie /dev/sdc1)

as detailed in [http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)
# device name   mount point     fs-type      options                 dump-freq pass-num
(mine as as follows:)
/dev/sdc1 /media/700gb ntfs-3g rw,exec,utf8 0 0

---

### Post by nothingspecial on 2010-01-08
Try ```
chmod -R a+rX /mount/music_drive
```

or whatever it`s called.

---

### Post by arkid77 on 2010-01-21
hi all

thanks for responses. i got it working by ignoring the /media folder mount area. i created a new folder under /mnt and then added following to my fstab

/dev/sdb1   /mnt/MusicDisk  nffs  rw,allow_other 0 0 


Thanks for the input!

---

### Post by nosnowking on 2010-01-28
As arkid77 said (kind of) create folders as root in the /media folder

Didin't work for me until I installed samba (it was a fresh install of karmic), then it all worked fine

---

### Post by loweryjk on 2010-05-08
Simply set the permission on the partition and the music folder to allow anyone to read it.

---

