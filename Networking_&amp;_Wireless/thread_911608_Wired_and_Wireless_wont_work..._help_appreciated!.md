---
title: "Wired and Wireless wont work... help appreciated!"
date: 2008-09-05
forum: Networking &amp; Wireless
---

### Post by camputer on 2008-09-05
I just got a new Lenovo ThinkPad SL400 and I installed ubuntu on it. Keep in mind I am a complete newcomer to all Linux.

I can't connect Wired or Wireless. It seems as though there are no drivers for either device installed. 

I was only able to install ndiswrapper off the CD (because I can't connect to the internet at all!)

ndiswrapper l- says:

> 02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

0c:00.0 Ethernet controller: Realtek Semiconductor Co. Ltd. RTL811/81688 PCI Express Gigabit Ethernet Controller (rev 02)

I have tried to download MadWifi and used a USB stick to put it on my ubuntu computer but simply typing make in the madwifi directory prompts a run command... in which nothing happens.

I am a complete novice at this, First attempt at ubuntu and Linux... Help is much needed and appreciated!

---

### Post by camputer on 2008-09-06
Bump... I still haven't figured anything out.

---

### Post by camputer on 2008-09-06
I really need some help :(... I have to get this computer working for monday (start of university). If you need me to do anything I will do it.

I still think MadWifi is likely the way to go with my Atheros wireless card. Only I don't understand the install instructions when it says to type "$ make" in the top-level MadWifi source directory to build all the modules for the currently running system... Where is the top-level directory? When I type: " cam@cam-laptop:~$ '/home/cam/Desktop/madwifi-0.9.4'" in the terminal it brings up the file contents ... there is nowhere to type "$ make". Simply clicking the Makefile and telling it to run does nothing...

I added the below as I have seen other threads where it was asked for.

> ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:22:15:61:d6:9f  

          inet6 addr: fe80::222:15ff:fe61:d69f/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:4294967286 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:219 Base address:0xa000 



eth0:avahi Link encap:Ethernet  HWaddr 00:22:15:61:d6:9f  

          inet addr:169.254.7.227  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          Interrupt:219 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1616 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1616 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:80992 (79.0 KB)  TX bytes:80992 (79.0 KB)


> iwconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by lighthammer on 2008-09-06
What is the name of your wireless network card?

I read what ndiswrapper saw it as but if I were to go to Lenovo.com and pick out your laptop, which wireless card is it?

---

### Post by camputer on 2008-09-06
Thanks for responding Lighthammer. Lenovo calls the card: "ThinkPad 11b/g III Wi-Fi wireless LAN Mini-PCIe"

---

### Post by camputer on 2008-09-06
I now have the wired internet working, still no luck with wireless though.

I figured out how to get into the MadWifi file directory, but when I type $ make, it trys and fails... here is the error message: 

> cam@cam-laptop:~/Desktop/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/cam/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  HOSTCC  /home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/cam/Desktop/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/cam/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/cam/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
cam@cam-laptop:~/Desktop/madwifi-0.9.4$ cam@cam-laptop:~$ cd '/home/cam/Desktop/madwifi-0.9.4' 


Hopefully someone can help... now that I have wired internet, hopefully it will be easier.

---

### Post by camputer on 2008-09-06
No one has any tips or suggestions? Sorry I keep bumping this... but I need some help.:confused:

---

### Post by camputer on 2008-09-07
Well, I am pretty much ready to give up on ubuntu alltogether. I find it hilarious that everyone says that ubuntu has great community support... If it were windows issues I was having, I am sure I would have gotten help far faster somewhere else.

 Maybe its just that I am a newb and no-one wants to help newbs... but its just sad that I can keep this thread going for 2 days without any help.

I am sure this issue would be easy for someone with linux experiance to fix... but I guess its clear that no-one wants to help.

I feel pretty discouraged about this... I'm going back to windows... at least **** works with Windows... and support is easy to get.

---

### Post by hawksbill on 2008-09-07
Try updating your system. Update your repositories under Synaptic and see if there is a newer package for your restricted drivers. 


Have you tried reading MadWifi's HowTo?

You can find it here:
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

This will take you step by step to install the correct drivers.

Also if installing a custom driver from MadWifi is your route, you will need to remove the precompiled restricted drivers from Ubuntu if I'm not mistaken. This isn't hard, but it may throw you a hiccup with display settings if you have an Nvidia graphics card. There may be a work around for this but I just don't remember at the moment + this is another topic.

Be patient for a response. I have never been disappointed with the Ubuntu forums. This isn't a job for most people here and it just takes some time to find what you need.

Hope that helps.

---

### Post by camputer on 2008-09-07
Thanks for the help and response. I will try to follow those instructions and see where I go. I am pretty much stuck with ubuntu now anyway... the system recovery wont work and my windows CD wants me to load hard drive drivers that I can't find... I hope I haven't wrecked a brand new laptop. Thanks again for the response.

---

### Post by camputer on 2008-09-07
I was able to find a windows 2k version of my Atheros driver (from Lenovo) and I extracted the .exe on my dad's laptop. I then copied the extracted folder to a USB stick and dragged the folder onto my Ubuntu desktop. 

then I found the .inf file and pointed ndiswrapper -i to it and it seemed to install correctly. Afterwards a ndiswrapper -l shows:

> cam@cam-laptop:~$ ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)


The only problem is... **I still can't connect wirelessly!** I don't understand what the problem is. :confused:

---

### Post by camputer on 2008-09-07
**PROBLEM RESOLVED!** I now have wireless! all I did was follow the instructions posted here: [http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780") Cool beans... I now have a little more faith in Ubuntu... for now.

I had to get rid of ndiswrapper and install MadWifi following those instructions exactly. Still not very impressed with the lack of help here.

---

