---
title: "iBurst HOW-TO for Ubuntu 7.04 (Feisty Fawn)?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by damies on 2007-04-23
Hi All,

I would like to thank Skrewdriver for the "iBurst PCMCIA How-TO" and "iBurst HOW-TO for Edgy"which helped me get my USB iBurst modem working under Edgy.

I just tried these same instructions under Feisty Fawn and the driver failed to compile, I am wondering if anyone has had any success? 

Cheers,

Dave.

---

### Post by hendo2007 on 2007-04-29
Ditto - I have burnt quite a few hours so far and am getting nowhere on this. I ran through the same as above and it also sounds like I am getting the same compile error as mentioned above. Has anyone had any success? Thanks.

---

### Post by hendo2007 on 2007-04-29
A new ib-driver is now on [http://sourceforge.net/projects/ibdriver/](http://sourceforge.net/projects/ibdriver/) that works for 2.6.20. I followed the instructions by Skrewdriver  - all worked fine. Skrewdriver - you are the end of a leg - thanks.

---

### Post by ellisdee on 2007-05-10
Excellent, thank you for the drivers link! This works for me too ;)

---

### Post by onegreenparker on 2007-06-20
I downloaded the drivers from Sourceforge, made them no problem, installed rp-pppoe, set it up, no problem so far....

But then sometimes when I connect to the internet my machine hangs as soon as I hit Enter. Or I get connected, but after that I can't connect ever again.

Any suggestions?

---

### Post by Xenonis on 2007-06-21
Yeah, I'm experiencing some problems too, I think the driver might be a little unstable. My system crashes a few seconds after connecting. I also found, if i leave my modem on will booting into Ubuntu nothing works, I can't open terminals or use applications, I have to turn on the modem after loging in. Really strange.

Anyway just my 2c.

Can anyone help?

---

### Post by onegreenparker on 2007-07-20
BUMP
Any suggestions?
I'd really rather be using Feisty than Dapper, but if I can't get my iBurst USB working.......

