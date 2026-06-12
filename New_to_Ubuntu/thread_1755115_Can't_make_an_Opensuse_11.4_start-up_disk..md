---
title: "Can't make an Opensuse 11.4 start-up disk."
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Kafubie on 2011-05-10
I'm using Xubuntu 11.04.

Now, I'm not sure if i'm getting something here, but none of the Opensuse 11.04 iso's work for making a start-up disk.

I can have any other distro work with the start-up disk creator.  But not just Opensuse.  You can select it with the "other" tab, but it isn't shown on what iso you selected before actually creating a live-usb.

Unetbootin selects the .iso, and when I create a live-usb it goes very fast and in the end, it doesn't even have the image on it.


Now.. Please tell me what's wrong.
thanks.


Hopefully i don't feel stupid.

---

### Post by mikewhatever on 2011-05-11
The Startup Disk Creator is not intended for dealing with any non-*buntu isos. There is an image writer somewhere on the OpenSuse site, but the easiest way to write that iso in Ubuntu is with with dd.

```

sudo dd if=/path-to-iso of=/dev/sdX bs=4096

```

Note: Be extra careful to select the correct device (/dev/sdx), double check, until you know for sure what it is.

---

### Post by gandaran on 2011-05-11
ubuntu start-up disk creator only works with ubuntu distributions, for opensuse you have to use unetbootin but I have never been able to install opensuse from a live usb pen drive, it always shows some error about cd drive so the only way it works is to burn the opensuse iso to a cd/dvd.

---

### Post by bennachie on 2011-05-11
openSUSE 11.4 images are in hybrid iso format. Using the "dd" method outlined by an earlier contributor produces a bootable USB stick with persistence enabled - which is a neat trick.

---

### Post by Kafubie on 2011-05-11
> **mikewhatever said:**
> The Startup Disk Creator is not intended for dealing with any non-*buntu isos. There is an image writer somewhere on the OpenSuse site, but the easiest way to write that iso in Ubuntu is with with dd.

```

sudo dd if=/path-to-iso of=/dev/sdX bs=4096

```

Note: Be extra careful to select the correct device (/dev/sdx), double check, until you know for sure what it is.

I've tried to boot it up after this.  Just a blank screen.

---

### Post by mikewhatever on 2011-05-11
Was the device blank when you wrote the iso?
What was you command you used?

---

### Post by Kafubie on 2011-05-11
> **mikewhatever said:**
> Was the device blank when you wrote the iso?
What was you command you used?

I did what you told me, the USB was renamed "openSUSE-Live-cd"
There was bootloading folders in there, so I shutdown and tried to boot from usb.  I tried this on two different computers also.  Maybe I did something wrong.

Results:  Just your typical black screen white cursor.

---

### Post by C.S.Cameron on 2011-05-11
MultiBootUSB will make a bootable iso of Opensuse.

---

### Post by mikewhatever on 2011-05-11
I've had better results writing ISOs with dd, when working with previously formatted USB sticks, in fact, just erasing the file system with the Disk Utility should be enough.

---

### Post by Kafubie on 2011-05-12
I've been researching the problem and trying many methods so many times.  Just not working.  

I'll give up for now, it's getting me stressed.

---

### Post by Durden on 2011-05-12
Try the opensuse forums.

---

### Post by Kafubie on 2011-05-12
> **Durden said:**
> Try the opensuse forums.

Will do!

---

