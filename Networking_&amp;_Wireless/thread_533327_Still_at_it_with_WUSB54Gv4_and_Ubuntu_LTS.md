---
title: "Still at it with WUSB54Gv4 and Ubuntu LTS"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by CoriolisSTORM on 2007-08-23
Alright gents, I'm still at it again with trying to install NDISwrapper and use my WUSB54Gv4 on a WPA network.  Anyway, I've tried following the guides here, but when I try to get run 
```
make
``` it gives me error code 1 and then error code 2 for NDISwrapper.  exact text is thus:  

```
rob@rob-desktop:~/Desktop/ndiswrapper-1.47$ sudo make
make -C driver
make[1]: Entering directory `/home/rob/Desktop/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/rob/Desktop/ndiswrapper-1.47/driver'
make: *** [all] Error 2

```

What do I need to do?  Once I've gotten past this, then what?  I've also tried to use the included original NDISwrapper on the CD, but I get an error about an invalid driver even though I use the WUSB54Gv4 one.  Once I get the correct ndiswrapper installed, what next?  Also, how do I configure it for WPA access?  I'm currently using a wired network bridge with my cuz's laptop who was nice enough to set in here with me whilst working on it.

---

### Post by CoriolisSTORM on 2007-08-23
NVM, got it to make, now I'm trying to install the driverm  and it won't do it.  
Got to looking and my device is also still found in the network settings area even though I have blacklisted rt2570 like the tutorial says.  thoughts?

---

### Post by CoriolisSTORM on 2007-08-23
Haha!  Getting better at it I think, I've got the card configured and ready to go, how do I use it to connect to a WPA network?  I'm totally new at this, so can you please put it in terms I can understand?  
Note on how I got it installed for those of you who cared:  Follow the install guide at the top of the page and USE THE VERSION OF NDISWRAPPER INCLUDED IN THE THREAD.

---

