---
title: "Need help with D-Link Wireless Card installation (DWA-542)"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by okkiedokki on 2008-08-31
Let me start out that I am completely over my head and I have no clue what I am doing; I installed Ubuntu 8.04.1 today.  

Now that is out, I've done lspci -nn and found out i have the AR5416 chipset.  I then proceeded to madwifi.org and got the file and followed the steps in the first time how to and I get errors all over the place.

When I'm in the scripts directory I type:
```
./madwifi-unload
```
And I get:
```
bash: ./madwifi-unload: No such file or directory

```

I then type:
```
./find-madwifi-modules.sh $(uname -r)
```
It asks me if I want to remove the old modules and I type r to remove them.  Then I go back to the madwifi directory and type make and get this:

```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/okkiedokki/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/okkiedokki/Desktop/madwifi/ath_hal/uudecode
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c: At top level:
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c: In function 'main':
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/okkiedokki/Desktop/madwifi/ath_hal/uudecode] Error 1
make[2]: *** [/home/okkiedokki/Desktop/madwifi/ath_hal] Error 2
make[1]: *** [_module_/home/okkiedokki/Desktop/madwifi] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

```

What in the world am I doing wrong?

---

### Post by okkiedokki on 2008-09-01
Ok i've figured out what I was doing wrong and got past that step and got the drivers installed.  With no errors, but now when I go do ```
modprobe ath_pci
```, I don't think it's loading the drivers because after I do 
```
 wlanconfig ath0 create wlandev wifi0 wlanmode sta
```
and I get
```
wlanconfig: ioctl: No such device
```

When I type in iwconfig I get:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

And ifconfig gives me this:
```
eth0      Link encap:Ethernet  HWaddr 00:14:2a:e3:29:14  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fee3:2914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4371 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5678509 (5.4 MB)  TX bytes:335301 (327.4 KB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10800 (10.5 KB)  TX bytes:10800 (10.5 KB)

```

I saw another thread where someone had the same problem and after a restart everything worked but that didn't work for me.  If anyone can help I'd appreciate it.

---

### Post by okkiedokki on 2008-09-02
bump.  Bueller?

---

### Post by okkiedokki on 2008-09-04
Come on guys someone's got have some sort of a solution.   Help please?

---

### Post by okkiedokki on 2008-09-08
bump.

---

### Post by wc4f on 2008-11-13
Okkiedokki,
There's a partial explanation to your problems here: [http://auxmem.blogspot.com/2008/11/using-d-link-dwa-542-wifi-card-under.html](http://auxmem.blogspot.com/2008/11/using-d-link-dwa-542-wifi-card-under.html)
Unfortunately, it's not entirely good news unless you you don't mind upgrading to 8.10. Then it's very good news.

---

