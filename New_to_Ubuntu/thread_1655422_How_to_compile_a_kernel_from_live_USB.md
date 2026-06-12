---
title: "How to compile a kernel from live USB"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by wishingstar on 2010-12-29
Hi all,

I am currently using lucid after I tried Maverick and was faced with a black screen on boot (the computer just froze), and I was told it was a kernel problem. 

Was this issue has been resolved in later maverick kernels? If so, is it possible to customize a USB install disc with the newer kernel instead of the default one? Or install the newer kernel at the time of installing ubuntu so I wouldn't have to revert to the lucid kernel? (which is quite problematic when running applications made for maverick, as one would imagine)

Thanks in advance

---

### Post by stmiller on 2010-12-29
I'm not sure that compiling a new kernel would 'fix' what you are describing. That is a scary road likely to lead to hours of more frustration.

When you say you tried 10.10, do you mean you could not load the live CD? That may be another issue all together.

You can just upgrade to 10.10 from within Ubuntu:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Regards,

---

### Post by wishingstar on 2010-12-29
> **stmiller said:**
> I'm not sure that compiling a new kernel would 'fix' what you are describing. That is a scary road likely to lead to hours of more frustration.

When you say you tried 10.10, do you mean you could not load the live CD? That may be another issue all together.

You can just upgrade to 10.10 from within Ubuntu:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Regards,

Thanks for responding :)

Yes, I tried to boot from the live CD and a USB, both showed a blank screen and I couldn't even log in using text mode. I asked on the forums, and they said it was a kernel issue with the video drivers in Maverick.

I tried to upgrade from within ubuntu, the upgrade went smoothly but when I restarted the system (booting into the new Maverick kernel) I was faced with the same issue and had to return to the old Lucid kernel (which created lots of problems especially with applications that required MPRIS support, and even wallpaper switching was problematic!)

I want to use Maverick, but it seems the kernel drivers are against me!

---