:(

---

### Post by Xenonis on 2007-07-26
Hey onegreenparker!

Yeah I did some snooping around(I've tried Fedora and openSuse) and it looks like all the other distro's have the same problem. It's got something to do with the new kernel. I geuss we'll just have to wait for more stable drivers.

Are you on PLUG? You should be, I'd like to mail you.

---

### Post by onegreenparker on 2007-08-04
Perhaps a little more info will help......

I've followed the HOWTO at [https://help.ubuntu.com/community/MobileWirelessBroadband](https://help.ubuntu.com/community/MobileWirelessBroadband)
Installed libc6-dev without a problem.

However 
```

make

```

gives me
```

ian@onegreenparker:~/ibdriver-1.3.2-linux-2.6$ make
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ian/ibdriver-1.3.2-linux-2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ian/ibdriver-1.3.2-linux-2.6/ib-net.o
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:462: warning: initialization from incompatible pointer type
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:463: warning: initialization from incompatible pointer type
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:464: warning: initialization from incompatible pointer type
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:529:50: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c: In function ‘ib_net_register’:
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:529: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:529: error: (Each undeclared identifier is reported only once
/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.c:529: error: for each function it appears in.)
make[2]: *** [/home/ian/ibdriver-1.3.2-linux-2.6/ib-net.o] Error 1
make[1]: *** [_module_/home/ian/ibdriver-1.3.2-linux-2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

```

On the HOWTO mentioned above there is talk of a patch for the driver, but in the ibdriver README it says that the patch was incorporated into version 1.2.9 of the driver. And also when I tried the patch, I was told, very politely by the terminal, that the patch had already been done.

Also mentioned was the possible need for kernel-devel to be installed in order to build properly. I searched on Synaptic for this package but found nothing.

Pretty please, help me. I need to use either the USB or PCMCIA as I am using an HP 6715s notebook and I need to be mobile.

Thanks

---

### Post by onegreenparker on 2007-08-10
OK, I downloaded the correct version of ibdriver, which is ibdriver-1.3.2-linux-2.6.20 ([found here)]("http://sourceforge.net/project/downloading.php?group_id=138984&use_mirror=belnet&filename=ibdriver-1.3.2-linux-2.6.20.tar.gz&67934202").

Succesful when I:
```
make
```
Succesful when I
```
sudo make install
```

Also, successful with rp-ppoe when I
```
sudo ./go
```

However, when I 
```
 sudo ifup ib0
```
I get 
```
............Timed Out!
Failed to bring up ib0.
```

I have removed Network Manager, as I have read somewhere that it sometimes interferes with this setup.

Any ideas?

---

### Post by onegreenparker on 2007-08-11
Update:

Without chaning anything, I get connected..... yay!

But, when I try to access any webpage, Firefox tells me that 'Server Not Found'.....boooo!

When I check pppoe-status, I get

```

ian@onegreenparker:~/rp-pppoe-3.8$ pppoe-status
pppoe-status: Link is up and running on interface ppp0
	  ppp0      Link encap:Point-to-Point Protocol  
          inet addr:196.2.116.71  P-t-P:196.2.112.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1392  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:474 (474.0 b)  TX bytes:397 (397.0 b)

```

...and this was after about 30 minutes. 

So, in summary, I am connected but the speed is something akin to dialup of the year 1927.

---

### Post by Skrewdriver on 2007-08-11
okay folks, I'm in hospital, doped up on morphine so my responses may be a little more incoherent than usual.
First off, I too have had problems compiling the drivers under feisty, so have installed a different kernel version (from edgy) : 2.6.17-50-generic.
you can get the necessary files from the Ubuntu repos via firefox.
It all becomes a bit messy when you then try to implement the latest NVIDIA drivers, but I'm not going to get sidetracked.
so now I have feisty and mobile broadband.
The guys developing the drivers on Sourceforge are aware that there is a problem with the driver and the current kernel, they are working on it (I think). I've filed all the relevant bug reports, support requests etc

nurse!!

---

### Post by onegreenparker on 2007-08-26
Seems I've missed something, have a look at the output below, what am I missing?

```

ian@onegreenparker:~/ibdriver-1.3.2-linux-2.6.17$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/ian/ibdriver-1.3.2-linux-2.6.17 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-generic/build'
make: *** [default] Error 2

```

BTW, this is when I make ibdriver-1.3.2-linux-2.6.17 when using 2.6.17-50-generic kernel.

---

### Post by Skrewdriver on 2007-08-26
looks like you are missing kernel source files for that version of kernel.

download here:
[LIST=1]
[*][http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10)
[*][http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic)
[/LIST]

---

### Post by mabb on 2007-12-30
> **onegreenparker said:**
> OK, I downloaded the correct version of ibdriver, which is ibdriver-1.3.2-linux-2.6.20 ([found here)]("http://sourceforge.net/project/downloading.php?group_id=138984&use_mirror=belnet&filename=ibdriver-1.3.2-linux-2.6.20.tar.gz&67934202").

Succesful when I:
```
make
```
Succesful when I
```
sudo make install
```

Also, successful with rp-ppoe when I
```
sudo ./go
```

However, when I 
```
 sudo ifup ib0
```
I get 
```
............Timed Out!
Failed to bring up ib0.
```

I have removed Network Manager, as I have read somewhere that it sometimes interferes with this setup.

Any ideas?


I have same porblem ( failed to bring up ib0) , Any suggestions ????????????:confused::confused::confused:

---

### Post by baignoire on 2008-01-13
hi
kind of same problem here with usb iburst : make install of drivers went ok, pppoe install/configure semmed to be ok too
but i do : "sudo ifup ib0" i have :
--------------------------------
/bin/sh: ipconfig: not found
Failed to bring up ib0.
--------------------------------
i m with a brand new install of ubuntu 7.10 gutsy
if someone can help......
thanks a lot

---

### Post by Keane on 2008-01-14
Excuse any non-sense. I'm very new to Ubuntu...

I went through the process of compiling and also eventually got the line: Failed to bring up ib0.

That was last night. This morn I read that in respect of Gutsy, the command should be "sudo ifup ib" and not "sudo ifup ib0".

I haven't had a chance to try this yet but it will later. Thought it might help. The thread I saw it on included Skrewdriver and it might even have been written by him.

If this works, please indicate on the thread.

---

### Post by insanoff on 2008-03-04
but when I
```
sudo ifup ib0
```
get
```
Timed Out!
Failed to bring up ib0
```
and when
```
sudo ifup ib
```
nothing happen!
what i may do???
:confused::confused::confused:

thanks!

---

### Post by SpockEars on 2008-03-05
Check your /var/log/messages 
and your dmesg

This should tell you why this is timing out.

Are you using a dialer eg Roaring Penguin?

Check the Readme file that you installed with the driver

---

### Post by scrime on 2008-03-16
I'm running Kubuntu 7.10, using external iBurst modem.  After 2 days of trying to compile the ibdriver, I gave up.  A solution I've found is connect the ethernet cable, run Roaring Penguin with default options (except username and password) and it connects works.  Yay!  Only problem is I'll have to install another network card or something if I want to network with other machines.

---

### Post by jkanounji on 2008-03-27
Hello people

For those of you who are having problem with  ifup ib0, 
Try the following:

sudo ifconfig ib0 up

works like a charm enjoy:guitar:

---

