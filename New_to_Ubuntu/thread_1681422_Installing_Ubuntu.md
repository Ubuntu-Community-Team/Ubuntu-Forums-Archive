---
title: "Installing Ubuntu"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by wa953135 on 2011-02-04
Hello,

I have burned an installation disc to install Ubuntu 10.10. I would like to replace Windows Vista on a Shuttle computer.

I restart the computer and boot from disc and this starts the Ubuntu installation procedure. I then choose to install Ubuntu.

I get the error message:

**(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs**

Leaving me unable to install anything or even run from the disc without installing.

Any idea what is wrong?

Nevica

---

### Post by wa953135 on 2011-02-04
Please see attachment to see what is on my Ubuntu installation disc.

---

### Post by mharrison on 2011-02-04
> **wa953135 said:**
> .

I get the error message 'cannot mount ......'

Leaving me unable to install anything or even run from the disc without installing.

Any idea what is wrong?

Nevica


Is that the entire error message, or is there more?  The full error message would be helpful.

---

### Post by wa953135 on 2011-02-04
> **mharrison said:**
> Is that the entire error message, or is there more?  The full error message would be helpful.

I have added error message.

---

### Post by mharrison on 2011-02-04
Could you try booting off of a USB drive.  I found some old posts on that error and it seems like the solution was either adding more memory or booting off of a usb drive.  The USB instructions can be found here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Select the USB radio button and then click "Show Me How"


HTH

---

### Post by wa953135 on 2011-02-04
Hello Mat,

Unable to install using this memory stick method as well. Any ideas.

I think the problem lies with this error message:

(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Nevica

---

### Post by mharrison on 2011-02-04
How much RAM does your machine have?

---

### Post by wa953135 on 2011-02-04
4 gb

---

### Post by mharrison on 2011-02-04
Couple of things to have you try, if they are possible for you.

Can you redownload the ISO and verify the MD5.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

There are Windows and Mac instructions towards the bottom.

If this doesn't work:

Do you have a different CD/DVD drive that you could try to see if possibly there are some issues with the drive itself?

---

### Post by wa953135 on 2011-02-04
Solved,

I tried the 32 bit version of the ISO file and it worked!!!!

Thanks for your help.

Nevica

---

### Post by mharrison on 2011-02-04
Glad you got it working. 

Hope you enjoy Ubuntu.

Also, please make sure to mark your thread as solved using the Thread Tools dropdown at the top of the thread.

---

