---
title: "ndiswrapper not working"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2009-01-19
I downloaded ndiswrapper form [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) I have followed the install file.

I have an acer aspire 4720z with 2.6.28 kernel.

root@bermudez:~/Shared/ndiswrapper-1.52# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
root@bermudez:~/Shared/ndiswrapper-1.52# make
make -C driver
make[1]: Entering directory `/home/lance/Shared/ndiswrapper-1.52/driver'
make -C /usr/src/linux-2.6.28 SUBDIRS=/home/lance/Shared/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-2.6.28'
  LD      /home/lance/Shared/ndiswrapper-1.52/driver/built-in.o
  CC [M]  /home/lance/Shared/ndiswrapper-1.52/driver/crt.o
  CC [M]  /home/lance/Shared/ndiswrapper-1.52/driver/hal.o
  CC [M]  /home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.o
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: error: too few arguments to function ‘iwe_stream_add_value’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/lance/Shared/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.28'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/lance/Shared/ndiswrapper-1.52/driver'
make: *** [all] Error 2
root@bermudez:~/Shared/ndiswrapper-1.52# make install
make -C driver install
make[1]: Entering directory `/home/lance/Shared/ndiswrapper-1.52/driver'
make -C /usr/src/linux-2.6.28 SUBDIRS=/home/lance/Shared/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-2.6.28'
  CC [M]  /home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.o
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c: In function ‘ndis_translate_scan’:
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1039: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1049: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1055: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1066: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1081: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 1 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 3 of ‘iwe_stream_add_event’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: warning: passing argument 4 of ‘iwe_stream_add_event’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1095: error: too few arguments to function ‘iwe_stream_add_event’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1106: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 1 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 4 of ‘iwe_stream_add_value’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: warning: passing argument 5 of ‘iwe_stream_add_value’ makes pointer from integer without a cast
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1122: error: too few arguments to function ‘iwe_stream_add_value’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1133: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1139: error: too few arguments to function ‘iwe_stream_add_point’
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 1 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 3 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: warning: passing argument 4 of ‘iwe_stream_add_point’ from incompatible pointer type
/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.c:1162: error: too few arguments to function ‘iwe_stream_add_point’
make[3]: *** [/home/lance/Shared/ndiswrapper-1.52/driver/iw_ndis.o] Error 1
make[2]: *** [_module_/home/lance/Shared/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.28'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/lance/Shared/ndiswrapper-1.52/driver'
make: *** [install] Error 2

I have already uninstalled and purged the ndiswrapper files with synaptic

---

### Post by adult swim on 2009-01-19
try pasting these commands into your terminal
```
cd

sudo apt-get install build-essential

sudo apt-get install linux-headers-`uname -r`

``` and then run ```
cd ~/Shared/ndiswrapper-1.52

make 

sudo make install
```

---

### Post by lance bermudez on 2009-01-20
I have those installed already i have attached the out put from my commands.

---

### Post by handydan918 on 2009-01-20
Why are you trying to compile?

 ndiswrapper has got to be in the repos....

---

### Post by lance bermudez on 2009-01-20
Becuse the one in the repo dosent work with the 2.6.28 kernel. I have uninstalled in and reinstalled it and it still does not work.

---

### Post by ugm6hr on 2009-01-20
> **lance bermudez said:**
> Becuse the one in the repo dosent work with the 2.6.28 kernel. I have uninstalled in and reinstalled it and it still does not work.

Which version of Ubuntu are you running?  Only Jaunty has 2.6.28 as far as I know - Jaunty is still in alpha (or is it beta now?) - so if that is what you have installed - please ask your question in the development section (i.e. stay out of Absolute Beginners).

---

### Post by lance bermudez on 2009-01-20
I’m not sure if you meaning to be put you seem a little rude ugm6hr with your stay out i.e. comment. I used kernel check to get the next kernel 2.6.28 because I was told it should have better drivers for my wireless card. Because I still did not know how to get it to work right I posted here. Sorry to have up set you I will move to where you advise.

---

### Post by ugm6hr on 2009-01-20
> **lance bermudez said:**
> I’m not sure if you meaning to be put you seem a little rude ugm6hr with your stay out i.e. comment.

That was not my intention.

Absolute Beginner's is not the place to be asking about unsupported upgrades, since it is likely that those offering advice here will not be in a position to help.

If you want to stick with an unsupported kernel, I'd suggest you ensure that you explain that is what you have done in a new support thread in either the development section (if you have Jaunty), or somewhere in Main Support if you have rolled your own kernel.

If you are genuinely a beginner, I'd suggest you start again with a supported version of Ubuntu.

Hope that clears things up.

---

