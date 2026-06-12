---
title: "Will an i386 installer image work on AMD?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by ben1828 on 2010-06-02
Really simple question I know, but will the USB pen drive installer image that ends "i386" work on my machine that is an AMD 64?

I note that one can download an ISO that ends in "i386" and another that ends in "AMD64". Also the USB installer (on [http://www.pendrivelinux.com](http://www.pendrivelinux.com)) only has a choice for i386 and will only load the i386 image to proceed.

As this is probably the cause of my installation problem (hangs after "select keyboard"), how would I create a USB Pen drive image for AMD?  This page   [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)   hasn't helped

Thanks

---

### Post by halitech on 2010-06-02
in theory both should work on an AMD64 machine but only the i386 image with work on a non 64bit machine.

---

### Post by ben1828 on 2010-06-02
Thank you.

The strange thing (to me) is that the USB image will load up Ubuntu fine and operate normally. So it's as if it is correct, but the installer would indicate otherwise.

From the USB load I can even connect to my WiFi and the web so is there an alternative way I can try an install from that point?  (Something like the installer app you can run from Windows)

---

### Post by 2hot6ft2 on 2010-06-02
Yes. It's a little confusing the way they named it, but the i386 will work on either a 32 bit CPU or a 64 bit one, but the x64 will only work with a 64 bit CPU.
It doesn't matter who makes the CPU just if it's 64 bit or not so the AMD64 should just be x64 since it has nothing to do with AMD.

i386 will work on a AMD whether it has a 32 or 64 bit CPU.
:popcorn:

---

### Post by ben1828 on 2010-06-02
THANK YOU!! That's very helpful - the answer I couldn't find!! :)

So I guess my installer is failing due to a different reason.

---

