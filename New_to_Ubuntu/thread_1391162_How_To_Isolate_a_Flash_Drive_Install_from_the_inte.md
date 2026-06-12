---
title: "How To Isolate a Flash Drive Install from the internal hard drive"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Pgohara on 2010-01-26
I have installed unr on a flash drive on a samsung netbook. My wife wants to access her company's network with a citrix client. I don't want my equipment hooked up to their network at all. I though this might be a good compromise. However I would like to isolate the unr flash drive installation from the internal hard drive. That way what happens on unr stays on unr. I just unplug it. However, I need to know how to create an account for her in unr that will isolate itself from the internal hard drive on the samsung. No drive, no files, no read, no write, no drive (what drive). I have very little linux experience. I wasn't sure this was the place to post this. Any help is appreciated. Thanks.

---

### Post by nhasian on 2010-01-26
okay it sounds like you dont want to access the internal hard disk at all while your running ubuntu from the flash drive.  thats no problem, just dont mount the internal hard disk and it will not be accessible.

---

### Post by bodhi.zazen on 2010-01-26
If the hard drive is pluged in you can access it (via root) from the USB.

The only way to prevent this would be with apparmor, it would not be too hard, give root a new shell, and allow everything, but deny access to your hard drive (by /dev).

If you are not familiar with apparmor, just disconnect the hard drive when you boot from the flash drive.

---

### Post by Pgohara on 2010-01-26
Thanks for the replies.

Nhasian, as I said, I have very little linux experience. How to unmount or not mount the internal drive is not apparent to me. I have experimented with the drives that are showing in the systems area but I have not discovered how to mount/unmount the drives. I am sure it is something simple but I am missing it.

bodhi.zazen, physically dismantling the drive from the machine isn't an option. The part about apparmor is way over my head. Thanks for the suggestions.

---

### Post by bodhi.zazen on 2010-01-26
> **Pgohara said:**
> bodhi.zazen, physically dismantling the drive from the machine isn't an option. The part about apparmor is way over my head. Thanks for the suggestions.

Then you will have to settle for the fact that the HD is accessible from the USB boot.

It should not automatically mount , but it is and will be available.

---

### Post by nhasian on 2010-01-27
oh i just thought of another option. you could enter the computer's bios and disable the hard disk controller.

---

### Post by lotharmat on 2010-01-27
> **nhasian said:**
> oh i just thought of another option. you could enter the computer's bios and disable the hard disk controller.


That could be a wee bit of a ball ache to remember to re-enable it when you want to use the computer..

---

