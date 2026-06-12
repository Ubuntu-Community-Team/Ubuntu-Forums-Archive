---
title: "Lost my ubuntu partition"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by keymoo on 2009-06-23
Hi there,

I had a dual boot Windows Vista and Ubuntu Jaunty configuration on my PC. I have recently downloaded the Windows 7 RC (boo hiss!) and did a clean install over Vista preserving my Linux partitions.

How do I get the bootloader to show me windows and linux? It now boots directly to Windows 7 without letting me get to my linux partition.

Thanks!
keymoo

---

### Post by LewRockwell on 2009-06-23
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by keymoo on 2009-06-23
Thanks I tried that but it didn't work for me. I selected Auto super grub disk and then nothing happened. Any other suggestions?

---

### Post by LewRockwell on 2009-06-23
> **keymoo said:**
> Thanks I tried that but it didn't work for me. I selected Auto super grub disk and then nothing happened. Any other suggestions?

that disk has quite a few different functional capabilities and you won't hurt anything by checking into it further

I'm reasonably sure it can cure your problem

---

### Post by billgoldberg on 2009-06-23
It's a common problem.

Windows doesn't care what operating systems are on your pc. It presumes you will only need Windows.

A solution can be found here if supergrubdisk doesn't work:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by Mark Phelps on 2009-06-24
Don't know why you say "boo hiss" about Windows 7, I've been really impressed with it -- when compared to Vista.

If you really did install the RC, you're nearly 150 builds behind the times!  That was build 7100; the current is 7260.  Lots of changes have been made since 7100.  If you are really interested in seeing what Seven has to offer, google around for locations to download the latest build.

Also, just to clear up your thread title ... you didn't lose your Ubuntu partition, you merely lost the ability to boot into it.  Do the GRUB repair that was posted and you'll get access back.

---

### Post by keymoo on 2009-06-24
Yeah Mark, I quite like it but I put that comment in for the benefit of this audience! I don't want to load an interim build as it doesn't go through the same level of testing and am using Windows 7 as my semi-main OS when I'm not using Ubuntu. :)

Thanks for the suggestions I'll try them later.

---

### Post by steigerjb on 2009-06-24
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

i think that is what you want

---

### Post by keymoo on 2009-06-24
steigerjb that's exactly what I wanted and fixed my issue (sending this from Ubuntu). Thanks!

---

