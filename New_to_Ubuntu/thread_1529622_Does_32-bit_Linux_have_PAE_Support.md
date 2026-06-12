---
title: "Does 32-bit Linux have PAE Support?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by GeekDiscourse on 2010-07-12
I have 6GB ram on my computer but as a Linux newbie, I am reluctant to install 64-bit Ubuntu. I have read there are incompatibilities or complicated workarounds related to running 64-bit. Does the 32-Bit kernel support PAE or should I simply go with 64-bit?

---

### Post by Crunchy the Headcrab on 2010-07-12
I've never had any problems related to using 64bit Ubuntu.  Some people have experienced problems with flash, but I haven't had any issues.  I actually recommend 64bit linux to people that have 64bit capable processors.

---

### Post by fooman on 2010-07-12
go with 64bit.

i have no issues with it,  although there may have been some in older versions.  those issues were mostly multimedia related, and are for the most part, fixed.

---

### Post by GeekDiscourse on 2010-07-12
What the official nVidia drivers? Any problems in 64-bit? If not then 64-bit sounds good.

---

### Post by philinux on 2010-07-12
> **GeekDiscourse said:**
> I have 6GB ram on my computer but as a Linux newbie, I am reluctant to install 64-bit Ubuntu. I have read there are incompatibilities or complicated workarounds related to running 64-bit. Does the 32-Bit kernel support PAE or should I simply go with 64-bit?

IIRC if the installer detects more than 4 gig memory it will install the pae kernel.

However. See this. [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

---

### Post by blur xc on 2010-07-12
> **GeekDiscourse said:**
> What the official nVidia drivers? Any problems in 64-bit? If not then 64-bit sounds good.
I use nvidia 64bit drivers in 10.04 and everything works great.  Flash doesn't seem to be quite up to snuff yet though, but i'm runnign the 64bit flash that's no longer available.  I have no idea how the latest 32bit plugin with the ndiswrapper works though...

BM

---

### Post by TrombaMarina on 2010-07-12
I'm also interested in how to enable PAE in the 32-bit kernel to make use of my 8GB memory.  I found something yesterday, but I've been searching for 20 minutes today and haven't found it yet.

Several people have suggested jumping to 64-bit.  I found that the Intel i915 graphics driver doesn't work for me in 64-bit.  For a complete description of the problem and workaround see:

[http://ubuntuforums.org/showthread.php?p=9583925#post9583925](http://ubuntuforums.org/showthread.php?p=9583925#post9583925)

Definitely try 64-bit for a few hours interactively before relying on it.  I had Java and Flash working fine after a not-too-difficult install.  The 64-bit IRC channel on Freenode only had about 5 potentially live humans on it, no discussion except for my unanswered question for over an hour this morning.

I believe in transcendence through suffering and "that which doesn't kill you makes you stronger."  But I also have to get work done.  If I can get 8GB of memory in 32-bit ubuntu, I would be very happy.  Hopefully PAE can supply that.

---

### Post by mrbond113 on 2010-07-12
In theory, the PAE kernel (kernelname-pae) should do the trick.  However, I've tried that method myself with no luck (in both 9.04 and 9.10). 

Something like "linux-image-2.6.32-pae" or somewhere thereabouts.

---

### Post by migs73 on 2010-07-12
Trombamarina

Try this, it worked fine for me with 4GB (now got 3.8 GiB on system monitor not 2.8 with standard 32 bit Kernel)

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by TrombaMarina on 2010-07-13
Thanks, everyone, for your PAE suggestions (migs73) and 64-bit suggestions.  I was able to get 64-bit working - my problem was a bug in the Intel i915 64-bit graphics driver, or possibly in DRI.  For a complete description of my problem and workaround see:

[http://ubuntuforums.org/showthread.php?p=9583925](http://ubuntuforums.org/showthread.php?p=9583925)

I'm happily using 64-bit now with 8GB ram, so I don't need PAE after all.

---

