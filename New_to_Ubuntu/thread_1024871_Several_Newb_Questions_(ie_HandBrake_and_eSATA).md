---
title: "Several Newb Questions (ie HandBrake and eSATA)"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by stealle on 2008-12-29
I have a new Asus laptop with an eSATA port. It's running Windows Vista. I'd like to run Xubuntu on an external hard drive hooked up via this eSATA port (since that should be faster than USB). Here are my questions.

After I am up and running, will Xubuntu (on the external hard drive) recognize my internal hard drive? For example will I be able to run Handbrake from within Xubuntu to transcode video but store the files on the internal hard drive. If so, will this mess with Windows Vista?  Also, when I boot into Vista will I see and be able to use the files I created while under Xubuntu. 

Kinda cunfusing... basically I'm asking if I will be able to share files back and forth between the Vista internal hard drive and the Xubuntu external hard drive.

---

### Post by jimmy the saint on 2008-12-29
Yes you will, but be prepared to either have and understand the Super Grub Disk or be able to restore the Vista boot loader.  A few weeks ago a guy did exactly what you are wanting to do and the grub boot loader replaced the vista boot loader, but was placed on the external HDD.  The result is that the computer will only boot when the external HDD is present.  I think if you make a small partition on the internal drive and mount it as /boot (which grub will install to automatically), this issue could be resolved, but I will let someone much smarter than me tell you for sure.

If it were me, I would just do a simple dual boot.  The whole process is simpler.  In fact, Unless you play games or do intense 3D work in vista, I would go even farther and just put Vista in a virtual machine. This could cause issues if you have the latest ipod touch or iphone though.

Edit:  Oh yeah, you should have no troubles with using files you created in xubuntu with vista.  You just need to make sure the files are in a format that vista has a program to work with.  Mpeg should work fine, OGG may need appropriate software.

---

