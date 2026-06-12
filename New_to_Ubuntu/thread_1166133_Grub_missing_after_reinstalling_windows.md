---
title: "Grub missing after reinstalling windows"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by bhanthenzzz07 on 2009-05-21
Hi, firstly I am not too good in linux, so I am forced to write my problem here because I can't complete it myself. ](*,)

Yesterday, I have problem with my windows (I'm using dual boot ubuntu 9.04 - Windows in my computer). So I decided to format my windows partion. But when I restart my computer, the grub is missing, so I can't boot my lovely ubuntu. 

When I boot with live CD, It still can open my ubuntu partition, but because there's no grub, I am unabe to boot it

I follow this step in this link
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But, in the final step, I got error code like this :sad:

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```

I'm glad if anyone want to help me [-o<. Anyway, I don't want to reinstalling ubuntu because there's file that I still download and they're incomplete.

---

### Post by Hospadar on 2009-05-21
No problem, you'll just need to re-install grub.  Windows knows nothing of grub or linux, so it will just wipe out your MBR (master boot record) if you install it after installing linux.  It's an easy fix, and it'll require a livecd and a little bit of terminal hax.  This guide should be of use: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bhanthenzzz07 on 2009-05-21
> **Hospadar said:**
> No problem, you'll just need to re-install grub.  Windows knows nothing of grub or linux, so it will just wipe out your MBR (master boot record) if you install it after installing linux.  It's an easy fix, and it'll require a livecd and a little bit of terminal hax.  This guide should be of use: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I already follow the step but I get error code like in my post above.

---

### Post by bhishan on 2009-05-21
> **bhanthenzzz07 said:**
> I already follow the step but I get error code like in my post above.

this tutorial worked for me last time I used it. 
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by bhanthenzzz07 on 2009-05-22
> **bhishan said:**
> this tutorial worked for me last time I used it. 
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

I already follow the turtorial but I got error like this
```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition
```

maybe I was wrong, then I tried to find grub directory with this command

```
grub> find /boot/grub/stage1

```
then it says (hd0,5). So I try to re-follow the turtorial like in this url
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) and it's keeping get error like this

```
grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```

I don't know what is wrong about this. Maybe I have to reinstall the ubuntu ?

---

