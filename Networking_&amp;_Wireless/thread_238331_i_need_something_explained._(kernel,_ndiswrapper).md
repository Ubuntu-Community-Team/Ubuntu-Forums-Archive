---
title: "i need something explained. (kernel, ndiswrapper)"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by 0okami on 2006-08-17
with a new kernel, i can NOT run ndiswrapper: 

```
ookami@localhost:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
mrv8k51         driver present, hardware present
ookami@localhost:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-23-386/misc/ndiswrapper.ko): Invalid argument
ookami@localhost:~$

```

I tried building/making but it was spitting out an error i dont have handy at the moment...  
 
after rebooting and selecting a different option in grub, i can do sudo make install, configure the drivers, and modprobe ndiswrapper without any issues. Why? whats going on? Im new to this sorry.  
```

ookami@localhost:~/Desktop/ndis$ sudo make install
make -C driver install
make[1]: Entering directory `/home/ookami/Desktop/ndis/driver'
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/ookami/Desktop/ndis/drive r
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-23-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-23-386'
echo /lib/modules/2.6.15-23-386/misc
/lib/modules/2.6.15-23-386/misc
mkdir -p /lib/modules/2.6.15-23-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.15-23-386/misc
/sbin/depmod -a 2.6.15-23-386 -b /
make[1]: Leaving directory `/home/ookami/Desktop/ndis/driver'
make -C utils install
make[1]: Entering directory `/home/ookami/Desktop/ndis/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must r e-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/ookami/Desktop/ndis/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
ookami@localhost:~/Desktop/ndis$ cd ..
ookami@localhost:~/Desktop$ ls
curly-009ab7e595.desktop   ndiswrapper problems.file~
larry-003faae01f.desktop   ndiswrapper-utils_1.8-0ubuntu2_i386.deb
navi_xorg.conf             new file~
ndis                       tri-mon xorg.conf
ndiswrapper-1.23.tar.gz    Win98
ndiswrapper problems.file
ookami@localhost:~/Desktop$ cd Win98
ookami@localhost:~/Desktop/Win98$ ls
mrv8k51.inf  MRV8K51.sys
ookami@localhost:~/Desktop/Win98$ sudo ndiswrapper -i mrv8k51.inf
Installing mrv8k51
ookami@localhost:~/Desktop/Win98$ ndiswrapper -l
Installed drivers:
mrv8k51         driver installed, hardware present
ookami@localhost:~/Desktop/Win98$ sudo modprobe ndiswrapper

# ookami configured the rest via gui and tested:

ookami@localhost:~/Desktop/Win98$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=238 time=42.3 ms
64 bytes from 72.14.207.99: icmp_seq=2 ttl=238 time=41.6 ms
64 bytes from 72.14.207.99: icmp_seq=3 ttl=238 time=40.4 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 40.482/41.509/42.367/0.796 ms
ookami@localhost:~/Desktop/Win98$


```


so im really puzzled as to why i cant get ndiswrapper working in the updated kernell... its asking about pointing it to some build something... damnit im out of time :( 

i'll edit this later when i get back from work.

Edit: what an oversight on my behalf... looks like i've experience this before.  lol. [http://ubuntuforums.org/showthread.php?t=170212](http://ubuntuforums.org/showthread.php?t=170212) 
I will try that again when i get home.

---

