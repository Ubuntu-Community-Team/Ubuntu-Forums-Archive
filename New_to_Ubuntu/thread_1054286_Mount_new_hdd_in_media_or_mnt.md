---
title: "Mount new hdd in /media or /mnt?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by dphirschler on 2009-01-29
Noob question here.  I've read that /media is mainly for temporary mounts such as usb drives, but then I see my cdrom is mounted there.  So where should my second (permanent) harddrive be mounted, under /media or /mnt?  FWIW, I've tried it both ways and of course it works.  I just want to be proper.


Darryl

---

### Post by mcduck on 2009-01-29
Which ever you like better.

If you want the drive to appear on desktop and in the Places-menu, mount it into /media. If not, mount it in /mnt. (or anywhere else)

---

### Post by slinkey1981 on 2009-01-29
I mount all of my drives in /mnt. I just like it better that way. I don't think there really is a 'proper' way to do it.

Do it how you like it.

---

### Post by egalvan on 2009-01-29
> **dphirschler said:**
> Noob question here.  I've read that /media is mainly for temporary mounts such as usb drives, but then I see my **cdrom **is mounted there.  
Darryl

That's because the actual media is temporary, i.e. the CD or DVD.
Not the mechanism. i.e. the drive itself.

And as others have stated, it's now more a preference.

mainly, do you want the icon placed on the desktop automaticallty, or not.

ErnestG

---

### Post by GepettoBR on 2009-01-29
> **egalvan said:**
> That's because the actual media is temporary, i.e. the CD or DVD.
Not the mechanism. i.e. the drive itself.

And as others have stated, it's now more a preference.

mainly, do you want the icon placed on the desktop automaticallty, or not.

ErnestG

Exactly. I, for example, mount my two data storage partitions in /data and /basement - neither /media or /mnt. In ubuntu, currently, /mnt is quite a useless directory that's there for convenience, like the Music, Videos, Pictures and other folders that are created by default in your home directory. /media/* always gets a shortcut in the desktop when mounted, but other than that it's just like any other place.

---

### Post by dphirschler on 2009-01-29
Is it possible to not have a desktop icon but have it show up under 'Places'?


Darryl

---

### Post by mcduck on 2009-01-29
> **dphirschler said:**
> Is it possible to not have a desktop icon but have it show up under 'Places'?


Darryl

You can either mount the drive in /media and then disable mounted drive icons on desktop (also losing icons for all removable drives), or mount it somewhere else and then just bookmark the drive in Nautilus and it will appear in the Places menu.

---

### Post by GepettoBR on 2009-01-29
> **dphirschler said:**
> Is it possible to not have a desktop icon but have it show up under 'Places'?


Darryl

AFAIK all hard drives and external media appear under Places, even when not mounted.

---

### Post by BDNiner on 2009-01-29
You can mount them where ever you want. I mount mine in /media since i like to keep all media besides my primary disk together in the directory  tree.

---

### Post by mcduck on 2009-01-30
> **GepettoBR said:**
> AFAIK all hard drives and external media appear under Places, even when not mounted.

Only if their mount points are inside /media.

---

### Post by GepettoBR on 2009-01-30
> **mcduck said:**
> Only if their mount points are inside /media.

Are you sure? I have a dedicated GRUB partition that I've never even mounted (it's not /boot, it's a standalone GRUB) and it's in Places. My Windows partition (/windows) and the two I mentioned earlier, however, aren't up there.

---

