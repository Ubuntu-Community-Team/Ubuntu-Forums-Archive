---
title: "ipw2200 injection for ubuntu 8.10"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by ubuntu_jazzbach on 2008-11-29
Hi !!!

I just installed Ubuntu 8.10 and, on the previous ubuntu version, I managed to correctly patch my wireless driver following the steps on this page:

[http://www.developarts.com/parte1_ipw2200_inyeccion](http://www.developarts.com/parte1_ipw2200_inyeccion)

Now that I've installed Ubuntu 8.10, I tried to follow the same steps but the following errors appear when trying to make the ieee80211 subsystem 

```

root@gentoo:/opt/ipw2200_injection/ieee80211-1.2.18# make SHELL=/bin/bash
Checking in /lib/modules/2.6.27-7-generic for ieee80211 components...
make -C /lib/modules/2.6.27-7-generic/build M=/opt/ipw2200_injection/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.o
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_translate_scan’:
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:61: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:61: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:70: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:70: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:73: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:73: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:80: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:80: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:90: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:90: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:98: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:98: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:102: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:102: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:111: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:111: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:131: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:131: error: too few arguments to function ‘iwe_stream_add_value’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:138: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:138: error: too few arguments to function ‘iwe_stream_add_value’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:188: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:188: error: too few arguments to function ‘iwe_stream_add_event’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:195: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:195: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:215: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:215: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:236: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:236: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:248: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:248: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:269: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:269: error: too few arguments to function ‘iwe_stream_add_point’
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c: In function ‘ieee80211_wx_set_encodeext’:
/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.c:631: warning: format not a string literal and no format arguments
make[2]: *** [/opt/ipw2200_injection/ieee80211-1.2.18/ieee80211_wx.o] Error 1
make[1]: *** [_module_/opt/ipw2200_injection/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2


```

Does anyone know how to efficiently patch (and install) the ipw2200 wireless driver on ubuntu 8.10 (kernel 2.6.27-7-generic), or a page where I can find the install steps, please help me ?? [-o<

---

### Post by J172 on 2008-11-29
Apologies, I wasn't able to read the site you referenced. The issue might lie in the fact that you are atempting to port drivers yourself (I mean no offense). Since I can't read what the process entails if I am incorrect, please do correct me. I haven't tried the linux drivers from Intel, my Ibex install automatically installed IPW2200 drivers.

Perhaps try these (the intel released ones)
[http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net)

---

### Post by ubuntu_jazzbach on 2008-11-29
No problem :D, it wasn't an offense at all. I totally understand you !.

The thing is that, I already have the latest ieee subsystem but, I dunno how to patch it (sorry for being so noobish but, I even don't know why do I have to patch it).

I think the patch has something to do with the current (installed) kernel version.

If anyone could give me something like a step-by-step recipe for ultra dummies, I'd be very pleased !!!

Thanks !

---

### Post by ubuntu_jazzbach on 2008-11-29
I forgot to tell:

I know the wireless driver must be patched in order to inject packets (and I want it to inject packets so that I can attack a WEP-based wireless net). My problem is that I don't know how to patch it.

---

### Post by J172 on 2008-11-29
No issue at all, I've only been using Ubuntu as my primary (laptop, not desktop atleast) OS for five days, you pick up SO MUCH SO FAST!! This is where you've lost me. I think I'll keep an eye on this post however, it may come in handy should I require a patch. Its odd why you might and I don't, such are computers. I do hope someone knows the answer. IPW2200 are very common (they were used in Dell D600s and the D600s were a hit seller[I bought one :P]).

---

### Post by emilio320 on 2008-12-22
has there been any luck compiling and patching the ieee80211 subsystem? after following many tutorials the furthest i have gotten is removing the current subsystem successfully but i get an error when using the MAKE command in the downloaded subsystem directory. im using the same ubuntu 8.10 you are using with i beleive the 2.6.27-9-generic kernel

---

### Post by dmitriyp13 on 2008-12-23
bump

---

### Post by XaTriX on 2008-12-24
Same problem.
Ubuntu 8.10 / 2.6.27-7-generic.

Even with the patch which fix for 8.04..

XaT

---

### Post by silent contender on 2008-12-26
Is this the error you have?  (I hope I'm not the only one)
[URL="http://ubuntuforums.org/showthread.php?t=1020864&highlight=ieee80211"]
http://ubuntuforums.org/showthread.php?t=1020864&highlight=ieee80211[/URL]

---

### Post by sayw3rd on 2008-12-26
Hi, I am in the same boat as all of you. After doing some extensive research all over google and many  forum sites, I've concluded that the main problem of updating your ipw2200 to work with injection stems from installing the ieee80211 modules in Ubuntu 8.10 Intrepid.

Has anyone tried the steps from [http://www.waraey.com/blog/index.php](http://www.waraey.com/blog/index.php) yet?
They seem to be the  closest and most up-to-date steps for installing ipw2200 drivers, applying injection patch, and updating the firmware for ipw2000.

I've read from many forums that some users have been messing up their ipw2200 drivers and losing wireless connection following some older steps thus I haven't tried the steps from [http://www.waraey.com/blog/index.php](http://www.waraey.com/blog/index.php) myself yet. I'm waiting to back up my entire partition before I do so. If anyone else has already tried these steps and failed or succeeded please post a reply.

Also, I noticed that the Ubuntu 8.10 Intrepid ipw2200 FIRMWARE is located in the directory /lib/firmware/ by default (after install) and most guides to setting up  the ipw22000 drivers and firmware tell you to copy the firmware into /lib/firmware/2.x.xx-xx-generic/  (for example #sudo cp *.fw /lib/firmware/2.6.22-14-generic/)

So in addition to the ieee80211 subsystem problem, installing the firmware in the wrong place might be a problem also? I don't fully understand how Ubuntu works so correct me if I'm wrong since  I've just started using Ubuntu a few days ago. Does it matter where the firmware files go?

---

### Post by silent contender on 2008-12-27
You do not necessarily have to backup your partition.  I killed my wireless after trying to compile ieee80211.  But all that is needed to restore the wireless is reinstall the kernel packages (for 8.10 it's kernel 2.6.27-9-generic).

I would give credit to the thread I read, but I can't remember it.

Edit:
Just tried [http://www.waraey.com/blog/index.php]("http://www.waraey.com/blog/index.php") using:

```
sudo make SHELL=/bin/bash
```

and yes to all.  Did not work.:(

---

### Post by Vitron on 2009-01-01
Does anyone know what version of ubuntu this was working on?

Or have a fix? I'm running into the same problem...

---

### Post by arturosevilla on 2009-01-05
I do have a fix :D
I just looked at the differences between the kernel ABIs in 2.6.24 and 2.6.27 and came up with the attached solution.
You must follow the same instructions in [http://www.developarts.com/parte1_ipw2200_inyeccion]("http://www.developarts.com/parte1_ipw2200_inyeccion") (for the 2.6.24 kernel), but before you enter *sudo make* (or just *make* if you are behind a root shell) you must apply the attached patch:
```
patch ieee80211_wx.c ieee80211_wx.c-2.6.27.patch
```
Afterwards you should be able to compile and install the customized ieee80211 subsystem.
Note: I ran into some problems while applying the rtap_fix patch for the ipw2200 module, however i just opened the patch file and made the changes by hand (they are only two changes and very simple to handle).
Now just unload all your old modules, both ieee80211 and ipw2200, and reload them with the new ones just built.:D
I am able to use the new modules, however I haven't tested injection (I am too lazy and too busy), so if anyone can report on this I would appreciate it :).
Enjoy!

---

### Post by monk24 on 2009-01-06
Hey; I've been having the same problem, so I tried to use your patch, along with those directions that are in Spanish.  Well, maybe it's partly because I don't know Spanish and I had to translate the page to try to follow the instructions, but I'm still getting the same error messages about 'proc_net' being an undeclared variable.  Any tips/info, or an English version of the directions (in case I screwed that part up)?  Thanks!

---

### Post by arturosevilla on 2009-01-06
> **monk24 said:**
> Hey; I've been having the same problem, so I tried to use your patch, along with those directions that are in Spanish.  Well, maybe it's partly because I don't know Spanish and I had to translate the page to try to follow the instructions, but I'm still getting the same error messages about 'proc_net' being an undeclared variable.  Any tips/info, or an English version of the directions (in case I screwed that part up)?  Thanks!

The error about 'proc_net' you solve it with a patch that is provided in the page that is in Spanish (those about fixing the kernel for 2.6.24). In fact the patch that fixes it is: [http://www.sukria.net/en/ieee80211-2.6.18+linux-2.6.24.diff.txt](http://www.sukria.net/en/ieee80211-2.6.18+linux-2.6.24.diff.txt)

If you already patched it and it didn't work the only thing that you have to do is all those references from 'proc_net' to 'init_net.proc_net' (without the quotes). For example, from:
```
proc_mkdir(DRV_NAME, proc_net)
```
to
```
proc_mkdir(DRV_NAME, init_net.proc_net)
```

These changes should fix your problem.

---

### Post by monk24 on 2009-01-07
Awesome; I'll give that a try when I get home today and post the results.  Thanks for the response!

---

### Post by paper2cuts on 2009-01-08
can someone please explain where exatcly do I have to change references.
I have followed the tutorial and got the same problem when compiling ieee8011..(proc_net' being an undeclared variable)

---

### Post by skyline2412 on 2009-01-20
I got all stuff compiled and patch, but i have a problem more...
while I try the modprobe command...

sudo modprobe ipw2200 rtap_iface=1
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by sambita on 2009-02-04
Hello everyone, i was trying to patch ipw2200 following the steps posted in the spanish page, and the corrections made on this post, however, being the first time i tried to do something like this, i messed up, so now im out of wireless, can someone tell me how to go back to the original configuration so as to regain wireless access?

Thank you very much!

*Edit: ive been able to solve this problem. [here is how]("http://ubuntuforums.org/showthread.php?p=6688433#post6688433")

---

### Post by CATIV on 2009-02-25
Having the same issue. Can anybody confirm they have succesfully run aircrack-ng on 8.10 with ipw2200?

---

### Post by lexios on 2009-03-07
I have the same problems in make on ieee802.

Is there any success with the latest kernel in 8.10?

---

### Post by Adnanpay on 2010-02-22
I'm unable to download the attachment for the patch.txt, does anybody know why?

---

