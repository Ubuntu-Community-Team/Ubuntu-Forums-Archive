---
title: "Boot problem: Undefined Video Mode 307"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-19
Once I get into grub and choose the kernel to boot from, it no longer takes me directly to the login prompt. Instead I get dropped at a black screen with a message: Undefined video mod1e:307 or something like that.

I have the option to either select from a list of about 2 dozen video modes, press space to continue (nothing happens) or wait 30 seconds and it automatically resumes the boot process and takes me to the login window normally.

Relatively new (1 week old install). Nothing has been removed, only lots of apps added. However no changes between when it was normal and this problem started.

Any ideas?

Thanks a lot

---

### Post by Andy06 on 2009-05-21
*bump*

---

### Post by rob2uk on 2009-05-21
Did you install Plymouth right before it started?

---

### Post by Andy06 on 2009-05-21
Nope, did not have a clue what that was. Googled it and found it was the boot loader for fedora. But yeah, nothing to do with plymouth.

In fact the strange thing is there were no changes whatsoever between working fine and giving this error. It "just happened", which is quite frequent for small issues, but this is a major one.

I've been installing and uninstalling lots of devices in windows and also playing around with drivers there, but I cannot imagine how that would affect Linux. They are on different partitions anyway.

---

### Post by Bucky Ball on 2009-05-21
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/216636](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/216636)

Ain't much but it's a start.

---

### Post by rob2uk on 2009-05-21
> **Andy06 said:**
> Nope, did not have a clue what that was. Googled it and found it was the boot loader for fedora. But yeah, nothing to do with plymouth.

In fact the strange thing is there were no changes whatsoever between working fine and giving this error. It "just happened", which is quite frequent for small issues, but this is a major one.

I've been installing and uninstalling lots of devices in windows and also playing around with drivers there, but I cannot imagine how that would affect Linux. They are on different partitions anyway.

Can you post the contents of /boot/grub/menu.lst please?

Not the whole file, just the section that starts ## ## End Default Options ## and ends ### END DEBIAN AUTOMAGIC KERNELS LIST

(should be the last part of the file)

---

### Post by Andy06 on 2009-05-21
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3a760e98-5c96-4ced-a87f-43ddf4ab6846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3a760e98-5c96-4ced-a87f-43ddf4ab6846 ro quiet splash vga=791 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		3a760e98-5c96-4ced-a87f-43ddf4ab6846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3a760e98-5c96-4ced-a87f-43ddf4ab6846 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		3a760e98-5c96-4ced-a87f-43ddf4ab6846
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Andy06 on 2009-05-21
I might add that I just managed to solve the issue by using start up manager and selecting 1024x768 as the resolution (despite my laptop widescreen resolution being 1280x800.

Funnily enough, the resolution itself did not change. Also even more curiously, it messed up the colours of the shut down splash (the start up ubuntu splash in reverse). The start up splash is still the way it was but the shut down splash now looks like its in the wrong "x-bit" colours mode.

---

### Post by rob2uk on 2009-05-21
back up the file, remove vga=791, save, then reboot.

Make sure you have a LiveCD handy just in case something goes wrong, but I'm certain that's where the problem lies

---

### Post by Andy06 on 2009-05-21
I managed to hack fix it using start up manager, would you recommend I still remove VGA791 thingy? 

Setting the resolution back to 1280x1024 in SUM brings the problem back if that helps.

Anyway if you recommend removing that VGA bit, I'll do that, lemme know.

Thank you very much for your time.

---

### Post by Gen2ly on 2009-05-21
Here's a link to setting the right vga setting:

[http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution](http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution)

I thought that Ubuntu still uses this!?

---

### Post by rob2uk on 2009-05-22
> **Andy06 said:**
> I managed to hack fix it using start up manager, would you recommend I still remove VGA791 thingy? 

Setting the resolution back to 1280x1024 in SUM brings the problem back if that helps.

Anyway if you recommend removing that VGA bit, I'll do that, lemme know.

Thank you very much for your time.

If you got it fixed already, then no :)

---

### Post by scorp123 on 2009-05-22
> **Andy06 said:**
> ## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		3a760e98-5c96-4ced-a87f-43ddf4ab6846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=3a760e98-5c96-4ced-a87f-43ddf4ab6846 ro quiet splash **[COLOR="Red"]vga=791 [/COLOR]**
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
 You tried to enable a framebuffer video mode for the text console?

I assume then that you did not know that since a few releases Ubuntu ships with the _framebuffer drivers **disabled.**_ So those "*vga=*" lines _**will not work**_ and cause a completely black screen.

To make it work again you'll have to follow these steps.

Please go to this thread ... to save you time I will link directly to the relevant posts:

First, do as Octagonal says in posting #51 - His posting will help you get the framebuffer back to work:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

