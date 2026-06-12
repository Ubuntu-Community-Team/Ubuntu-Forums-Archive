---
title: "Why can't I use the SD slot in LXDE?"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by sam.pulis on 2009-09-14
Hello all, new here, I started with Linux and Ubunntu just recently (maybe 6 months ago) so I know very little about it.  I had installed Ubuntu on my EEE 900 and on my new Atom driven nettop from MSi.  It worked really well for the most part but certain things did not work well at all, like youtube videos and other web applications like photobucket.  I went out seeking a lighter alternative to Ubuntu and came across some news articles about Lubuntu which said it used much less resources than ubuntu and the main difference is that it uses the LXDE window manager instead of what ubuntu uses, GNOME i think?  Anyway i went ahead and installed LDXE as per their instructions:  ```
 sudo aptitude install lxde
```  
LXDE works great, Youtube works perfectly and the computer runs alot faster.  The only problem is that now I can't use the SD card slot in the front of the computer which stinks because I need that to work.  Same thing on the netbook.  These worked when i was using GNOME.  Is there anything i need to do to get it to work?  The window manager shouldn't have affected this at all right?  Also, after that didn't work i put the card back in my camera and dug up the USB cable and plugged that into the various USB ports in front and behind with no luck.  It wasn't popping up the window or placing the icon for the device on my desktop.  Is there something else i need to do?  Something like sudo mount whatever whatever?  Is there a way to have it automatically appear when I put the card in like in gnome?  because that is just so convenient and logging out to log back in under gnome just to copy pictures over is a hassle i'd rather not have to do.  Thanks.

---

### Post by Bachstelze on 2009-09-14
Insert a card and run

```
dmesg | tail
```

and paste what you get. Your SD card reader is probably working fine, it's just that the card doesn't get automounted.

---

### Post by halitech on 2009-09-14
I don't think LXDE does automounting or showing the icon for the drive on the desktop but there are apps like pmount and manual mounting. with the drive plugged in, open a terminal and run```
sudo fdisk -l
```then you can use```
sudo mount /dev/sdXX /media/thumbdrive
```
change sdXX to whatever the drive is and /media/thumbdrive to whatever you want the mount point to be

---

### Post by sam.pulis on 2009-09-14
> **Bachstelze said:**
> Insert a card and run

```
dmesg | tail
```

and paste what you get. Your SD card reader is probably working fine, it's just that the card doesn't get automounted.

I figured that was the problem.  When i do dmesg | tail it says this

```
x@desktop:~$ dmesg | tail
[123978.669630] [drm:i915_getparam] *ERROR* Unknown parameter 6
[123979.273383] [drm:i915_getparam] *ERROR* Unknown parameter 6
[161443.596487] [drm:i915_getparam] *ERROR* Unknown parameter 6
[161443.640889] [drm:i915_getparam] *ERROR* Unknown parameter 6
[162043.669894] [drm:i915_getparam] *ERROR* Unknown parameter 6
[163300.765074] [drm:i915_getparam] *ERROR* Unknown parameter 6
[165542.418825] mtrr: no MTRR for e0000000,10000000 found
[165544.261210] [drm:i915_setparam] *ERROR* unknown parameter 4
[165544.261260] [drm:i915_getparam] *ERROR* Unknown parameter 6
[165544.861408] [drm:i915_getparam] *ERROR* Unknown parameter 6

```
:confused:

---

### Post by sam.pulis on 2009-09-14
> **halitech said:**
> I don't think LXDE does automounting or showing the icon for the drive on the desktop but there are apps like pmount and manual mounting. with the drive plugged in, open a terminal and run```
sudo fdisk -l
```then you can use```
sudo mount /dev/sdXX /media/thumbdrive
```
change sdXX to whatever the drive is and /media/thumbdrive to whatever you want the mount point to be

Is there a way to set it up so that when i put the sd card in it just works?  I don't mind doing things in terminal and wish I knew more commands etc..  but my wife wants nothing to do with terminal and that slot is going to be used by her quite often.  Also, fdisk?  isn't that going to erase the disk?  sorry I'm sure thats a dumb question.

---

### Post by kerry_s on 2009-09-14
did you even try lightning gnome? it has a setting for reduced resources & the effects can be turned off, lighter programs can be used in place of the heavier ones.
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

---

### Post by sam.pulis on 2009-09-14
No, I had not tried that.  Thanks for the link.  Maybe that will work out better than LXDE.  :)

---

### Post by halitech on 2009-09-14
> **sam.pulis said:**
> Is there a way to set it up so that when i put the sd card in it just works?  I don't mind doing things in terminal and wish I knew more commands etc..  but my wife wants nothing to do with terminal and that slot is going to be used by her quite often.  Also, fdisk?  isn't that going to erase the disk?  sorry I'm sure thats a dumb question.

Pmount can be used to mount and unmount devices, I just wanted to confirm the device is being seen with the terminal commands.

---

### Post by sam.pulis on 2009-09-14
ok, i popped the card out and put it back in and then the dmesg | tail command worked.  I guess it wasn't inserted properly :rolleyes:

```
[ 4925.273305] sd 4:0:0:0: [sdb] Write Protect is off
[ 4925.273317] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4925.273324] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4925.276824] sd 4:0:0:0: [sdb] 31387648 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[ 4925.278277] sd 4:0:0:0: [sdb] Write Protect is off
[ 4925.278285] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4925.278290] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4925.278302]  sdb: sdb1
[ 4925.279426] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 4925.279617] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

I used hailtechs instructions had to sudo mkdir /media/EOS_DIGITAL to make it work.  OK so its mounted and now shows in the file manager but does not pop up on the desktop. 

Before I did that, I did sudo apt-get install pmount but putting hte disk in seemed to have no effect when i put the card in.  :confused:  Any tips how to make it auto mount?

---

### Post by cariboo on 2009-09-14
Have a look at autofs, it is in the repositories.

---

### Post by kerry_s on 2009-09-15
i don't think pcmanfm shows devices on the desktop, it only shows what's in ~/Desktop if i remember right.

---

### Post by halitech on 2009-09-15
> **sam.pulis said:**
> ok, i popped the card out and put it back in and then the dmesg | tail command worked.  I guess it wasn't inserted properly :rolleyes:

```
[ 4925.273305] sd 4:0:0:0: [sdb] Write Protect is off
[ 4925.273317] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4925.273324] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4925.276824] sd 4:0:0:0: [sdb] 31387648 512-byte hardware sectors: (16.0 GB/14.9 GiB)
[ 4925.278277] sd 4:0:0:0: [sdb] Write Protect is off
[ 4925.278285] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4925.278290] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 4925.278302]  sdb: sdb1
[ 4925.279426] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 4925.279617] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

I used hailtechs instructions had to sudo mkdir /media/EOS_DIGITAL to make it work.  OK so its mounted and now shows in the file manager but does not pop up on the desktop. 

Before I did that, I did sudo apt-get install pmount but putting hte disk in seemed to have no effect when i put the card in.  :confused:  Any tips how to make it auto mount?

PCManfm doesn't show things on the desktop from what I can remember so  you would need to open PCManfm. To use Pmount, you would need to add it to your taskbar so you can click on it to mount devices. To unmount,  you would use
```
sudo umount /media/EOS_DIGITAL
```

---

