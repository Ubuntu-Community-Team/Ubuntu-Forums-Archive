---
title: "[SOLVED] Can't compile ndiswrapper 1.53"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by koji042 on 2008-11-05
I recently installed Xubuntu 8.10 on my laptop and everytime I try the "make" command from the terminal, it seems to work initially before blowing out a ton of error messages:

```
winston@winston-laptop:~$ cd ndiswrapper-1.53
winston@winston-laptop:~/ndiswrapper-1.53$ make
make -C driver
make[1]: Entering directory `/home/winston/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.27-7-generic M=/home/winston/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/winston/ndiswrapper-1.53/driver/iw_ndis.o
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c: In function &#8216;ndis_translate_scan&#8217;:
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1037: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1037: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1047: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1047: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1053: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1053: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1064: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1064: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1079: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1079: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1093: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1093: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1104: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1104: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 1 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 4 of &#8216;iwe_stream_add_value&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1120: warning: passing argument 5 of &#8216;iwe_stream_add_value&#8217; makes pointer from integer without a cast
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1120: error: too few arguments to function &#8216;iwe_stream_add_value&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1131: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1131: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1137: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1137: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1159: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/home/winston/ndiswrapper-1.53/driver/iw_ndis.c:1159: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/home/winston/ndiswrapper-1.53/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/winston/ndiswrapper-1.53/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/winston/ndiswrapper-1.53/driver'
make: *** [all] Error 2
winston@winston-laptop:~/ndiswrapper-1.53$ 

```
This is my first time trying to compile anything, so I have no idea what I might be doing wrong.
Following the INSTALL text, I've the kernel header files are there, and I also have the "build-essential" package installed, so could this just be an incompatible kernel? I've tried several times (with 1.52 and 1.53) to no avail. The results would amount to something similar to the output above; it would compile a few files successfully and then fail.

Any help is appreciated. Thanks much. ^.^

---

### Post by koji042 on 2008-11-06
Bump.

Has anyone been able to compile ndiswrapper on Intrepid? I've been scrolling through the forums and I just really don't know anymore. ndiswrapper seems to work for some and completely black out on others. -.-

---

### Post by Ayuthia on 2008-11-06
You can't compile ndiswrapper without a patch in 2.6.27 (Intrepid).  You can check out this link:
[http://www.linuxquestions.org/questions/slackware-14/ndiswrapper-and-2.6.27-675886/](http://www.linuxquestions.org/questions/slackware-14/ndiswrapper-and-2.6.27-675886/)
It has a link to a [patch]("http://www.slackware.com/~alien/slackbuilds/ndiswrapper/build/ndiswrapper_kernel_2.6.27.patch").  It was listed for slackware, but the patch looked like another one that I saw so I am guessing that it should work (I have not tried it out yet).

Just save the patch under something like ndiswrapper_2.6.27.patch then go into the ndiswrapper directory (the one where you would do the make and make install) and do the following:
```
patch -p1 < ndiswrapper_2.6.27.patch
```
Then compile the code.  Hope that helps.

EDIT: By the way, have you tried the ndiswrapper from the repositories?  It is currently at 1.52 in Intrepid.  It might work fine.  Just install ndiswrapper-utils-1.9.

---

### Post by koji042 on 2008-11-06
I've tried the one in the repositories but but I get a FATAL error and the wiki advised that I compile it instead so.... here I am.

Thanks much, I'll try the patch as soon as I get home from school. ^.^

---

### Post by koji042 on 2008-11-06
Well I've successfully managed to compile ndiswrapper, but now I can't seem to get my wireless card working. 

I've installed the driver already: 
```
winston@winston-laptop:~$ net8185 : driver installed
device (1799:701F) present (alternative driver: rtl8180)

```

Thanks.

EDIT: I think that the problem is that the alternative driver (rtl8180) is interfering with the one I installed. But entering "blacklist rtl8180" into the blacklist file (/etc/modprobe.d/blacklist) doesn't seem to do anything.

EDIT: Wireless now seems to work (as in it appears in the menu), however, the lights on my wireless card still aren't active and I can't actually connect to any network... o.o

EDIT: Okay... it works now. I suppose blacklisting rtl8180 did the trick (along with a reset). Finally solved for good. ^(^.^)^

---

