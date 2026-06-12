---
title: "Trouble installing ndiswrapper?"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by Vekemi on 2006-09-26
Here's the issue I have:

```

vekemi@vekemi-laptop~/ndiswrapper-1.23$ sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
vekemi@vekemi-laptop~/ndiswrapper-1.23$ sudo make
make -C driver
make[1]: Entering directory `/home/vekemi/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build; give the path to kernel build directory with KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/vekemi/ndiswrapper-1.23/driver'
make: *** [all] Error 2
vekemi@vekemi-laptop~/ndiswrapper-1.23$ sudo make install
make -C driver
make[1]: Entering directory `/home/vekemi/ndiswrapper-1.23/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build; give the path to kernel build directory with KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/vekemi/ndiswrapper-1.23/driver'
make: *** [all] Error 2
vekemi@vekemi-laptop:~/nidswrapper-1.23$

```

Can anyone help?

---

### Post by pay on 2006-09-26
You need to point it to the kernel. ie KBUILD=/usr/src/<yourkernel>

---

### Post by Vekemi on 2006-09-27
My /usr/src directory is completely empty.

:x

---

### Post by davey.moore on 2006-09-27
Im having exactly the same problem here :-k

---

### Post by siiib on 2006-09-27
(*,) this is one of the problems with ubuntu and is my big beef with it apart from the fact that this bl88dy synaptics touch pad causes the cursor to jump around all over the place.. sorry

the install doesn't install the sources to save space on the cd .. apparently.. pain in the arse for the uninformed..everyone finds out the hard way](*,) 

you need to do a sudo apt-get install kernel-headers and perhaps a bunch of other stuff like you'd need to be able to do a kernel rebuild have a look at the kernel howto.. normally . .sorry ..back in the day the distro would install the headers and source as well so that you could do this stuff..ubuntu doesn't.. which is okay but it doesn't tell you .. so you can do sod all in effect..

sorry i have to go .. will try and help tomorrow.. btw ndiswrapper is a BOS.. my solution was to buy a new wifi card that was supported.. ten quid off ebay... if only i could get rid of this touchpad](*,) hth

---

### Post by Vekemi on 2006-09-27
```
sudo apt-get install kernel-headers
``` would assume that I have an Internet connection, which I don't have on Ubuntu, right? Or can I do it off the LiveCD?

---

### Post by siiib on 2006-09-28
ahh GOTCHA!! sincere apologies.. i never thought of that .. could you run a temporary cable?.. i always have a 20m cat5 cable spare.. just in case;-)  down the stairs.. through the hall.. not ideal but good for emergencies..

i always thought the source packages were on the cd in dist.. dapper.. main.. although i don't have a cd to hand atm.. try it.. aptitude should pick it up if it is in the cd repository as it will be listed in the /etc/apt/sources.lst

---

### Post by Vekemi on 2006-09-28
I'm getting more errors after ```
sudo apt-get install kernel-headers
```

._.

```

make -C driver
make[1]: Entering directory `/home/vekemi/ndiswrapper-1.23/driver'
make -C /usr/src/kernel-headers-2.4.27-2 SUBDIRS=/home/vekemi/ndiswrapper-1.23/driver
make[2]: Entering directory `/usr/src/kernel-headers-2.4.27-2'
make: Entering an unknown directory
make: *** arch/i386/boot: No such file or directory.  Stop.
make: Leaving an unknown directory
make[2]: *** [archdep] Error 2
make[2]: Leaving directory `/usr/src/kernel-headers-2.4.27-2'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/vekemi/ndiswrapper-1.23/driver'
make: *** [all] Error 2

```

---

### Post by siiib on 2006-09-28
have you got the right headers.. your first post refers to 2.6.15 and your last one 2.4.something .. 
OTOH you do an apt-get install kernel-headers(uname -r) to get the right ones.. i may be wrong about this (don't have black book on me) perhaps someone else can put you right on this til i get home..

---

