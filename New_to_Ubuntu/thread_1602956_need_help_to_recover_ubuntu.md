---
title: "need help to recover ubuntu"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by rainyhere on 2010-10-22
my ubuntu has corrupted during updation and now i am unable to use it any tips on how to recover...

---

### Post by ibizatunes on 2010-10-22
what it not doing your ubuntu?
download a new copy and do a clean install

---

### Post by Rubi1200 on 2010-10-22
The information you have provided is insufficient for us to know what is going on and how to help you.

Please tell us, at least, the following:

1. what version of Ubuntu do you have and how was it installed e.g. using Wubi?

2. how much RAM do you have and what graphics card is installed?

3. do you also have other operating systems such as Windows installed and what version?

4. do you get any error messages when trying to boot; please describe the situation in more detail

Thanks.

---

### Post by sikander3786 on 2010-10-22
> **rainyhere said:**
> my ubuntu has corrupted during updation and now i am unable to use it any tips on how to recover...
We need some more information.

Did the upgrade process complete successfully?

What do you get now when you try to boot Ubuntu? Blank screen? Grub rescue? Any error messages will be helpful.

---

### Post by rainyhere on 2010-10-22
no upgrade wasnt complted successfully...system was halted during installation and after that when i booted it through ubuntu i just got a blank screen...

i am using ubunt 10.4 and installed it in dual boot mode...

---

### Post by sikander3786 on 2010-10-22
Press down and hold the Shift key on your computer's bios screen. You'll see a Grub menu. Choose the second entry i.e, recovery mode > Drop to root shell or something like that. Now try to reconfigure all the packages.

```
sudo dpkg --configure -a
```

Do you see any error messages? Please post if any.


Edit: I just noticed it is a dual boot setup, in that case you don't need to hold down the shift key. You will see the Grub menu automatically.

---

### Post by Rubi1200 on 2010-10-22
Thanks for the information.

From a LiveCD, post the results of the boot-script linked at the bottom of my post.

Wrap the text with the # tag from the menu when you copy it back here.

---

### Post by sikander3786 on 2010-10-22
> **Rubi1200 said:**
> Thanks for the information.

From a LiveCD, post the results of the boot-script linked at the bottom of my post.

Wrap the text with the # tag from the menu when you copy it back here.
I think the OP was trying to install regular updates. Not a dist-upgrade. Will the bootinfoscript be helpful in that case?

To the OP: Please confirm if it was a regular update process interrupted or it was a distribution upgrade in process?

---

### Post by Rubi1200 on 2010-10-22
@sikander3786; if the process was halted and something got messed up with GRUB or the file system mounting, then yes, the boot script might be helpful to identify the problem.

---

### Post by sikander3786 on 2010-10-22
> **Rubi1200 said:**
> @sikander3786; if the process was halted and something got messed up with GRUB or the file system mounting, then yes, the boot script might be helpful to identify the problem.
Got it. I agree :-)

---

### Post by rainyhere on 2010-10-22
@sikandar

recovery console is not taking any command

---

### Post by sikander3786 on 2010-10-22
> **rainyhere said:**
> @sikandar

recovery console is not taking any command
What does it say? Any errors?

Please post the bootinfoscript as Rubi mentioned as it might also be helpful in the current situation.

---

### Post by rainyhere on 2010-10-28
i was using linux and windows in dual boot environment...after getting erros in ubuntu i used windows xp and today even that isnt working. following are the results of boot script info...
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 



---

