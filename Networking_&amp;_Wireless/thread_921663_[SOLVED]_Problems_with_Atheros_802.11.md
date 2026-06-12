---
title: "[SOLVED] Problems with Atheros 802.11"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by putnam120 on 2008-09-16
I am using a HP Pavilion dv6700 (64-bit with an AMD processor) and have just installed Ubuntu. However, my wireless card is not working and I am not able to get a wired connection to the internet to download anything (I am currently using another computer). Is there anyway to get my wireless card working?

---

### Post by caligula08 on 2008-09-16
which drivers are u using?  i recommend madwifi-hal-0.10.5.6-r3835-20080801.tar.gz.   have been using those for many moons
now on Atheros.

---

### Post by putnam120 on 2008-09-16
Alright, but how do I go about installing it?

---

### Post by putnam120 on 2008-09-16
Ok if found some instructions on how to install it but ran into a few problems. 

After I enter ```
sudo make
``` get the following

```
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: At top level:
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c: In function 'main':
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode] Error 1
make[2]: *** [/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal] Error 2
make[1]: *** [_module_/home/nick/Desktop/madwifi-hal-0.10.5.6-r3835-20080801] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2

```

Am I doing something wrong or am I missing some other program?

---

### Post by moore.bryan on 2008-09-16
you could try hard-connecting via ethernet and then installing linux-restricted-modules-common should fix you up with the madwifi modules.
```
sudo aptitude install linux-restricted-modules-common
```

---

### Post by putnam120 on 2008-09-16
I would love to try that the only problem is that I am not able to connect via ethernet (stupid way the school has it set up only Mac and Windows machines can connect that way). So I have to download all my stuff on this computer (running windows) and then transfer it over to the one with Ubuntu.

---

### Post by moore.bryan on 2008-09-16
fair enough. is it proxied? there are ways around that... ;-)

you can also download the package from the packages site [here]("http://packages.ubuntu.com/").

---

### Post by Sayers on 2008-09-16
That's funny, the one thing that isn't a security threat is blocked...

---

### Post by putnam120 on 2008-09-16
moore.bryan: what exactly am i supposed to download from that link? and then how do I install it once I do?

---

### Post by n00rt on 2008-09-16
i couldn't get the madwifi working with my atheros card - ar5bxb63 or something similar - although i think it is supported - so i use teh ndiswrapper thing with a windows driver that i downloaded - easiest way is to install the ndiswrapper (Windows Wireless Drivers)from add remove applications and then download teh drivers you need - google them then add them with system > administration > windows wireless drivers - also you may want to disable the atheros support in system > admin > hardware drivers - uncheck the hal and support for atheros - apparently hardy detects this card wrongly and uses the wrong drivers?

edit - tho that's not much use if you cant get on the internet in the first place - there is a thread in this forum about intstalling ndiswrapper without a connection - maybe that will help?

---

### Post by moore.bryan on 2008-09-16
when you get to the home page, scroll-down and there's a search box. if you're running hardy, that's the default; if not, select the proper version and in the search box type "linux-restricted-modules-common." when you get the homepage of that package, scroll-down and you should see a link to the different architectures... click the appropriate one (usually "all") and then one of the mirror sites. open a terminal and go to where you saved the *.deb file. then install using ```
sudo dpkg -i *.deb
``` with "*.deb" being whatever the name of the file is.

i know that's a lot of stuff... if you run into any issues, just post.

---

### Post by putnam120 on 2008-09-17
Alright i did that and everything seemed to go alright, what do I do now?

---

### Post by moore.bryan on 2008-09-18
now, reboot and your wireless should use the madwifi stuff included in the package you just installed. try-out network-manager's connection possibilities now.

---

### Post by putnam120 on 2008-09-18
where is "network-manager's connection possibilities"?

---

### Post by moore.bryan on 2008-09-18
click (maybe double-click) the network-manager icon in the system tray/top panel and there should be your options.

---

### Post by putnam120 on 2008-09-18
I did that and nothing different is there.

---

### Post by moore.bryan on 2008-09-19
hmm... let me dig a little.

---

### Post by moore.bryan on 2008-09-19
okay... according to what i've found, although it may be an atheros chipset in your lappie, most have an intel pro/wireless 3945abg network adapter. now, that may not mean anything to you, but it means you can try and use the intel-supplied driver for that adapter:
[http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2259&DwnldID=10315&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2259&DwnldID=10315&lang=eng)

---

### Post by putnam120 on 2008-09-20
That seems to be for computers with intel chips and I am using AMD.

---

### Post by moore.bryan on 2008-09-21
righto... missed that one. funny, the hp website for your lappie doesn't even show that as an option. you've stumped me thus far. have you asked around the madwifi forums and/or tried to compile from scratch?

---

### Post by putnam120 on 2008-09-21
Thanks for all your help moore.bryan.
I was able to finally able to get my wireless card to work by following this post [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780) and also having to use my friend's router to get a direct connection.

---

### Post by moore.bryan on 2008-09-21
no worries... i'm just glad to hear you finally got it working. best of luck and happy ubuntu-ing.

ps... you probably should mark the thread as "solved" under the "thread tools" link at the top of the page.

---

### Post by vonbrune on 2009-03-01
Btw... If you had the CD then you could navigate to pool/main/l folder and there would be linux-backports-modules-(something) and install that.

---

