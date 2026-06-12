---
title: "Applications: minimum RAM?"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by amanchesterman on 2009-09-03
I have an old laptop (an Acer Aspire 1300) which used to run Windows XP. I have recently installed Xubuntu 9.04 (Jaunty) instead and I am very pleased with the result: it's now a fast and usable machine.

I chose Xubuntu because it's designed for machines with limited RAM: the Aspire 1300 has only 256k. Xubuntu comes with a range of applications as part of the distro, but I'd like to install some more. My question is, how do I find out the minimum RAM requirements for each application? The install/remove option lists a range of applications that are available for download, are they all suitable for machines with a limited memory? Or do I have to check each application separately? And if so, how do I do that?

As an example: I use Open Office on another (Windows) laptop and I think it's great. But the Open Office website says that the program needs a minimum of 356k RAM -- so there is no point in me trying to install it on the Linux machine. Presumably other applications have minimum RAM requirements too?

---

### Post by LowSky on 2009-09-03
Um.. its not 356k, its 356MB, MB as in megabytes... best answer is you should have about 512MB to run your computer efficiently. the more the better.

Oddly Linux doesn't really ever posts specifications for programs. But if you need a lighter weight word processor try Abiword, but OpenOffice should work albeit really slow

as seen here
[http://www.openoffice.org/dev_docs/source/sys_reqs_30.html](http://www.openoffice.org/dev_docs/source/sys_reqs_30.html)


Microsoft Windows

    * Windows 2000 (Service Pack 2 or higher), Windows XP, Windows 2003, Windows Vista
    * 256 Mbytes RAM (512 MB RAM recommended)
    * At least 650 Mbytes available disk space for a default install (including a JRE) via download. After installation and deletion of temporary installation files, OpenOffice.org will use approximately 440 Mbytes disk space.
    * 1024 x 768 or higher resolution with at least 256 colours


GNU/Linux ("Linux")

    * Linux kernel version 2.4 or higher, glibc2 version 2.3.2 or higher
    * 256 Mbytes RAM (512 MB recommended)
    * 400 Mbytes available disk space
    * X-Server with 1024 x 768 or higher resolution with at least 256 colours

---

### Post by aeiah on 2009-09-03
because linux distros are so variable i dont think any developer could reasonably state what ram their software requires. software may need 60mb ram, which is fine if your linux install only requires 120mb but not if it requires 220mb in your case.

i guess you should just test things out. to be honest, unless you're doing music / video production you'll probably not use software that uses as much as open office or firefox. there are lightweight alternatives to open office like abiword etc. perhaps as a pointer you should see what software distros like damn small linux, puppy linux and crunchbang use as defaults as these are likely to be pretty lightweight

---

### Post by rsiddharth on 2009-09-03
googling perhaps is a good good idea . For instance , If you want to find the minimum requirements to run Open Office you can do a search like - open office minimum requirements . In most cases the first link should the one your looking for .

---

### Post by Sir Jasper on 2009-09-03
Hi amanchesterman,

I suggest you try Open Office (256MB (not 356 MB RAM?) with nothing else active and see how slow or fast it is. It is easily uninstalled if too slow for you.

My regards

---

### Post by yanceypd on 2009-09-03
Im not sure but you might be able to format a jump drive as swap to increase ram.  Someone else here might know for sure

---

### Post by earthpigg on 2009-09-03
hi amanchesterman,

a base RAM requirement, the way it is frequently done in Windows or OS X, would not work with Linunx -- or even with Ubuntu.

lets work how you would establish the minimum RAM requirements for, say, Firefox.

r = requirement
o = ram used by OS
p = ram used by program in question

o + p = r

Some Ubuntu machines run xfce (the branding is "xubuntu", but you are running Ubuntu with xfce). lets say for this, 0 = 200
Some Ubuntu machines run gnome (Ubuntu default). lets say for this, o = 400
Some machines run others - the machine i am on now runs Ubuntu, but with LXDE. 0 = 60.


since the possible variations of "o" are endless - *even within Ubuntu* - the closest that could be done would be to ask "how much RAM does this program use when ran?"

that question may also need to include which DE you are using -- a GNOME app run in KDE will require more RAM than when run in GNOME.... since the GNOME app in KDE will need to load a bunch of GNOME stuff.

that would allow you to figure out if you could run the program without relying on your swap, or if you would need to rely on your swap.

either way, *you could still run the program as long as you have a generous swap.*

---

### Post by LewRockwell on 2009-09-03
slap a couple of 512MB sticks in there and run like the wind!

[http://www.upgradecomputermemory.com/ram.cfm/memory/A/Acer/AcerAspire-Notebook-Series/Aspire-1300-Notebook-Series/](http://www.upgradecomputermemory.com/ram.cfm/memory/A/Acer/AcerAspire-Notebook-Series/Aspire-1300-Notebook-Series/)

.

---

### Post by snowpine on 2009-09-03
Well what can I say that Earthpigg hasn't already... that was a very informative post. :)

Do you have a swap partition? (It is created automatically if you used the default install options.) If so, it is "virtual memory." If you have 256mb ram plus 512mb swap, you can run applications that require 768mb of ram. They will be slow, though...

I have OpenOffice installed on a 128mb computer using the Slitaz distro. It runs, but it's slow. Abiword is faster.

---

### Post by Paqman on 2009-09-03
> **yanceypd said:**
> Im not sure but you might be able to format a jump drive as swap to increase ram.  Someone else here might know for sure

The swap partition on your hard drive does this already. I wouldn't use anything connected over USB for swap space, it'd be painfully slow.

---

### Post by amanchesterman on 2009-09-04
Many thanks to you all for your advice and your informative responses. You have kinda confirmed what I suspected, so that's reassuring.

Xubuntu works well on this (low spec) machine, it includes the Xfce desktop and Abiword.

Thanks again. :D

---

