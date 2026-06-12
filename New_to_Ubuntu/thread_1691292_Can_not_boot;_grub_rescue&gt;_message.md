---
title: "Can not boot; grub rescue&gt; message"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by tgsauer19 on 2011-02-19
I am a relatively new user. I tried to set up my new I7 processer computer to be able to dual boot with Windows 7. I thought I was being careful by installing UBUNTU on a separate external USB hard drive so as to not corrupt my internal hard drive with the Window 7 operating syatem. Followed the procedure outlined on instllation CD.
When I tried to restart after installation I got the following message:
"error: file not found
grub rescue> "

I can still boot from CD but not from anywhere else. What should I do.

---

### Post by J697 on 2011-02-19
I am not an expert, but I think I need more info than that. Like, you used a usb to install ubuntu? What exactly happens after you installed it? What exactly happens when you boot up? You wanted to dual-boot windows 7 and linux, huh... My guess is it will boot into widows 7, but when you select to start Ubuntu it gives the error? If so then, either try the liveCD, or the alternate install (still on CD).

---

### Post by n-n-nebbl on 2011-02-19
Do you know where you installed your grub?
And what's your boot-order? Hard-Drive with windows, or external USB-Drive first?

---

### Post by tgsauer19 on 2011-02-19
Let me clarify. I installed from a CD. I selected an external USB drive as the place to install UBUNTU. I believe that I put Grub on my A drive, the internal hard drive

---

### Post by n-n-nebbl on 2011-02-19
maybe your grub has a problem to find your external USB-Drive

GRUB has 2 stages

Stage 1 is installed on the MBR of your internal Hard-Drive

Stage 2 is on /boot of your Ubuntu Installation (default: your external USB-Drive)

If grub cannot find your external USB-Drive it cannot mount and read /boot (where the grub.cfg file is located)


If you know how, i would make a boot partition on your internal hard-drive and install Ubuntu again, so you can boot without the external USB-Drive into grub
From there you can boot Windows usually without problems, and see further with your Ubuntu problem if it still exists.

---

