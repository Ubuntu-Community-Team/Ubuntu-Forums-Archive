---
title: "Can't get back to Windows Vista"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by GoogleBoy on 2009-10-14
Windows Vista 32-bit operating system.

I downloaded the Ubuntu iso, got it all going, installed it. And then I noticed I didn't download Wubi when I was on Windows. I've tried downloading  it on Ubuntu, is there anything I can do to get rid of Ubuntu from Ubuntu? I don't have the Recovery CD.

---

### Post by lestatius on 2009-10-14
If you bought your pc from a store there might be a recover partition. if you press I think f12 or another one of those  f keys you can have an option to recover from a selected partition. Otherwise you might need download windows vista from torrent and use your key on the side of the pc and then install windows and drivers again.

---

### Post by GoogleBoy on 2009-10-14
I was thinking about the Recovery on boot. But when I press they key, it doesn't respond.
The key is F11.

If I have to resort to downloading Windows Vista, will my data on Windows still be there?

---

### Post by Kazade on 2009-10-14
> **GoogleBoy said:**
> I was thinking about the Recovery on boot. But when I press they key, it doesn't respond.
The key is F11.

If I have to resort to downloading Windows Vista, will my data on Windows still be there?

When you are inside Ubuntu, can you see your Windows disk under the Places menu?

If you can't, then you might have overwritten the whole disk with the Ubuntu installation.

---

### Post by LewRockwell on 2009-10-14
```
sudo fdisk -l
```

---

### Post by Merk42 on 2009-10-14
> **LewRockwell said:**
> ```
sudo fdisk -l
```

If this post isn't clear, please run this in a terminal
Applications > Accessories > Terminal

You can just copy/paste the part quoted to make sure you don't mistype it.  You will be asked for your password, after that copy/paste the output back here.

---

### Post by GoogleBoy on 2009-10-14
Yeah, I probably did overwrite it. I don't see the disk.

That's what I got from sudo.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38160   306520168+  83  Linux
/dev/sda2           38161       38913     6048472+   5  Extended
/dev/sda5           38161       38913     6048441   82  Linux swap / Solaris

I can't find find Windows OS, or anything like it.

---

### Post by LewRockwell on 2009-10-14
Parted Magic LiveCD has some utilities on it that might help you if you feel inclined to investigate data recovery

[http://partedmagic.com/](http://partedmagic.com/)

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://en.wikipedia.org/wiki/Photorec](http://en.wikipedia.org/wiki/Photorec)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

.

---

### Post by LewRockwell on 2009-10-14
once you get your machine and operating system(s) the way you want them then you can use Clonezilla(included in the Parted Magic LiveCD Utility Suite) to make an exact clone of your partition(s) and/or complete hard drive(s) so that...

if this ever happens again you can just slip your most recent clone back-up in, and away you go again...with just a little bump in the road

also, additional informational links included:

[http://clonezilla.org/](http://clonezilla.org/)

[http://sourceforge.net/projects/clonezilla/](http://sourceforge.net/projects/clonezilla/)

[http://en.wikipedia.org/wiki/Clonezilla](http://en.wikipedia.org/wiki/Clonezilla)

.

---

