---
title: "When I Double click my USB Drive..."
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-02
It doesn't mount, it gives the following error:
> mount: wrong fs type, bad option, bad superblock on /dev/sdb1,        missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail  or so

dmesg | tail:

```
[  143.937392] FAT: IO charset ANSI_X3.4-1968 not found
[  143.962748] FAT: IO charset ANSI_X3.4-1968 not found
[  976.334623] FAT: IO charset ANSI_X3.4-1968 not found
[  976.351019] FAT: IO charset ANSI_X3.4-1968 not found
[  981.138447] FAT: IO charset ANSI_X3.4-1968 not found
[  981.155016] FAT: IO charset ANSI_X3.4-1968 not found
```

Manually mounting it with the following command:
```
sudo mount -t vfat /dev/sdb1 /media/disk -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```
works however. This is a mini.iso install with xfce4 metapackage. Installing default Ubuntu or Xubuntu has this working out of the box; however, due to limited memory resources, I would rather not take up half of my memory at once just by surfing the web on sites that have flash ads in order to listen to music using flash media players (IE: Newgrounds) using Midori Web Browser.

---

### Post by gsmanners on 2010-01-02
Have you tried putting in an entry for /etc/fstab? I guess it would be something like:

```
/dev/sdb1 /mnt/usb vfat rw,noauto,user,utf8,dmask=027,fmask=137 0 0
```

---

### Post by Psumi on 2010-01-02
Thank you, I used /media/disk instead of mnt/usb however (since that was how it was before.

Also, you didn't tell me that I had to put a new blank line at the end of fstab to avoid warnings/errors.

---

### Post by gsmanners on 2010-01-03
Using /etc/fstab was pretty standard for a long time. It's only just recently that we have nice things like udev and hal doing all the work for us.

I don't actually have a blank newline. That's just the way vBulletin formats "code" blocks (redundant space for scrollbars?).

---

### Post by Psumi on 2010-01-03
> **gsmanners said:**
> Using /etc/fstab was pretty standard for a long time. It's only just recently that we have nice things like udev and hal doing all the work for us.

I don't actually have a blank newline. That's just the way vBulletin formats "code" blocks (redundant space for scrollbars?).

No, there was an error message when I double clicked it after I added your line, it said it needed a blank new line at the end of fstab.

Ubuntu 9.10 barely has any hal implementation (And 10.04 removes it completely.) xfburn doesn't work on 9.10 because of this, hence why Xubuntu uses brasero.

---

### Post by gsmanners on 2010-01-03
Oh, okay. Thanks for clearing that up. Yeah, there is an extra newline at the end of /etc/fstab. That should have been apparent in a text editor.

No hal in 10.04? That's funny because Worker just added support for that a few weeks ago.

---

