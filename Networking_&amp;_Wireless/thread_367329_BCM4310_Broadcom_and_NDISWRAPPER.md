---
title: "BCM4310 Broadcom and NDISWRAPPER"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Valehru on 2007-02-22
For those of you who want to get the broadcom 4310 wireless card working under edgy on the Compaq V3000 I created a how to on my blog.  
[URL="http://www.valehru.com/blog/?p=181"]
 http://www.valehru.com/blog/?p=181[/URL]

Hope that this helps you to get it working.

---

### Post by Kuraboy on 2007-03-04
site not found...

---

### Post by Valehru on 2007-03-04
"Site not found"

Apologies, please follow this link.  I adjusted the permalink structure of my website last week.  I didn't realize that it gave a 404.  Thanks.

[http://www.valehru.com/blog/?p=181]("http://www.valehru.com/blog/?p=181")

---

### Post by the buddha on 2007-03-07
Thank you for the howto. I had been totally frustrated for lack of wi-fi on my ultra-portable (sic)
Yeah it had left me tied to a LAN cable, so much for its portabiity :p

By the way , you can add to the list of h/w tested for your howto, my Compaq Presario BT1914.
I had not to change one bit or stray away from your instructions. The only hiccup was clearing the earlier installation of ndiswrapper, but its easy if you know your linux well. Also in conjuction to your howto , the following link was of particular help , since specifically because I was getting an error on 
 *# ndiswrapper -a 14e4:4312 bcmwl5* 
mentioned with a solution in the following thread:
[http://www.sabayonlinux.org/forum/viewtopic.php?t=4112&highlight=]("http://www.sabayonlinux.org/forum/viewtopic.php?t=4112&highlight=")

I guess you could add the information from that thread for this error condition to your howto in order to make it more comprehensive.

Now if somebody else like you could just get the sound working ....it would really clear the only 2 problems there are with the B1914 model (wireless and sound) and make it equivalent to my earlier linux-pal "thinkpad" ie complete for linux  !

Once again , thanks for your effort!

---

### Post by Valehru on 2007-03-07
> **the buddha said:**
> 
Now if somebody else like you could just get the sound working ....it would really clear the only 2 problems there are with the B1914 model (wireless and sound) and make it equivalent to my earlier linux-pal "thinkpad" ie complete for linux  !

Once again , thanks for your effort!

My pleasure.  Glad that I could help.  What seems to be the problem with your sound?  I know that I had a problem where the default installation of edgy did not detect my headphones however I resolved that with an alsa patch. If that's the same problem I can write a how-to for that over the next few days if you like.

---

### Post by the buddha on 2007-03-07
Well just like the wireless agony, suond has been amply posted and discussed. Its a break from the current topic but we need not start a fresh thread. I am posting links for your reference.

[http://ubuntuforums.org/archive/index.php/t-269532.html](http://ubuntuforums.org/archive/index.php/t-269532.html)

[http://www.spinics.net/lists/alsa-devel/msg04565.html](http://www.spinics.net/lists/alsa-devel/msg04565.html)

[http://www.spinics.net/lists/alsa-devel/msg04591.html](http://www.spinics.net/lists/alsa-devel/msg04591.html)

And of course since this problem is more h/w specific the distro doesn't seem to matter (or rather it won't). Here's a link :
[http://forum.club.mandriva.com/viewtopic.php?t=57060&sid=e3b6ab9a17bf70f61a119b8bd17d5bcf](http://forum.club.mandriva.com/viewtopic.php?t=57060&sid=e3b6ab9a17bf70f61a119b8bd17d5bcf)

Hope this helps towards your understanding.

---

### Post by Alfdog on 2007-04-03
I'm using feisty 7.04 beta kernel updated to 2.6.20-13.  The Ndiswrapper version from your site wouldn't install, so I used the newer version from the package manager.  I followed your instructions, when I got to the part to run

sudo ndiswrapper -a 14E4:4312 bcmwl5

I got the error:

couldn't create symlink for "14E4:4328.5.conf": File exists -
installation may be incomplete

driver 'bcmwl5' is not installed (properly)!

Anyways, I finished the steps in the guide, and it works

EDIT:

Bah, after a reboot it's not working  >.<  I think I might just wait to 7.04 is final.

---

### Post by Alfdog on 2007-04-19
Has  anyone gotten the 4310 card working on feisty yet?

---

### Post by Valehru on 2007-04-20
Working perfectly here....

---

### Post by Alfdog on 2007-04-20
did you update your install? or did you do a clean install?

---

### Post by Valehru on 2007-04-20
It was on a clean install of Feisty.  Ndiswrapper has not changed in any way.  

compile ndiswrapper
install the driver
disable bcm43xx
modprobe ndiswrapper
set up the interfaces file

and thats pretty much it

---

### Post by fusionisthefuture on 2007-04-21
valehru, i have a question for you.  im also running feisty, and before that i was running edgy, and at one point i got my wireless to work with fwcutter, but it was very dissapointing.  the speed was terrible, i got maybe 25K/s, and it was all spikey, even then.  so my question is, is this what happens to you when you run it with ndiswrapper?  also if not, will your howto work for feisty?  thanks alot.
-arne

---

### Post by Valehru on 2007-04-21
Ndiswrapper allows full duplex speed.  Currently it is at 54Mbps.  

Twice as fast as fwcutter and yes it works on feisty!

---

### Post by fusionisthefuture on 2007-04-21
i think im having a problem installing ndiswrapper.  i downloaded the source from that link on your page, and when i sudo make install it gives me this:

sudo make install
make -C driver install
make[1]: Entering directory `/home/user/Desktop/ndiswrapper-1.37/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/user/Desktop/ndiswrapper-1.37/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
/sbin/depmod -a 2.6.20-15-generic -b /
make[1]: Leaving directory `/home/user/Desktop/ndiswrapper-1.37/driver'
make -C utils install
make[1]: Entering directory `/home/user/Desktop/ndiswrapper-1.37/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:179: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:179: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:183: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:195: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:206: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:218: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:218: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:222: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:223: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:225: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:233: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:233: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:233: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:250: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:250: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:252: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:256: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:258: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:260: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:262: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:268: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:268: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:272: warning: implicit declaration of function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:281: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:281: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:283: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:285: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘stat’
loadndisdriver.c:288: error: dereferencing pointer to incomplete type
loadndisdriver.c:289: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:295: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:295: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:300: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:304: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:314: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:319: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:322: error: dereferencing pointer to incomplete type
loadndisdriver.c:283: warning: unused variable ‘statbuf’
loadndisdriver.c:345: error: expected expression before ‘struct’
loadndisdriver.c:347: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:349: warning: implicit declaration of function ‘free’
loadndisdriver.c:356: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:356: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:358: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:368: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:371: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:371: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:375: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:377: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:377: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:408: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:368: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:420: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:420: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:424: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:425: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:427: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:428: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:430: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:435: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:437: error: dereferencing pointer to incomplete type
loadndisdriver.c:440: error: dereferencing pointer to incomplete type
loadndisdriver.c:449: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:466: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:466: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:474: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:474: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:475: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:475: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:485: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:490: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:491: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:491: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:491: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:492: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:497: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:513: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:513: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:515: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:517: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:519: warning: implicit declaration of function ‘printf’
loadndisdriver.c:519: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:529: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:544: warning: implicit declaration of function ‘atof’
loadndisdriver.c:551: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:558: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:592: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/user/Desktop/ndiswrapper-1.37/utils'
make: *** [install] Error 2

in case this is how its supposed to look, i tried to go on, and use the command : sudo ndiswrapper -i bcmwl5.inf   from directory SPwhatever, and it says that ndiswrapper: command not found dealy.  so im thinking there was a problem with installing ndiswrapper.  how do i uninstall everything?  
thanks
-arne

---

### Post by Valehru on 2007-04-21
Did you go 
sudo apt-get install build-essential

then 

cd /home/user/Desktop/ndiswrapper-1.37/

then 
sudo make install

---

### Post by fusionisthefuture on 2007-04-21
k well i got past that and got ndiswrapper installed but now when i run ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

i get taht, which is supposed to be right, and then if i do 

sudo ndiswrapper -a 14E4:4312 bcmwl5
couldn't create symlink for "14E4:4311:1363:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1364:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1365:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1374:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1375:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1376:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311:1377:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4311.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:135F:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1360:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1361:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1362:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1370:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1371:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1372:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312:1373:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4312.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318:1355:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318:1356:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318:1357:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319:1358:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319:1359:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319:135A:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4319.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:00E7:0E11.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F4:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:12F8:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FA:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320:12FB:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:12F9:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324:12FC:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4324.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328:1366:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328:1367:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328:1368:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328:1369:103C.5.conf": File exists -
installation may be incomplete
couldn't create symlink for "14E4:4328.5.conf": File exists -
installation may be incomplete
driver 'bcmwl5' is not installed (properly)!


i get that, which cant be right.  
any ideas?
thanks
-arne

---

### Post by fusionisthefuture on 2007-04-21
kkk sorry again, ignore that last part...  

i got it up to the point where you modprobe ndiswrapper, and it seems to be trying to work.  up at the little network manager applet dealy, if i click on it it shows the ssid of my network, and the signal bar is about 3/4 full, and i can get returns on both iwlist scan and iwconfig.  but when i try to sudo ifup eth1 i get : ignoring uknown interface eth1=eth1, and it just wont connect to the network.  it will just sit there and spin until it time out and says it cant connect.  if i do dmesg | grem eth i get a bunch of messages saying basically:  eth1, link is not ready, eth1, link becomes ready, eth1, no IPv6 routers present, then it just keeps outputting that, over and over, that theres no IPv6 routers.  

what does this mean?
thanks alot
-arne

---

### Post by Valehru on 2007-04-22
Have you set up the interfaces file?  

I would recommend that perhaps if you are not on an IPV6 network then you should disable IPV6 altogether.  

try the following commands

sudo ifdown eth1
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifdown eth1
sudo /etc/init.d/networking restart
sudo ifup eth1

Check the output of dmesg and paste it here.  Thx...

---

### Post by fusionisthefuture on 2007-04-22
most networks are ipv4 and ipv6 is that new thing that not many people use yet, right?  if thats the case, how do i go about disabling ipv6 and telling it to use ipv4 instead?
thanks
-arne

---

### Post by Valehru on 2007-04-22
I've seen lots of posts about problems with IPv6 (slow network/Internet connections, DNS resolution problems, etc.). I've also seen several posts presenting solutions to these issues. Herewith, what I had to do to disable IPv6 and get reasonable connection & DNS speeds.

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off ipv6
4. Save the file and reboot

Please note that many of the suggestions I've seen recommend running the command sudo update-modules before rebooting; whenever I've done this, I still see IPv6 active (i.e., the sit0 section when running ifconfig -a) and still experience the network performance problems.

Finally, with Mozilla browsers (Firefox or Suite), you can enter about:config in the address bar, locate the line starting with network.dns.disableIPv6 and change the value to true. (I'm not sure if this is necessary; I do know that, by itself, it doesn't solve the problem. But, hey - it can't hurt!)

---

### Post by fusionisthefuture on 2007-04-22
dmesg | grep eth
[   16.940957] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.59.
[   17.058864] forcedeth: using HIGHDMA
[   17.579013] eth0: forcedeth.c: subsystem: 0103c:30b5 bound to 0000:00:14.0
[   92.595693] wlan0: ethernet device 00:1a:73:18:cc:81 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4312.5.conf
[   92.599330] ndiswrapper: changing interface name from 'wlan0' to 'eth1'

ive just disabled ipv6, in that file that you told me to use, but not in mozilla yet, i figured that doesnt have much to do with actually connecting to the network, and i couldnt find the line that you told me to find.  but anyways, it still wont connect, i tried the sudo ifdown eth1 thing, and every  time i do that command, i get:  

ifdown: interface eth1 not configured

it even says that after ive modprobed ndiswrapper, but if i continue with those commands and restart the networking, which reads: 

 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5066
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d3:90:df:cd
Sending on   LPF/eth0/00:16:d3:90:df:cd
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d3:90:df:cd
Sending on   LPF/eth0/00:16:d3:90:df:cd
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.52 -- renewal in 2147483648 seconds.
                                                                         [ OK ]

(when im connected thru wired network)

and then when i sudo ifup eth1 it says :  Ignoring unknown interface eth1=eth1.

---

### Post by Valehru on 2007-04-22
Can you post your /etc/network/interfaces  file please.

For your wifi network I personally think that you would be better off having a static address.  It takes too long to get a DHCP assigned address.  Also, perhaps your are connected to the network, could you try pinging the router.  Also place the network applet into the status bar.  You should be able to see if its connected or not. 

If you can ping the router but are still not able to go online this means that your DNS settings are out of wack.  Edit the /etc/resolv.conf file appropriately.  

I'd advise you to ask online in the IRC #ubuntu forum as well.  There are alot of people there who could also help.  
Thx.

---

### Post by fusionisthefuture on 2007-04-22
well first of all, thank you so much for your patience and help, it is currently working (sort of).  it turns out i am actually connected to the network, even though the network manager up by the clock doesnt say so.  it says im not connected, and if i try to connect using it, it doesnt work, but in reality, i am connected, and ive got internet and all that.  i turned on the other network connection applet that shows which connection your currently using, and that one shows that im using eth1, and that its connected, but what i wanna know now is this.  on this router, its set to static ip on the router, which i think might be messing it up, if i have it set to roaming and dhcp here in the computer.  but on other networks, say the one at my school, do you think it will allow me to connect normally, and actually think im connected?  
-arne
p.s. i think what fixed it was me finally adding that stuff to my network/interfaces file, i had forgotten to do so until just now.  what exactly does that file do?  thanks again

---

### Post by Valehru on 2007-04-22
What you could do is set up your network interface files as follows, change the encryption key and Network name. 

Home network  - Standard wep encryption - static IP
/etc/network/interfaces:
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface eth1 inet static
wireless-essid HOME
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:THIS_IS_MY_WEP_KEY
auto eth1

```

Say at school which has a network called school and no encryption and a dhcp server
/etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
wireless-essid SCHOOL
auto eth1

```

if you change the interface file in anyway remember to do the following commands
sudo ifdown eth1
sudo /etc/init.d/networking/restart
sudo ifup eth1

You may have to manually set the DNS server from time to time with a static IP.  Point it to the address of your router on the WAN 
sudo gedit  /etc/resolv.conf 
nameserver 192.168.0.1

Hope that helps you out.  Any problems let me know.  Now you may have to repeat all of these steps each time you get a kernel upgrade or update ok!  Best of luck and welcome to wifi on linux.

---

### Post by fusionisthefuture on 2007-04-22
new problem ><.

when i edited /etc/modules and added ndiswrapper, and then rebooted, it didnt work, and every time i try to rmmod ndiswrapper, it completely locks my computer, cant mouse or anything, cant even get to a CLI with ctrl+alt+f1.  but if i remove ndiswrapper from the modules file, and do it manually after boot every time, it seems to work just dandy?
-arne

---

### Post by Valehru on 2007-04-22
hmm...sounds weird.  

If you don't want to add it there what you could do is modprobe ndiswrapper when you enter the gnome desktop.  

System > Preferences > Sessions

Add a new startup program

sudo modprobe ndiswrapper

Its irregular but it should work.  Lemme know how it goes.

---

### Post by fusionisthefuture on 2007-04-22
well, that didnt work either, if i do it that way, it just doest do anything, and i still have to do it manually, but then it starts up

---

### Post by fusionisthefuture on 2007-04-22
kkk i did a complete reinstall, and its pretty much doing the same thing, except it does actually modprobe ndiswrapper when it boots up after i added it to that file.  - but - it doesnt actually connect.  i have to do ifdown ifup and then it will connect again.  do you think this is a problem with my network/interfaces file?  ive just got it on dhcp right now, and it really doenst take long at all to connect that way when i use sudo ifup eth1, becuase my router is doing the static ips for all the computers in my house.  also, is there any way to make that network-manager-gnome thing make it recognize that im acutally connected to the network?
thanks
-arne
p.s. ill vote now, its a yes

---

### Post by fusionisthefuture on 2007-04-22
valehru, i was just trying to stream HDTV over my wireless network via myth, and i noticed that the max transfer rate i could get was 1.3 mb/s.  do you have this same problem?  have you actually achieved full duplex 20-so mb/s?  
thanks
-arne

---

### Post by Alfdog on 2007-04-24
I don't mean to try to hijack this thread, but I got my 4310 card working using the instructions in this thread [http://ubuntuforums.org/showthread.php?t=417731](http://ubuntuforums.org/showthread.php?t=417731)  He uses a different driver, but basically the same type of deal.  I don't know if it matters that I'm not using a Compaq, I'm using a Dell 1490 wireless card that uses that same chipset.

---

### Post by fusionisthefuture on 2007-07-01
i finally figured out why this method would only occasionally work for me, and thats beause the network manager was screwing things up.  once i uninstalled that, and manually configured the connections, it worked fine, every time.  i got the idea from getting wireless to work on my desktop, with a wusb54g v4, and it was doing the same thing, but with the normal drivers for that card, not ndiswrapper.  

-arne

also i made a mistake saying it doesnt allow full bandwidth, it does, its just that ubuntu uses megabytes while windows uses bits, and so the numbers are quite different.  it works perfect.  thanks alot.

---

