---
title: "kubuntu: USB booting not working"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by vkbidve on 2011-06-01
Hi,

I downloaded the iso image of latest kubuntu 11.04, made a startup USB stick through ubuntu 10.04 and tried it on my laptop after changing the boot sequence in its setup.

The laptop gave 'Boot Error' message and stuck. After pressing a key, it went to other boot devices and started grub.

But on another PC, the same USB stick worked just fine! I could try kubuntu very well.

What is this 'boot error' thing? and how to remove it? :(

---

### Post by mastablasta on 2011-06-01
my USB key with Ubuntu is ignored on one computer and works nicely on another. so perhaps hardware (USBkey) is not compatible with the computer you try to boot from?!

---

### Post by vkbidve on 2011-06-01
> **mastablasta said:**
> my USB key with Ubuntu is ignored on one computer and works nicely on another. so perhaps hardware (USBkey) is not compatible with the computer you try to boot from?!

It doesn't look so, as the usb stick is detected in windows and in old installtion of ubuntu on the same laptop.

---

### Post by jre6 on 2011-06-01
Delete all the files that the startup disk creator made. You may have to search for some files and folders which have a "." in the beginning of the name, and so they are invisible.

Then, make your USB drive bootable with UNetBootin, and report if it works.

---

### Post by vkbidve on 2011-06-01
But while making the startup disk, i deliberately clicked on 'Erase Disk' button.

Also, the same stick is working fine on another pc without making any such modifications.

---

### Post by mastablasta on 2011-06-01
> **vkbidve said:**
> It doesn't look so, as the usb stick is detected in windows and in old installtion of ubuntu on the same laptop.
 
 
same/similar here. i can see it in Windows but it still doesn't boot. 
 
Oh yes perhaps erase disk doens't erase all.
hmm i haven't reied formating it. in my case i think it even worked before. htough i am not sure since it's been a while when i put the OS on this USBdisk. other USB works fine.

---

### Post by vkbidve on 2011-06-01
But still, my question remains as it is. Why ***THE SAME*** usb stick works on other pc very fine and doesn't boot at all on my laptop?

---

