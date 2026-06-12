---
title: "How to enable wireless... without wires?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Bogus83 on 2007-03-20
Hi all,

I've recently installed Edgy on my system (Athlon 2400+, GeForce 5200, 1.5GB PC2700,) dual booting with XP.  I've got the Netgear WG111T USB wifi adapter, and I'm trying to get it to work.  The problem is, I only have wireless internet available in my apartment.  I can access the internet fine through XP, and I can transfer files from XP to my Ext3 partition.  But I can't just "plug in" to get the files I need to enable the wireless adapter.

My question is this, what files would I need to download and transfer to my Ubuntu partition to get this working, and where might I find them?  I've got ndiswrapper 1.38 and the Netgear windows drivers on Ubuntu, but I won't be able to apt-get ANYTHING.  So any prerequisites for ndiswrapper, etc, I'll need to download via XP and move over.  Can someone please help me?

Thanks!
-Brian

---

### Post by chili555 on 2007-03-20
Perhaps this will be helpful: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) See item #5.

I gather, from your statement that you have the ndiswrapper-1.38.xxx.tar.gz that you will compile. I, and many others have had an easier time with the Ubuntu packages. YMMV.

Post back if we can help.

---

### Post by Bogus83 on 2007-03-20
Help!  :) 

I'm basically trying to figure out what to do, and that's what I've done so far.  If there's an easier method by all means I'd rather do that.  All I want to do is enable my wireless adapter (WG111T USB "dongle" adapter).  I have the latest drivers for it, and I'm open to suggestions on how to proceed.  The one caveat is that I don't have a jack to plug into for internet access, so anything I need to obtain has to be downloaded in windows and sent over.  (I've already got the transfer part worked out nicely).

---

### Post by chili555 on 2007-03-20
I suggest you go to the link I posted in post#2, scroll down to item #5 and you will see a list of the files you need. Click on the links, beneath Edgy, select 'i386', 'all', etc. until you can see the list of mirrors and click any one of them. Download the three files to any convenient place on your Windows machine.

Put the three files on a CD or USB drive and go back to Ubuntu. Then follow the instructions on the link.

Post back if you need more.

---

### Post by Bogus83 on 2007-03-20
lsusb does not see my adapter.  I'm not sure what to do from here, as that makes it difficult to determine which of the .inf and .sys files I need to use (there are three sets of each).  It's not an issue with the port, as the adapter works in XP and I can use other devices (mouse, keyboard) on that USB port.  Any idea why it wouldn't see it at all?

Edit: Ignore that.  sudo lsusb -v did get it to show, and it's a good thing it did- the device I have is ID 1385:4251, which states on the List page (for ndiswrapper) > Other: Both athfmwdl.inf and netwg11t.inf installed with ndiswrapper version 1.23 or later as there is a bug in previous versions of ndiswrapper (per the changelog). This bug caused me hours of frustration using ndiswrapper v1.22 (Ubuntu Edgy).

So I may use ndiswrapper 1.38 after all- the one currently on my system is 1.22.

If you've got a suggestion for a different version please let me know.

Thanks!

---

### Post by Bogus83 on 2007-03-20
Now I'm really confused.. just for the heck of it I decided to try to use the version I had, and the outcome looked like this:

> bogus@BHCpc:~/Desktop/wifi/wifidrivers/Drivers$ sudo ndiswrapper -i ~/Drivers/athfmwdl.inf
sudo: ndiswrapper: command not found

Kind of odd since I followed the instructions for installing the packages listed in section #5 of the article posted in link #2.  So, I tried installing the three packages again.  The first two looked good, no errors or anything strange in their output.  Installing ndisgtk was different:

> dpkg: ndisgtk: dependency problems, but configuring anyway as you request:
ndisgtk depends on ndiswrapper-utils; however;
Package ndiswrapper-utils is not installed.

Hmm.. that was the second one I installed, as per the instructions.  Now, I know that ndisgtk is the graphical installation program for ndiswrapper, and to be honest I'd rather do it from the command line, so that's not a big deal.  But, it's making me think that even though it LOOKS like I'm installing things, that's not quite the case.  Any thoughts?

---

### Post by Bogus83 on 2007-03-20
I'm really lost now.  I tried to uninstall ndiswrapper 1.22, which seemed to work.  Then in the ndiswrapper-1.38 folder I did sudo make, which freaked out.. it looked like this:

