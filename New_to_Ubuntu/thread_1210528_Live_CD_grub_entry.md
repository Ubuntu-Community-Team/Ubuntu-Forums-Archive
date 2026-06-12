---
title: "Live CD grub entry"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-07-11
How do I find out the grub entry run on a live disk?

---

### Post by LewRockwell on 2009-07-11
I'm sorry but I don't understand your trouble-call

.

---

### Post by celticbhoy on 2009-07-11
I want to know how to view the grub entry for the live CD.

---

### Post by celticbhoy on 2009-07-11
In fact if I am reight you may be able to help me LewRockwell, do you use an Aspire One? If so what vga setting do you use for usplash in grub. The only boot that shows Usplash for from start till GDM is on my live usb. Thats why I wanted to view the grub entry, but I cant find the thing.

---

### Post by LewRockwell on 2009-07-11
During utilization of the LiveCD to load and run Ubuntu grub is not used

The only grub information on the LiveCD would be the files and data that are required to install grub, if it is necessary to do so(for multi-boot systems only).

Honestly, I've never tried to mount and view the contents of a LiveCD...

Perhaps I'll try that someday, might be interesting...

.

---

### Post by celticbhoy on 2009-07-11
In that case what vga setting is used on a live disk?

---

### Post by LewRockwell on 2009-07-11
this previous thread might be some food for thought:

[http://ubuntuforums.org/showthread.php?t=279251](http://ubuntuforums.org/showthread.php?t=279251)

.

---

### Post by celticbhoy on 2009-07-11
Cheers - will try playing with the settings.

---

### Post by LewRockwell on 2009-07-11
my Jaunty installation shows the following:

```
/etc/usplash.conf
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=640
yres=480
```

I'll continue to investigate...

.

---

### Post by celticbhoy on 2009-07-11
Cheers again will try at the low res etting to start with.

---

### Post by LewRockwell on 2009-07-11
my resolution in Jaunty is currently set at 1024 x 600, refresh rate is 60Hz, rotation is Normal

Jaunty reports my screen as ten inches but it's only 8.9(just a little guy)

I searched and found 43 files and folders with "usplash" in their names and visited several of them but didn't find anything more promising than what I gave you before referencing the 640 x 480

was wondering exactly what your project entailed?

.

---

### Post by CaptainMark on 2009-07-11
going back a bit i know you can mount and veiw the files from a usb live disk. makes it handy if you run the live session edit files and want to access them straight from usb. im on a live cd at the mo had a quick look but couldnt seem to mount the disk

---

### Post by celticbhoy on 2009-07-11
As I said it aint a project as such, just cant get usplash to work correctly in jaunty or Karmic. Both have slightly different problems, Jaunty goes to text after initial usplash during search, and Karmic stays on usplash but with no progress. The resolution in both is different, but as I say none are working.

---

