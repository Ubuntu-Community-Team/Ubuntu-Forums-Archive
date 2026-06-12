---
title: "Can't install drivers"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by PeterDenStore on 2007-06-17
Hello,

I'm trying to follow this howto ([http://ubuntuforums.org/archive/index.php/t-132980.html](http://ubuntuforums.org/archive/index.php/t-132980.html)) and when I get to the make all command I get the following message:

"ubuntu@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
sudo: make: command not found"

I've tried in both 7.04 and 6.06 both give me the same error. 
Is there something I'm missing?

Thanks!
Pete

---

### Post by SeanHodges on 2007-06-17
To compile from source code you need to install make, and the other build tools first:

```
sudo apt-get install build-essential
```

should do the trick

---

### Post by Swab on 2007-06-17
You don't have make installed.

```
sudo apt-get install build-essential
```

will take care of that.

---

### Post by PeterDenStore on 2007-06-17
Now I seem to get the following error:

ubuntu@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2
ubuntu@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ make
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2


thanks for all the help.
Pete

---

### Post by chili555 on 2007-06-17
sudo apt-get install linux-headers-`uname -r`

That's the backtick, that's up by the 1 on your keyboard.

Then *make* should make.

---

### Post by PeterDenStore on 2007-06-17
You talking about ~ and where should get go?

Thanks,
Pete

---

### Post by PeterDenStore on 2007-06-17
ok never mind I see what you were saying now. but now I got the following message:

```
ubuntu@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ cd '/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module' 
ubuntu@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
ubuntu@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$
```

So I still haven't got past the error 2  :( So I still need more help please!

thanks for the help!
Pete

---

### Post by chili555 on 2007-06-18
This post helped me to 'make all.' [http://ubuntuforums.org/showthread.php?t=415693&highlight=RT61](http://ubuntuforums.org/showthread.php?t=415693&highlight=RT61)

Especially this part:> in file:
/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c

comment out line 197, it should look like this:

#if WIRELESS_EXT >= 12
**//** net_dev->get_wireless_stats = RT61_get_wireless_stats;
net_dev->wireless_handlers = (struct iw_handler_def *) &rt61_iw_handler_def;
#endif

By the way, rt61.ko exists in your kernel right now. Any reason this is not working for you?

---

### Post by PeterDenStore on 2007-06-18
It wont seem to connect to anything. I can see the networks but cannot to connect to them at all. with or without wep. I've been trying to get this card to work in linux for about a month now. But half of that could be I'm very new to linux. I will hopefully get to try that thread once I get home from work. 

Thanks for all your help.

---

