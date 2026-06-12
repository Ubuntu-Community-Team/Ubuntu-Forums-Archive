---
title: "making an iso to load on usb."
date: 2011-01-11
forum: New to Ubuntu
---

### Post by topher-t-mill on 2011-01-11
I have had trouble installing extra software and settings to USB sticks and would like to make an iso of an hard disk, I have had no success with g4l and whilst I have installed partimage I cannot locate it to be able to attempt to use it. help please.

---

### Post by bodhi.zazen on 2011-01-11
Try remastersys

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

If you need more then that you will need to do some reading

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by topher-t-mill on 2011-01-12
Please can I break into this topic as I had no reply to a question about making an iso to install on a flash drive ,as I find that  extra software does not install to the drive, I have done ordinary installs to a hard drive and then put it into a usb case but that is a bit cumbersome but it does work. is the answer to do an ordinary install to a flash drive. or make an iso of the  particular hard drive and then use usb creator?

---

### Post by howefield on 2011-01-12
Post sliced from Testimonials & Experiences thread, and merged with your original post on the subject.

Please keep support questions for the support forums.

---

### Post by C.S.Cameron on 2011-01-12
> **topher-t-mill said:**
> Please can I break into this topic as I had no reply to a question about making an iso to install on a flash drive ,as I find that  extra software does not install to the drive, I have done ordinary installs to a hard drive and then put it into a usb case but that is a bit cumbersome but it does work. is the answer to do an ordinary install to a flash drive. or make an iso of the  particular hard drive and then use usb creator?

Remastersys will make an iso of a Full install.

I usually do a full install to thumb drive which works for me. If I need a second copy I use dd to clone the drive.

---

### Post by topher-t-mill on 2011-02-10
Thank you, and of course sorry to break into wrong thread. I did manage to do roughly what I wanted, in two different ways, partly by using UCK to make a customised cd but that was not altogether brilliant. So I had a fairly well populated version of mint which I copied using GParted, but I was unable to get it to boot till I installed mint in another partition and Grub then allowed me access to it, and I now have a portable working system.

---

