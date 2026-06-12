---
title: "USB devices in VirtualBox"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by patilkaustubhv on 2009-05-10
hi...

My USB mouse works fine with Virtual XP with VirtualBox...but my pen-drives are not detected nor is my memory card reader....


is there any solution to this.... I use VirtualBox 2.2 closed source.... and 8.10

(I haven't disabled any of the usb devices.....)

---

### Post by Legace on 2009-05-10
Are you using virtualbox-ose?
The OSE version doesn't support USB.

You need to download VirtualBox from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) for it to have USB support :)

---

### Post by spcwingo on 2009-05-10
I used these instructions to get USB support going on Hardy with vbox 2.1.4:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html]("http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html")

---

### Post by patilkaustubhv on 2009-05-10
NO i do not use OSE version

---

### Post by spcwingo on 2009-05-10
Neither do I, but I still had to do what I mentioned above to enable USB support.

---

### Post by Ocxic on 2009-05-10
You also have to give the virtual machine your using access to you USB devices in the USB settings for your virtual machine.

---

