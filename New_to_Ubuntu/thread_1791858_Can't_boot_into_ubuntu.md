---
title: "Can't boot into ubuntu"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by flee0308 on 2011-06-27
My cousin computer has a problem. After selecting ubuntu in the grub screen, this screen appears:

[http://s74.photobucket.com/albums/i259/flee0308/?action=view&current=IMG_20110627_225700](http://s74.photobucket.com/albums/i259/flee0308/?action=view&current=IMG_20110627_225700).

This is on a pure boot ubuntu btw.

---

### Post by jerrrys on 2011-06-27
no pic in that link

if you go to "advanced" when posting, you can click on the paper clip and post a pic

---

### Post by yetiman64 on 2011-06-27
You're link does not open the picture but sends me to the sign up/login page. Is your album on photobucket set for public access ?

Edit: jerrys got to it first :-)

---

### Post by flee0308 on 2011-06-27
[[IMG]http://i74.photobucket.com/albums/i259/flee0308/th_IMG_20110627_225700.jpg[/IMG]](http://s74.photobucket.com/albums/i259/flee0308/?action=view&current=IMG_20110627_225700.jpg)

Sorry about that, should have tested the photo.

---

### Post by drs305 on 2011-06-27
The best option would probably to boot the LiveCD and download/extract/run the boot info script, which will provide us with information regarding the boot files. Run the script and post the contents of RESULTS.txt

You can click on the 'BIS' link in my signature line to take you to the web page.

Since you say it's the only OS, we can try a few things (though the RESULTS.txt would be better).

Is there a backup kernel to boot?
Can your cousin boot into the recovery mode?

From the Grub2 menu (hold SHIFT during boot if you don't see it). I'll assume the Ubuntu partition is sda1 (hd0,1) - change if necessary.

Press 'c' to get to the grub prompt. If you run the following, do you get the response after the # symbol:

```
ls # Lists (hd0), (hd0,1)
ls (hd0,1)/ # vmlinuz and initrd.img
ls (hd0,1)/boot # specific vmlinuz kernel and initrd files
ls (hd0,1)/boot/grub # Lots of *.mod files 
```

---

