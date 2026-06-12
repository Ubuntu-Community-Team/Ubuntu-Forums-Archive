---
title: "zd1211 based usb wifi card using driver from sf.net"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by ghee22 on 2005-10-15
using 5.04 i was able to use ubuntu's [wiki page on zd1211]("https://wiki.ubuntu.com/zd1211wifi") and have my wireless usb dongle up and running.  

unfortunately, i did a clean format and now the instructions don't work anymore... it won't sudo make anymore.. i think the symbolic links need to be different but i'm not sure... i can't even scroll up to see the errors on it. 

has anyone got this working and please how?

UPDATE: Here are the 2 errors:
make[2]: *** [/home/nilay/zd1211/src/zd1205.o] Error 1
make[1]: *** [_module_/home/nilay/zd1211] Error 2

---

### Post by ghee22 on 2005-10-18
i have made no progress with 5.10 :confused: 

i'm now going to try installing 5.04, using the wiki's solution and trying a apt-get dist-upgrade

will post results asap

---

### Post by REBELinBLUE on 2005-10-18
install gcc-3.6

---

### Post by ghee22 on 2005-10-18
[QUOTE=REBELinBLUE]install gcc-3.6[/QUOTE]

by doing the following?

sudo apt-get install gcc-3.6

---

### Post by blastus on 2005-10-18
> i have made no progress with 5.10 :confused: 

i'm now going to try installing 5.04, using the wiki's solution and trying a apt-get dist-upgrade

will post results asap

I am a newbie to this but from what I understand that won't work. These threads....

