---
title: "no internet at home"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by guitar dave on 2011-06-30
I have a unique situation...I have internet at work, but not at home.  The PC at work is an older dell, the one at home 64x windows 7, on which I've installed Ubuntu to run along side Win 7.

How do I transfer (via usb drive) programs I download at work, and install on the one at home?
(Also, one is 32x and the other 64x)

Any help would be appreciated.

---

### Post by dFlyer on 2011-06-30
Copy the programs to the usb drive, hopefully they are deb file. Than transfer the programs to your ubuntu computer. If they are deb files you can just click on they and install they or from the command line you can use:

dpkg -i "nameofpackage.deb" without the quotes.

One problem with the above is that if there are other libs required you will need a network connect to pull in the libs.

---

### Post by georgelab on 2011-06-30
Look for ia32 libs

---

### Post by createdcreature on 2011-06-30
The deb packages need dependencies that need to be downloaded from the internet, so it is  almost impossible. If you really need it, get them from here [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/).

---

### Post by guitar dave on 2011-06-30
Does the Software Center give the option to save to USB?

---

