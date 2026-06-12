---
title: "Grub boot loader"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by djyoung4 on 2009-05-25
ok so I have a couple of questions about using the Grub boot loader.  Right now I am dual booting Ubuntu 9.04 and windows xp sp3.  I would like to try and set up a tri-boot with windows 7 and I know this really isn't the best place to ask about this but will I be able to use Grub to boot into windows 7. is this possible.  another things is when grub starts i have 2 different ubuntus.  one says ubuntu 9.04 kernel 2.6.28-12-some other number and the other says 11 in the place of 12.  other then those two numbers they are exactly the same.  Do i need both of these and if i dont is there a way to get rid of the one i dont need.  any help would be greatly appreciated

---

### Post by supersonicdarky on 2009-05-25
Question 2:
It gives you an option which kernel to boot. You usually want to keep 2, just in case 1 fails. You can remove the older ones with synaptic. (linux-image-*)

---

### Post by djyoung4 on 2009-05-25
they each have a safe mode as well and what does the 11 and 12 even mean.  is that just part of the version

---

### Post by raymondh on 2009-05-26
> **supersonicdarky said:**
> Question 2:
It gives you an option which kernel to boot. You usually want to keep 2, just in case 1 fails. You can remove the older ones with synaptic. (linux-image-*)

Hello,

as a follow to this ... you can install startupmanager (thru synaptic or terminal)...it'll give you the option to choose a default boot as well as hide the kernels (not erase them)

in terminal

sudo apt-get install startupmanager

Once installed, you'll find it in system > administration

Here's the official link

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Regards,

---

### Post by supersonicdarky on 2009-05-26
Here's my **uname -a**
```
Linux fission 2.6.29.2 #1 SMP PREEMPT Wed May 6 07:25:08 EDT 2009 x86_64 GNU/Linux
```
2.6.29.2 is the main version. If you are using stock kernels, then they also have a suffix such as -12. That just means build 12. Perhaps some custom patches were added, or files were moved, but it's still the same version.

In safe mode it tries to load as few drivers and devices as possible while getting you to a workable root shell. Useful when you mess something up and it doesn't boot.

---

### Post by djyoung4 on 2009-05-26
ok so if i am getting this correctly then the 11 one is the original install that i did and then when i changed it 12 became my own custom install.  thanks for the explanations by the way

---