Then follow the link Namanbagga gives in posting #53 - His posting will fix the splash screen during boot and shutdown (just do the 3 steps there he mentions on his blog):
[http://ubuntuforums.org/showpost.php?p=3715308&postcount=53](http://ubuntuforums.org/showpost.php?p=3715308&postcount=53)

And if you're fairly positive that your framebuffer could do more than just "vga=791" you could try these experiments and change that number "791" to a higher resolution based on your findings:
[http://ubuntuforums.org/showpost.php?p=5034658&postcount=62](http://ubuntuforums.org/showpost.php?p=5034658&postcount=62)
[http://ubuntuforums.org/showpost.php?p=6281148&postcount=73](http://ubuntuforums.org/showpost.php?p=6281148&postcount=73)

Just be aware that not all resolutions may be supported, despite what your screen might be capable of otherwise:
[http://ubuntuforums.org/showpost.php?p=6345515&postcount=77](http://ubuntuforums.org/showpost.php?p=6345515&postcount=77)

And in case anyone cares to know what this "vga=" stuff is all about - voila:
[http://ubuntuforums.org/showpost.php?p=7182310&postcount=89](http://ubuntuforums.org/showpost.php?p=7182310&postcount=89)

---

### Post by AldenIsZen on 2009-05-22
I think I will look at all that later Scorp, thanks for the information. I loved to understand and learn. 

Anyhow, this problem has been plaguing me for close to a year, but due to circumstances I haven't bothered looking into it but  few times and I didn't have time to start a thread and follow up as Ubuntu still ran. I decided to try to get Counter Strike Source running today though. :) Start-up-Manager was the culprit as I had tried to get a higher resolution for my wide-screen monitor. I figured why not make startup look better eh? ):P

---

### Post by Andy06 on 2009-05-22
>  	
Re: Boot problem: Undefined Video Mode 307
Quote:
Originally Posted by Andy06 View Post
## ## End Default Options ##

title Ubuntu 9.04, kernel 2.6.28-11-generic
uuid 3a760e98-5c96-4ced-a87f-43ddf4ab6846
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=3a760e98-5c96-4ced-a87f-43ddf4ab6846 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.28-11-generic
quiet
You tried to enable a framebuffer video mode for the text console?

I assume then that you did not know that since a few releases Ubuntu ships with the framebuffer drivers disabled. So those "vga=" lines will not work and cause a completely black screen.

To make it work again you'll have to follow these steps.

Please go to this thread ... to save you time I will link directly to the relevant posts:

First, do as Octagonal says in posting #51 - His posting will help you get the framebuffer back to work:
[http://ubuntuforums.org/showpost.php...9&postcount=51](http://ubuntuforums.org/showpost.php...9&postcount=51)

Then follow the link Namanbagga gives in posting #53 - His posting will fix the splash screen during boot and shutdown (just do the 3 steps there he mentions on his blog):
[http://ubuntuforums.org/showpost.php...8&postcount=53](http://ubuntuforums.org/showpost.php...8&postcount=53)

And if you're fairly positive that your framebuffer could do more than just "vga=791" you could try these experiments and change that number "791" to a higher resolution based on your findings:
[http://ubuntuforums.org/showpost.php...8&postcount=62](http://ubuntuforums.org/showpost.php...8&postcount=62)
[http://ubuntuforums.org/showpost.php...8&postcount=73](http://ubuntuforums.org/showpost.php...8&postcount=73)

Just be aware that not all resolutions may be supported, despite what your screen might be capable of otherwise:
[http://ubuntuforums.org/showpost.php...5&postcount=77](http://ubuntuforums.org/showpost.php...5&postcount=77)

And in case anyone cares to know what this "vga=" stuff is all about - voila:
[http://ubuntuforums.org/showpost.php...0&postcount=89](http://ubuntuforums.org/showpost.php...0&postcount=89)

:shock::shock:

I dint do any of that mainly because I have no idea what all that is :mrgreen:

You give me far too much credit by overestimating my competence level.

---

### Post by scorp123 on 2009-05-22
> **AldenIsZen said:**
>  Start-up-Manager was the culprit as I had tried to get a higher resolution for my wide-screen monitor. As written above: You have to re-enable the framebuffer drivers. Then it will work as you intended (for the text consoles).

---

### Post by scorp123 on 2009-05-22
> **Andy06 said:**
>  I dint do any of that mainly because I have no idea what all that is  Read and learn. ;)  Especially that last link I gave explains a lot.

> **Andy06 said:**
>  You give me far too much credit by overestimating my competence level. Well, "vga=791" on that kernel line tells me enough. You tried to enable a framebuffer resolution. As I said above: Unless you follow the few simple steps to get the driver back (it's there but disabled) that line in your config won't work. You will get a black screen.

---

### Post by Andy06 on 2009-05-22
> 
[QUOTE]Originally Posted by Andy06 View Post
I dint do any of that mainly because I have no idea what all that is
Read and learn. Especially that last link I gave explains a lot.[/QUOTE]

No no I meant I din't do any of those things to cause that problem. As in I did not try to enable any frambuffer resolution simply because I have no idea what that is or does :D. I wasn't saying that I can't do what you recommended because I wasn't comofortable.

Maybe some app (Start Up manager) does that (framebuffer thingy) when you try to change resolution.



> [QUOTE]Originally Posted by AldenIsZen View Post
Start-up-Manager was the culprit as I had tried to get a higher resolution for my wide-screen monitor.
As written above: You have to re-enable the framebuffer drivers. Then it will work as you intended (for the text consoles). [/QUOTE]

Although I sort of fixed it by simply playing around with SUM resolution settings. Then re created the issue and fixed it again to make sure. Thing is I don't think SUM CAUSED the issue because I hadn't played with it initially.

Hope that helps.

---

### Post by scorp123 on 2009-05-22
> **Andy06 said:**
>  Maybe some app (Start Up manager) does that (framebuffer thingy) when you try to change resolution. I think that this could be the culprit.

---

### Post by Bucky Ball on 2009-05-22
> **Andy06 said:**
>  Thing is I don't think SUM CAUSED the issue because I hadn't played with it initially.

Sometimes these mysteries happen, but once set up, hopefully rarely! An update cause the problem, perhaps? Just started happening?

---

### Post by Andy06 on 2009-05-22
Not even update. Coz I hadn't updated right before. Basically between it not happening and happening, there were no changes hehe.

Just one of *those* things.......

---

