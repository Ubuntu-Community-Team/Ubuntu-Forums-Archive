---
title: "Recompile kernel to 1000hz"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by 4JOKE4 on 2009-02-03
I need to recompile Xubuntu Kernel to 1000hz. But I afraid that it could crash.

Could someone write here easy step-by-step manual?!
I only found this recompile script, by I don't know if I can use it for Xubuntu exactly as it is there:
[http://ubuntuforums.org/showthread.php?t=302069&highlight=1000hz](http://ubuntuforums.org/showthread.php?t=302069&highlight=1000hz)

---

### Post by igknighted on 2009-02-03
[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

Use this app, or search the forums for the "Master Kernel Thread".

Compiling your own kernel is completely safe.  Even if you mess up 100% and it doesn't work at all, you simply reboot into your old kernel which will still be in the grub menu and try again.  All you lose is the time you spent compiling.

---

### Post by 4JOKE4 on 2009-02-03
At first I looked at Master Kernel Thread and try to do it by myself but I got error.

So I installed KernelCheck. It's very good software and very easy to use. Thanks for advice :)

But I got the same error as before:
[[IMG]http://obrazok.eu/files/re0m3th19uhzxjab38a7_thumb.jpg[/IMG]](http://obrazok.eu/viewer.php?file=re0m3th19uhzxjab38a7.jpg)

What's wrong ?!

---

### Post by 4JOKE4 on 2009-02-03
hmm... I was finding at google/this forum ... and didn't found explanation of this error message :/

---

### Post by cardinals_fan on 2009-02-03
[http://ubuntuforums.org/showpost.php?p=6663154&postcount=335](http://ubuntuforums.org/showpost.php?p=6663154&postcount=335)

---

### Post by 4JOKE4 on 2009-02-04
I did this:
**cd /usr/src/linux-2.6.28/****/usr/src/linux-2.6.28$ gedit .config**

But in **.config** I can't find string CONFIG_XEN ?!
And I also tryed to find it in qconf which is visual editor of config which kernelcheck automatically opens.

---

### Post by kerry_s on 2009-02-04
on my old notes i used this.

in /etc/rc.local:
echo 1000 > /proc/sys/dev/rtc/max-user-freq &

use: locate max-user-freq

to find the right path.

i'm using arch, it looks like this:
echo 1024 > /sys/class/rtc/rtc0/max_user_freq &

i think due to kernel changes it should be "1024" instead of "1000" the default is "64".

---

### Post by 4JOKE4 on 2009-02-04
So I am now confused. I read that I have to recompile kernel to 1000hz and now kerry_s said that I need only 3 commands to set kernel to 1000hz, which seems to be 10times easier...

So is advice from kerry_s useful ?!

I think that it could be better, if someone said me where I can find CONFIG_XEN and then I will recompile kernel.

Thnx.

---

### Post by kerry_s on 2009-02-04
> **4JOKE4 said:**
> So I am now confused. I read that I have to recompile kernel to 1000hz and now kerry_s said that I need only 3 commands to set kernel to 1000hz, which seems to be 10times easier...

So is advice from kerry_s useful ?!

I think that it could be better, if someone said me where I can find CONFIG_XEN and then I will recompile kernel.

Thnx.

if your after a xen kernel it's in the repos. 
or is there some particular reason you need 1000hz?
i have it noted as a speed tweak in my notes.

for xen:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by 4JOKE4 on 2009-02-05
I need to make 1000fps game server, so I really need 1000hz kernel.

I looked at your link about XEN. I saw that page many times before, but I can't find there anything useful. It's about installing XEN, but I have to disable it somewhere in file(maybe config file), when I am compiling kernel... isn't it ?!

---

### Post by kerry_s on 2009-02-05
in that case, yeah, you'll have to go with a custom kernel and try to cut out what you don't need as well. you should be using a custom install to, you want to limit those background tasks.

look here, i had some notes, might help you:
[http://ubuntuforums.org/showthread.php?t=973191&highlight=custom+kernel](http://ubuntuforums.org/showthread.php?t=973191&highlight=custom+kernel)

---

### Post by 4JOKE4 on 2009-02-05
hmm and what is diference between your notes to compile kernel and between what kernelcheck does ?

---

### Post by kerry_s on 2009-02-05
> **4JOKE4 said:**
> hmm and what is diference between your notes to compile kernel and between what kernelcheck does ?

don't know, never tried kernelcheck, just always done it the debian way.

---

### Post by 4JOKE4 on 2009-02-06
I used your notes, but still I get error :(

41800000-41821000 rw-p 41800000 00:00 0 
41821000-41900000 ---p 41821000 00:00 0 
bfca2000-bfcb5000 rwxp bffea000 00:00 0          [stack]
bfcb5000-bfcb8000 rw-p bfffd000 00:00 0 
fs/ext4/namei.c: In function \u2018ext4_rename\u2019:
fs/ext4/namei.c:2289: internal compiler error: Zru\u0161ené
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.3/README.Bugs> for instructions.
make[3]: *** [fs/ext4/namei.o] Error 1
make[2]: *** [fs/ext4] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.4'
make: *** [debian/stamp-build-kernel] Error 2

---

### Post by 4JOKE4 on 2009-02-06
Damn, I have totally badluck! Is there any easy way to compile kernel? I think that NO...

When I got ext4 error, I disabled ext4 and compile again...
But then I got new error (about oracle I think), so I disabled oracle feature...

Now I tryed to compile again and got this error message:

Building modules, stage 2.
MODPOST 2023 modules
ERROR: "pcd_pci_tbl" [drivers/pci/hotplug/shpchp.ko] undefined!
WARNING: modpost: Found 9 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Chyba 1
make[1]: *** [modules] Chyba 2
make[1]: Leaving directory `/usr/src/linux-2.6.27.4'
make: *** [debian/stamp-build-kernel] Chyba 2


How many times I have to recompile kernel to disable everything what is problematic?!?!
Is there any easier way ?!

---

### Post by kerry_s on 2009-02-06
ouch, it happens.

make sure you have the things needed, like the stuff to build, the development stuff(ext4dev?), any patches needed?. 

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

don't sweat it, it takes practice, practice, practice
just try, try again and again and again..... ;)

i gave up compiling ages ago, just hate it.

---

