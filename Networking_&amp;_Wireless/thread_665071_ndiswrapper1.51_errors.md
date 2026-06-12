---
title: "ndiswrapper1.51 errors"
date: 2008-01-11
forum: Networking &amp; Wireless
---

### Post by mrxtambourineman on 2008-01-11
I'm running the 64 bit version of ubuntu 7.1. When I try to install ndiswrapper i get the following errors: 

eric@portablevegan:~/ndiswrapper-1.51$ make install 
make -C driver install 
make[1]: Entering directory `/home/eric/ndiswrapper-1.51/driver' 
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/eric/ndiswrapper-1.51/driver 
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  Building modules, stage 2. 
  MODPOST 1 modules 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
echo /lib/modules/2.6.22-14-generic/misc 
/lib/modules/2.6.22-14-generic/misc 
mkdir -p /lib/modules/2.6.22-14-generic/misc 
install -m 0644 ndiswrapper.ko /lib/modules/2.6.22-14-generic/misc 
install: cannot remove `/lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko': Permission denied 
make[1]: *** [install] Error 1 
make[1]: Leaving directory `/home/eric/ndiswrapper-1.51/driver' 
make: *** [install] Error 2 

Can anyone tell me what I need to do to get ndiswrapper installed correctly? I just installed ubuntu earlier today. I am the only user for ubuntu too so it's not like I'm not the admin or anything... Also, keep in mind that I'm new to ubuntu/linux. Thank you for the help.

Eric

---

### Post by Rockman4140 on 2008-01-11
An idea would be to try running the command with sudo before it. It'll ask for your password, but it should give you the permissions you need.

I'm a novice as well, and messing with sudo can be bad news if you don't know what you are doing, so I would wait until you can get a more helpful post.

---

### Post by mrxtambourineman on 2008-01-12
Thanks a lot! It worked.

---

