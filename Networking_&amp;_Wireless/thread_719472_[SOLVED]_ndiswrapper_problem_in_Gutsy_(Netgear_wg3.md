---
title: "[SOLVED] ndiswrapper problem in Gutsy (Netgear wg311v3)"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by Dirigo on 2008-03-09
I'm trying to get my wireless adapter woking in Gutsy (worked fine in Feisty).  I've followed the tutorial in the WifiDocs about this adapter, and all goes very well and according to the outputs in the tutorial until I hit

"sudo modprobe ndiswrapper"

The output from that reads:  

"FATAL: Module ndiswrapper not found"

when I type in 

"iwconfig"

 I get:

"lo     no wireless extensions"

when I type in 

ndiswrapper -m

The return is:

"module configuration already contains alias directive"

I'm new to this, so I'm sure I've missed something, but I don't know my way out.  Any assistance would be welcome.  Thanks!

---

### Post by spd106 on 2008-03-09
Unless you have compiled ndiswrapper manually, the kernel module is supplied with the Ubuntu kernel. The separate ndiswrapper packages only have the userspace tools.

Try looking for the ndiswrapper.ko file, it should be in the /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ directory. If not you may have to download a copy or perhaps re-install the kernel image.

Also try running ```
modinfo ndiswrapper
``` and ```
ndiswrapper -v
``` for extra information.

---

### Post by Dirigo on 2008-03-09
Thanks for the prompt response!

ndiswrapper .ko 

is indeed in the directory you suggested.

modinfo ndiswrapper  returns:

"could not find module ndiswrapper"

ndiswrapper -v  returns:

"utils version: 1.9
driver modinfo: could not find module ndiswrapper"

Where should I go from here?  

Thanks for your patience...

---

### Post by Dirigo on 2008-03-11
Is there anyone who can help me futher with this?  I've been digging through all the posts/tutorials and nothing I've found has applied to this problem.

How do I proceed with the advice that was given?

Thanks.

---

### Post by spd106 on 2008-03-15
Sorry for the delay in replying.

I was mistaken before when I gave you the path to the module, because I gave you the one I have and I'm still running Ubuntu 7.04. For 7.10 the path will be slightly different due to a different kernel version. If you upgraded from 7.04 to 7.10 then the old kernel might still be around meaning that you would find the module in the path I stated previously.


The best thing to do next would be to try to find all ndiswrapper files.
i.e.```

sudo updatedb
locate ndiswrapper
```

You should then be able to find if you have the ndiswrapper.ko for your current kernel.

N.B. To find the kernel version quickly run this
```
uname -r
```

---

### Post by Dirigo on 2008-03-16
Thank you for the reply! I had some time this weekend, and just ended up doing a clean install, because I had updated from 7.04. My wireless is working just fine in 7.10 now by following this excellent thread:
 
[http://ubuntuforums.org/showthread.php?t=574501&highlight=kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=kevdog)
 
It worked like a charm!

---

