---
title: "Hardwire LAN not working"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by hmag on 2013-12-31
Hello

I repost this question 3 days after a 1st post associated to another unlucky fellow with same issue...

I am running 12.04 LTS on an ASUS, my LAN card used to work until recently.
It is no longer visible in ifconfig thus I suspect a kernel issue.

NOT a hardware problem, I have a dual boot and all works fine with MSWindows

Below a few elements.

Early thanks & BR
HMag

```


root@asus2:~# uname -a
Linux asus2 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lspci | grep net
03:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:126 erreurs:0 :0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:11996 (11.9 KB) Octets transmis:11996 (11.9 KB)

wlan0     Link encap:Ethernet  HWaddr dc:85:de:6d:f0:32  
          inet adr:192.168.1.14  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::de85:deff:fe6d:f032/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:3189 erreurs:0 :0 overruns:0 frame:0
          TX packets:1535 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1375793 (1.3 MB) Octets transmis:296427 (296.4 KB)


```

---

### Post by chili555 on 2013-12-31
Did you compile the driver *alx* from source code like this? [http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)  If you compiled, it was only for your current kernel version. If you got an updated kernel from Update Manager, you need to recompile:```
cd ~/compat-wireless-2012-07-03-pc  [COLOR="#FF0000"]<--or whatever you downloaded[/COLOR]
make clean
./scripts/driver-select alx
make
sudo make install
```

What happens if you try to load the driver?```
sudo modprobe alx
```

---

### Post by hmag on 2014-01-01
Hi Chili555

Thanks for your help.
I never dowloaded or compiled anything related to the kernel. I just installed 12.04LTS on my laptop after purchased.
All worked fine until recently (probably due to a new kernel installed by a recent automatic update).

To date I don't have any "alx" on my machine, ...
```

root@asus2:~# modprobe -l | grep alx
root@asus2:~# 


```

I am a little bit surprised that I now would have to manage this manually, while the installation procedure did it very well 1+ year ago...
From where can I get this "alx" kernel module ?

Thanks !
HMag

---

### Post by chili555 on 2014-01-01
Let's just verify your device first:```
lspci -nn | grep 0200
```Thanks.

---

### Post by hmag on 2014-01-03
Ok ;-)

```

hmag@asus2:~$ lspci -nn | grep 0200
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)


```

---

### Post by chili555 on 2014-01-03
Well, the module *alx* is correct for your device. I am baffled as to how it could work previously if alx isn't on your system. What does this tell us?```
modinfo alx
sudo modprobe alx
```

---

### Post by hmag on 2014-01-04
Hi chili555

2 days ago I provided a :

```


hmag@asus2:~$ modprobe -l | grep alx
hmag@asus2:~$ 


```

... that provides no answer

Meaning that we could expect the below response froml the system :
```


hmag@asus2:~$ modinfo alx
ERROR: modinfo: could not find module alx
hmag@asus2:~$ 


```

FYI, last week I had the automatic update of my laptop after many months not using it.
Maybe something has been broken, because since last week update, Ubuntu update manager does not show any new update ("system is up to date")...
Any way to refresh this ?

THanks,

---

### Post by praseodym on 2014-01-04
Try this driver:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/55/19/4987097-alx_dkms-cw20121003.tar.gz
sudo tar xvf 4987097-alx_dkms-cw20121003.tar.gz -C /usr/src
sudo dkms add alx_dkms -v cw20121003
sudo dkms build alx_dkms -v cw20121003
sudo dkms install alx_dkms -v cw20121003
sudo depmod -a && sudo update-initramfs -u 
```
Check:```

dkms status
modinfo alx
sudo modprobe -v alx
ifconfig -a 
```

---

### Post by hmag on 2014-07-12
Hi praseodym

Sorry for my late reply, I used wireed LAN for some time, as well as other computers....

I get blocked at DKMS build: 

```
root@asus2:~# dkms build alx_dkms -v cw20121003

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' -C src/compat-wireless-2012-10-03-pc_alx_only all......(bad exit status: 2)
ERROR (dkms apport): binary package for alx_dkms: cw20121003 not found
Error! Bad return status for module build on kernel: 3.2.0-65-generic (x86_64)
Consult /var/lib/dkms/alx_dkms/cw20121003/build/make.log for more information.
root@asus2:~# gedit /var/lib/dkms/alx_dkms/cw20121003/build/make.log &
[1] 7856
root@asus2:~#
```

Below what /var/lib/dkms/alx_dkms/cw20121003/build/make.log says :

Early Thanks for your additional help ;-)
BR
HMag

```
DKMS make.log for alx_dkms-cw20121003 for kernel 3.2.0-65-generic (x86_64)
samedi 12 juillet 2014, 20:55:33 (UTC+0200)
make: entrant dans le répertoire « /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only »
./scripts/gen-compat-autoconf.sh /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/.config /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/3.2.0-65-generic/build M=/var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-65-generic »
  CC [M]  /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/compat/main.o
In file included from /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/include/linux/compat-2.6.h:65:0,
                 from <command-line>:0:
/var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/include/linux/compat-3.4.h:43:21: erreur: redefinition of ‘kmalloc_array’
include/linux/slab.h:243:21: note: previous definition of ‘kmalloc_array’ was here
make[3]: *** [/var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/compat/main.o] Erreur 1
make[2]: *** [/var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only/compat] Erreur 2
make[1]: *** [_module_/var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-65-generic »
make: *** [modules] Erreur 2
make: quittant le répertoire « /var/lib/dkms/alx_dkms/cw20121003/build/src/compat-wireless-2012-10-03-pc_alx_only »
```

---

### Post by praseodym on 2014-07-13
```
sudo apt-get install linux-backports-modules-cw-3.4-precise-$(uname -r | cut -c10-23) 
```
should do the trick.

---

### Post by laughton.andrew on 2014-07-14
I am not sure if this is the correct place for this post but anyway;

I have had issues with ethernet not working as well, the system does not see the hardware.
I updated using Internet over my phone and the USB port, and ethernet worked again.
Another update, another failure, I am not sure how many times.
It last worked around 12th June 2014.  I updated again via my phone, still no ethernet.

I booted up on an 14.04 install USB drive, and ethernet / Internet worked.
I wrote down output from different command line instructions to ID the hardware, then rebooted onto the hard drive install.
Without doing anything else, ethernet / Internet now works as it should.

I am guessing the USB boot disk tickled the ethernet hardware in some way that the newer version does not.

Andrew.

---

