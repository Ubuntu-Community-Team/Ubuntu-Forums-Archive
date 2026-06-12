---
title: "Installing onto x86 laptop that is not an Adam?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by wx1gdave on 2009-08-14
I would like to install Jaunty onto a Dell laptop that does not have an Adam processor.  The optical drive is unreliable, so, I'd like to install from a USB stick.  I cannot find an ".img" file, made from the ".iso" desktop image.  Will the netbook remix work on processors that are not Adams?  

I will be creating this installation medium on a Mac, running Leopard.  I've already found instructions for putting the '.img' file onto a usb stick, and can handle that.  If the netbook remix will not work, how can I create or where do I find an ".img" file, made from the Jaunty i386 desktop installation cd?:confused:

---

### Post by cmannnn on 2009-08-14
you can download it from ubuntu.com

---

### Post by sandyd on 2009-08-14
[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

---

### Post by mrbiggbrain on 2009-08-14
use uNetbootin to create USB installers from any linux ISO :-) enjoy

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by wx1gdave on 2009-08-15
Thanks, but there isn't a unitbootin for Macos.

---

### Post by wx1gdave on 2009-08-16
I downloaded the Netbook Remix usb image and wrote it to a fat-32-formatted flash drive, using the "dd" command, as suggested in the community documentation.  The result was a non-bootable drive.  I flagged the first partition as "active" and performed a "update" using Apple's fdisk utility.  Drive is still not bootable.:(

---