> make -C driver
make[1]: Entering directory `/home/bogus/Desktop/wifi/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/bogus/Desktop/wifi/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: Leaving directory `/home/bogus/Desktop/wifi/ndiswrapper-1.38/driver'
make -C utils
make[1]: Entering directory `/home/bogus/Desktop/wifi/ndiswrapper-1.38/utils'
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
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
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
make[1]: Leaving directory `/home/bogus/Desktop/wifi/ndiswrapper-1.38/utils'
make: *** [all] Error 2


Sorry for all that.  In any case, this is after I've taken my computer to a friend's apartment, plugged it in, and downloaded updates.  According to Synaptic I've successfully installed the ndiswrapper-util and ndisgtk.  But ndiswrapper -v still shows version 1.22, and I can't compile the 1.38 version.

Sheesh.. this isn't going as well as I'd hoped.

---

### Post by Bogus83 on 2007-03-21
Can anyone help me?  I'd be glad to provide more information if necessary.

---

### Post by Everything Is Relative on 2007-03-28
I have installed Ubuntu 6.10 using the alternative method and it installed okay on my Dell Inspiron 1100 Notebook

I would love to use my linksys wusb54GSC to get internet access.

I put the USB compact wireless adapter on the computer but Ubuntu did not pic it up....

I am used to a MS O.S

I am a very new to Linux... and it took me 5 days to get my resolution past 600X400 
(had to flash Bios with a updated version.)

I am not familiar with the syntax of linux as of yet, though I did manage to to a lot of it trying to get my Screen to settle at 1024X768

But this is about as far as I have gone. 

I have down loaded the file ndiswrapper-1.8.tar.gz AND
rt2400-1.2.2.-b3.tar.gz

On to a MS WINDOWS Machine and put them on a thumb drive
As I was told that these drivers were the ones I needed to use my Linksys USB 54G adapter on linksys Ubuntu distro

Now I have placed those files from the thumb drive to my notebooks Ubuntu desktop and 

thats where I am stuck at.... How do I get those drives to install? There are no EXE. extentions that I am used to seeing in MSWIN syntax. 

I have read that you are supposed to make sure that your kernal is the same as something else in another file and use a code (i am assuming in the Applications>Accessories>terminal window) to check. 
I tried that syntax (I think it was sudo appt-get linux-headers-<uname -r> or something to that effect. But when I executed the command it came back as file not found

Next there is a lot of refrences to "Compile to root and extract using 
$tar zxvf ndiswrapper-version.tar.gz

I have no ideas what any of this means and if there is anyone AS TO BE SOOO VERY KIND 

to a very tired NEWB I would be so greatful :popcorn: 

Please someone show me step by step instructions on how to get these drives up 
and going.

I dont know how to compile the folder to the root nor how to get to the root

Am I supposed to be in the terminal or manuver through the windows to the root?

They say unzip the files with a Code command but how do I do that? And where?

Should I use the terminal to get there? :confused: :confused: :confused: :confused: 

Thank you very much!

---

### Post by diepruis on 2007-04-03
> **Bogus83 said:**
> Can anyone help me?  I'd be glad to provide more information if necessary.

Okay, here's what you did wrong: You installed the packages in the wrong order. That doesn't matter, however, since those packages will not help you. You need the up to date ndiswrapper. So go back to the directory where you extracted the source for it, and try to compile it again. This time, though, do it like this:

```

./configure
make
sudo make install

```

That should install it properly.

I'm currently struggling with the same problem under PCLinuxOS. I'll let you know if I figure out anything.

PS: Everything Is Relative: Please post you problem in another thread, it will just get lost here.

---

### Post by diepruis on 2007-04-03
Okay, it seems to be working now, I haven't tested rebooting and such yet, but at least it's a start.

Here's what I did:

[LIST=1]
[*]Downloaded [this driver](ftp://downloads.netgear.com/files/wg111t_1_2.zip).
[*]Extracted the file to /lib/ndis/
[*]Configured ndiswrapper:
```

sudo ndiswrapper -i '/lib/ndis/WG111T_re1.2_rc1/ndis5/athfmwdl.inf'                   
sudo ndiswrapper -i '/lib/ndis/WG111T_re1.2_rc1/ndis5/netwg11t.inf'
sudo ndiswrapper -a 1385:4251 netwg11t
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```
[*]Configured device
```

sudo iwconfig essid MYESSID
sudo iwconfig key MYWEPKEY

```
[*]Here PCLinuxOS automagically brought up the interface, I'm guessing that you'll need to type
```

sudo dhclient wlan0

```
under Ubuntu.
[/LIST]

Hope this helps and please post back with results.

---