[Compiling kernel modules (GCC3.4 / 4.0) problem](http://ubuntuforums.org/showthread.php?t=77851)
[breezy badger - cannot compile Lucent modem drivers](http://ubuntuforums.org/showthread.php?t=77537)

..may shed some light on the issue. To date, I haven't seen a single post yet where someone has sucessfully compiled a kernel module under Breezy.

> install gcc-3.6

gcc-3.6 is not on the Breezy CD.

---

### Post by ghee22 on 2005-10-19
very good links blastus... one user managed a solution:
1. install hoary
2. compile drivers
3. grab *.ko files and put on removable drive
4. format
5. install breezy
6. use *.ko files from removable drive on breezy
7. ...
8. PROFIT! ... ok well,  not really but i'll let you how this goes this weekend

---

### Post by zasten on 2005-10-20
I have a usb wifi adapter based on the zd1211 chipset. I have managed to get it to work but not on startup. Used the updated driver from [http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/)  (version r34)

Installed pretty much as in [https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

Still using Hoary as I'm sure that there will be many many updates to come and  I'm waiting for the unofficial Ubuntu guide to be updated to breezy.

Anyway my problem is that during startup I get the following error repeated seven times and the driver cant find my wep protected wireless router. :mad: 

****** Can't find desiredSSID:

once the desktop is loaded then I have to go into the terminal and do ifdown/ifup wlan0. I wrote a small script to do this and put it into the /etc/rc.boot/ directory so that it would run on startup...

However I can't get rid of the the time consuming error mentioned above that happens during startup..

I have looked at [http://sourceforge.net/mailarchive/message.php?msg_id=12025349](http://sourceforge.net/mailarchive/message.php?msg_id=12025349) but cant make make sense of it too much of a noob

Any ideas??

Would really like to have some pointers here.

Cheers

---

### Post by skmassey on 2005-10-20
Sorry, my internet connection broke up and I posted twice 8(.  My post is just one below this one.

---

### Post by skmassey on 2005-10-20
Following the instructions for the zd1211wifi wiki [here]("https://wiki.ubuntu.com/zd1211wifi"), I get the error on the make portion Error 1 after I issue the "make" command. What is the cause of this error?

---

### Post by ghee22 on 2005-10-21
[QUOTE=skmassey]Following the instructions for the zd1211wifi wiki [here]("https://wiki.ubuntu.com/zd1211wifi"), I get the error on the make portion Error 1 after I issue the "make" command. What is the cause of this error?[/QUOTE]

the cause of this error is a kernel compiled in gcc-3.4 but a distribution including only gcc-4.0.  if you have a cd burner on a seperate computer with an internet connection, try to download gcc-3.4 and burn it.. then in your apt-get .sources list, include the cdrom and apt-get install gcc-3.4.  then try the make command.  

i'm not expert so take these instructions with a giant 5 pound bag of salt :smile:

---

### Post by ghee22 on 2005-10-31
^^BUMP^^&

It works! I installed 5.04, installed the ZD1211 using the ubuntu wiki. i then added this command:
Code:

alias wlan0 zd1211

in /etc/modules
so that i modprobe would survive a reboot

internet works on 5.04, so i downloaded and burned a copy of 5.10. put the cd in and used the upgrade all packages option. incurred some package errors but it was all good because after a reboot (don't forget to remove the 5.10 cd) , i still had my wireless usb card working!!!

tell me how this works out for y'all.

---

### Post by dom on 2005-10-31
i just got this device working

[http://ubuntuforums.org/showthread.php?p=458488](http://ubuntuforums.org/showthread.php?p=458488)

i got also the error 
****** Can't find desiredSSID:

and it slowed the boot up while it was looking


i haven't tried adding the alias to /etc/modules yet.


has anybody else here being using WPA ?  [ i just built wpa_supplicant ]

I'm looking for tips/info on getting this device activated and setup properly on boot, or even at the end of the boot, if i could call a script to be run in the background......

thanks

dom

---

### Post by rosales on 2005-11-11
I got it! Got my USB ZD1211 WiFi dongle to work on Ubuntu Breezy, guys!

First: I got the last ZyDas ZD1211 linux driver from sourceforge (august 2005).
Second: I made the following symlinks:
     ln -s /usr/src/linux-headers-2.6.12-9-386 /usr/src/linux
     ln -s /lib/modules/2.6.12-9-386/ /lib/modules/2.6.12
Third: moved to /tmp and decompressed the driver here (builds /tmp/zd1211 directory)
Fourth: cd /tmp/zd1211 && make && make install

I didn't use other gcc version than default (4.0).
Once it was installed (depmod-ed of course), I raised wlan0, but in order to function I had to tune iwconfig settings (essid and key, I use wep). In addition, once I rebooted the machine, I needed to get on my user session, open a terminal, and issue again the same iwconfig settings (I don't know how to make these changes persistent)

Greetings from southern Spain,

---

### Post by jounihat on 2005-11-12
So, is there any way I could install the driver without re-installing 5.04 and upgrading to 5.10? I've just configured all my systems to run perfectly, and I'd rather not mess up with them right now. I've got an Internet connection via ethernet, so I can install GCC 3.4 too, but make install gives me this error:

"gcc -o apdbg apdbg.c
apdbg.c:1:19: error: stdio.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:2:20: error: stdlib.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:3:20: error: unistd.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:4:20: error: string.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:5:19: error: errno.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:6:19: error: ctype.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:7:23: error: sys/types.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:8:24: error: sys/socket.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:9:23: error: sys/ioctl.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:10:20: error: net/if.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:11:24: error: netinet/in.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:13:27: error: linux/sockios.h: Tiedostoa tai hakemistoa ei ole
apdbg.c:75: warning: &#8216;struct ifreq&#8217; declared inside parameter list
apdbg.c:75: warning: its scope is only this definition or declaration, which is probably not what you want
apdbg.c: In function &#8216;set_ioctl&#8217;:
apdbg.c:77: error: &#8216;SIOCDEVPRIVATE&#8217; undeclared (first use in this function)
apdbg.c:77: error: (Each undeclared identifier is reported only once
apdbg.c:77: error: for each function it appears in.)
apdbg.c:79: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
apdbg.c:79: error: &#8216;stderr&#8217; undeclared (first use in this function)
apdbg.c:80: error: &#8216;errno&#8217; undeclared (first use in this function)
apdbg.c: At top level:
apdbg.c:88: warning: &#8216;struct ifreq&#8217; declared inside parameter list
apdbg.c: In function &#8216;read_reg&#8217;:
apdbg.c:92: warning: passing argument 2 of &#8216;set_ioctl&#8217; from incompatible pointer type
apdbg.c: At top level:
apdbg.c:102: warning: &#8216;struct ifreq&#8217; declared inside parameter list
apdbg.c: In function &#8216;read_mem&#8217;:
apdbg.c:107: warning: passing argument 2 of &#8216;set_ioctl&#8217; from incompatible pointer type
apdbg.c: In function &#8216;main&#8217;:
apdbg.c:129: error: storage size of &#8216;req&#8217; isn&#8217;t known
apdbg.c:130: error: &#8216;NULL&#8217; undeclared (first use in this function)
apdbg.c:137: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
apdbg.c:137: error: &#8216;stderr&#8217; undeclared (first use in this function)
apdbg.c:142: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
apdbg.c:145: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
apdbg.c:150: error: &#8216;AF_INET&#8217; undeclared (first use in this function)
apdbg.c:150: error: &#8216;SOCK_RAW&#8217; undeclared (first use in this function)
apdbg.c:150: error: &#8216;IPPROTO_RAW&#8217; undeclared (first use in this function)
apdbg.c:152: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
apdbg.c:152: error: &#8216;errno&#8217; undeclared (first use in this function)
apdbg.c:153: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
apdbg.c:156: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
apdbg.c:231: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
apdbg.c:232: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
apdbg.c:250: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make: *** [install] Error 1"

Any ideas? Any hope to get it to work without removing my current system? Thanks in advance!

Edit: "Tiedostoa tai hakemistoa ei ole." = "No such file or directory."

---

### Post by vnlinux on 2007-03-24
Im using Ubuntu 6.06. I downloaded zd1211b-r85 driver and successfully build & install. When restart, I got the same error: "can't find desiredSSID". 
Only after I type the command: **sudo modprobe -r zd1211b** that it stops printing that message. But it happens again during next restart. How to eliminate zd1211b module out of Linux kernel? Or I have to add the above command automatically run???
Anyway, I still cannot make the wlan working by following all instructions. So tired of installing driver in Linux ^^

---

