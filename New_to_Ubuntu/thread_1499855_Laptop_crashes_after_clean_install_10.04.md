---
title: "Laptop crashes after clean install 10.04"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Peterfc on 2010-06-02
Hi

I have just done a clean install with 10.04. Almost every time i switch on i sometimes get to the login screen and put in my password or sometimes it just goes to a black screen?

Thanks for reading 


Dell Inspiron 512 Ram 40Gb H/drive

---

### Post by Arla on 2010-06-02
NVidia graphics card?

---

### Post by Peterfc on 2010-06-02
Hi Aria 

How would i check for that.

Thanks

---

### Post by jaycee23 on 2010-06-02
I've got the Nvidia 8600M GT card on my laptop and for a while all was good even had triple boot of Win 7, karmic and lucid working well BUT last week my Linux install went to pot. Just got repeated blank (thou' in my case I had vertical stripes). Spent nearly a week trawling the net for answers - even installed different distro but to no avail - have had to give up on Linux working on my laptop any more.

:cry: 

Only thing Win 7 keep chugging away - can still use it and even play games like Crysis on it!!

Go figure

---

### Post by utnubuuser on 2010-06-02
have you tried the 'nomodeset' fix?  > You might also try the "nomodeset" fix... It's a fairly common solution to a fairly common problem.

Here's a link to a how-to:[http://www.absolutelytech.com/2010/0...-ati-graphics/](http://www.absolutelytech.com/2010/0...-ati-graphics/)

Have a read through forum sticky on common issues for Lucid.

The easiest way to check the nomodeset fix is to select the kernel to boot in grub, while selected, press e then use the arrow keys to scroll to the line that begins with 'kernel', then scroll to the end of that line and add nomodeset after quiet splash, then cntrl+x to boot.


---

### Post by darkdragn on 2010-06-02
Sometimes, when it trys to load the wireless drivers, if using a broadcom chipset, ubuntu will panic and crash. My gf had the issue with a compaq mini 110c. Easily fixed, if you can get it to boot once, or force it into single user mode. Just install the broadcom sta drivers... if that's the issue, i'm trying to look up the computer info right now, but there are quite a few dell inspiron models out there... Do you have the exact model?

---

