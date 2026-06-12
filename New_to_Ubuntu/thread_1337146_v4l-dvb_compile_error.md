---
title: "v4l-dvb compile error"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by tduccuong on 2009-11-25
Hi all,

I have a LogiLink dvb-t stick which works perfectly in Jaunty and Intrepid through v4l-dvb (lsusb gives ID 18b4:1689). However after freshly installed Karmic, I cant compile v4l-dvb anymore. This is what I get from terminal:
```
Kernel build directory is /lib/modules/2.6.31-15-generic/build
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/tduccuong/Tmp/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.o
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list

```

While searching for a solution, I came across this [http://ubuntuforums.org/showthread.php?t=1305228](http://ubuntuforums.org/showthread.php?t=1305228). However I could not find the .config file as the guys suggested...

Does anyone have any idea?

Thank you very much!

---

### Post by Sealbhach on 2009-11-25
It's a hidden file, so maybe in Nautilus select View/Show Hidden Files and you will see it in the v4l folder. Alternatively, hit Ctrl + H.

Apologies if you've already tried this.

.

---

### Post by Zwiebelsaft on 2009-11-26
doublepost

---

### Post by Zwiebelsaft on 2009-11-26
.config file does not exist if you download v4l with hg.
However, it will be generated if you type "make menuconfig" and Exit saving changes.

These steps worked for me:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make menuconfig  <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make install

---

### Post by tduccuong on 2009-11-26
> **Zwiebelsaft said:**
> .config file does not exist if you download v4l with hg.
However, it will be generated if you type "make menuconfig" and Exit saving changes.

These steps worked for me:

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make menuconfig  <-- dont change anything, just "Exit" and save changes
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n
make
sudo make install

Hi,

Thank u for ur reply. I followed ur instructions, but errors are still there. This is the code:
```
tduccuong@ctOfficeLaptop:~/Tmp/v4l-dvb$ make menuconfig
make -C /home/tduccuong/Tmp/v4l-dvb/v4l menuconfig
make[1]: Entering directory `/home/tduccuong/Tmp/v4l-dvb/v4l'
make -C /lib/modules/2.6.31-15-generic/build -f /home/tduccuong/Tmp/v4l-dvb/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.31-15-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
make -f /lib/modules/2.6.31-15-generic/build/scripts/Makefile.build obj=scripts/kconfig hostprogs-y=mconf scripts/kconfig/mconf
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [/lib/modules/2.6.31-15-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/tduccuong/Tmp/v4l-dvb/v4l'
make: *** [menuconfig] Error 2

```

I installed everything related to ncurses but the problem persists! 

What do I do now?

---

### Post by husindo on 2009-11-29
*** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.

ncurses, but also had a look on: aptitude search ncurses-dev
p   libcunit1-ncurses-dev                     - Unit Testing Library for C (ncurses) -- development 
p   libkaya-ncurses-dev                       - Ncurses binding for kaya                            
v   libncurses-dev                            -                                                     
v   ncurses-dev                               -                                                     

?

Try to install ncurses-dev for the beginning (in ubuntu-forum-jargon "sudo aptitude search ncurses-dev"): Maybe that solves, but if not, diggle more with the libraries named on "aptitude search libncurses": Already tried libncurses-dev ?

If you compile something on your own (with configure, make, menuconfig etc.), the problems mostly lies in dependencies between libraries and other files which are not catched up by a package-manager because you just undergo him at that moment you dont use him to install an app on the system (you compile the written code of a programmer, and nobody wrote that wonderful deb/rpm files in which exactly those dependencies are written in)
Hope it helps... if still not, then try to post what related packages you installed, so the guys here can decide if some linkage is broken in your system? And do a "make -d" so you get more debug-info out!

Btw., i found some "v4l-conf"-tool with description "tool to configure video4linux drivers", and "v4l2ucp" with description "Video for Linux 2 Universal Control Panel" in the tree.
Wondering why ubuntu has config-tools in the karmic universe but not v4l itself :D
Come on guys, im shure mythbuntu would be grateful:popcorn:

---

### Post by husindo on 2009-11-29
i managed to get s2api with v4l-dvb (on my Hauppauge - WinTV-NOVA-HD-S2) which does not brake when package-manager does update/upgrade with the following steps:
[B]
apt-get install build-essential
apt-get install mercurial cvs subversion libncurses-dev[/B]
cd /usr/local/src
hg clone [http://mercurial.intuxication.org/hg/s2-liplianin/](http://mercurial.intuxication.org/hg/s2-liplianin/)
cd s2-liplianin
cd linux/include/linux
ln -s /usr/src/linux-headers-`uname -r`/include/linux/compiler.h ./
cd ../../../
make
make install
depmod -a
reboot


Quotation from the thread i got the steps above:
"To skip the procedures of constant patching (and breaking with newer
revisions) I use Igor M. Liplianin's repo. This person has a repo to
make our life easier so that we don't have to constant patch our v4l or
kernel pulls. As a plus, Igor's S2API repo has supported for different
kind of DVB-S2 cards which are not supported in multiproto or in any
other repo! :)"




Source (google-cache due to original site is down atm): [http://209.85.135.132/search?q=cache:McVFhZgRtKwJ:www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681+http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681&cd=1&hl=en&ct=clnk](http://209.85.135.132/search?q=cache:McVFhZgRtKwJ:www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681+http://www.eurocardsharing.com/f273/howto-getting-hvr-4000-nova-hd-cards-working-linux-using-s2api-105681&cd=1&hl=en&ct=clnk)

---

### Post by tduccuong on 2009-12-02
hi guys thank u for ur instructions but unfortunately nothing worked! here is what I get from terminal:

for husindo's instruction:
> **husindo said:**
> 
Try to install ncurses-dev for the beginning (in ubuntu-forum-jargon "sudo aptitude search ncurses-dev"): Maybe that solves, but if not, diggle more with the libraries named on "aptitude search libncurses": Already tried libncurses-dev ?


I get:
```
tduccuong@ctOfficeLaptop:~/Tmp/v4l-dvb$ aptitude search libncurses
v   libncurses-dev                                                  -                                                                          
i   libncurses-gst                                                  - Ncurses bindings for GNU Smalltalk                                       
i   libncurses-ruby                                                 - ruby Extension for the ncurses C library                                 
i A libncurses-ruby1.8                                              - ruby Extension for the ncurses C library                                 
p   libncurses-ruby1.9                                              - ruby Extension for the ncurses C library                                 
i   libncurses5                                                     - shared libraries for terminal handling                                   
p   libncurses5-dbg                                                 - debugging/profiling libraries for ncurses                                
i   libncurses5-dev                                                 - developer's libraries and docs for ncurses                               
i   libncursesw5                                                    - shared libraries for terminal handling (wide character support)          
p   libncursesw5-dbg                                                - debugging/profiling libraries for ncurses                                
i   libncursesw5-dev                                                - developer's libraries for ncursesw                                       
tduccuong@ctOfficeLaptop:~/Tmp/v4l-dvb$ sudo apt-get install libncurses-dev libncurses-gst libncurses-ruby libncurses5-dev libncursesw5 libncursesw5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev instead of libncurses-dev
libncurses5-dev is already the newest version.
libncurses-gst is already the newest version.
libncurses-ruby is already the newest version.
libncurses5-dev is already the newest version.
libncursesw5 is already the newest version.
libncursesw5-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
```

And:
```
tduccuong@ctOfficeLaptop:~/Tmp/v4l-dvb$ make menuconfig
make -C /home/tduccuong/Tmp/v4l-dvb/v4l menuconfig
make[1]: Entering directory `/home/tduccuong/Tmp/v4l-dvb/v4l'
make -C /lib/modules/2.6.31-15-generic/build -f /home/tduccuong/Tmp/v4l-dvb/v4l/Makefile.kernel config-targets=1 mixed-targets=0 dot-config=0 SRCDIR=/lib/modules/2.6.31-15-generic/build v4l-mconf
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
make -f /lib/modules/2.6.31-15-generic/build/scripts/Makefile.build obj=scripts/kconfig hostprogs-y=mconf scripts/kconfig/mconf
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make[1]: *** [/lib/modules/2.6.31-15-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/tduccuong/Tmp/v4l-dvb/v4l'
make: *** [menuconfig] Error 2
```

The other solution via "s2api" does not work either! I get the same error message when try to do the "make" command:
```
Kernel build directory is /lib/modules/2.6.31-15-generic/build
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/tduccuong/Tmp/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.o
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/tduccuong/Tmp/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
```

I guess I have installed all "ncurses-" related stuffs. It kinda drives me crazy now, what is ncurse anyway?

---

### Post by tduccuong on 2009-12-10
Anyone please?

---

### Post by deejc on 2009-12-15
i seem to have fixed this error as i also had it,

instead of running "make menuconfig"
just run "make config"

press the enter key until you reach the point that shows :

```

    * Supported FireWire (IEEE 1394) Adapters
    *
    FireDTV and FloppyDTV (DVB_FIREDTV) [M/n/?] 

```

Press "n"

and then press enter continously until it exits, then run "make"

this stops the error on that card and accepts all the defaults.

---

### Post by lordbah on 2009-12-16
Thanks for that, it allowed me to get the driver compiled. That didn't fix my problem unfortunately, but it still deserves thanks.

My issue is:
libv4l2: error turning on stream: Input/output error

---

### Post by tduccuong on 2009-12-16
It worked! Thank u deejc very much! U saved me :)

btw: If anyone gets some "radio" related error (which I did), just do the "make config" again, and disable the first question about "radio", then follow deejc's solution.

---

### Post by scorptig on 2010-09-27
> **deejc said:**
> i seem to have fixed this error as i also had it,

instead of running "make menuconfig"
just run "make config"

press the enter key until you reach the point that shows :

```

    * Supported FireWire (IEEE 1394) Adapters
    *
    FireDTV and FloppyDTV (DVB_FIREDTV) [M/n/?] 

```

Press "n"

and then press enter continously until it exits, then run "make"

this stops the error on that card and accepts all the defaults.

OK this did help me. Except I still have following error:

```
modprobe cx18
FATAL: Error inserting cx18 (/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/cx18/cx18.ko): Operation not permitted
```

Also I am trying to use tv-viewer

ref []("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1496516")
I have Active TCL installed.

Any help would be welcomed. tv-viewer does not see CX18 Hauppauge HVR-1600.

---

### Post by scorptig on 2010-10-04
I started over the process, I installed fresh copy of Ubuntu 10.04, I copied the firmware for Hauppauge HVR1600. Followed []("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600") instructions. 

Then I followed TV-VIEWER instructions including Activel TCL instructions, as I am using 64 bit version of Ubuntu see[ [URL="http://tv-viewer.sourceforge.net/mediawiki/index.php/]("http://tv-viewer.sourceforge.net/mediawiki/index.php/")Howto#Replacing_included_Tcl.2FTk_packages_with_ActiveTcl"

Now I have Analogue Channels working, quite well. I use Nvidia card, I set my video driver xv adaptor=0 NV17 video texture after attempting other settings, this seems best.

Now TV-VIEWER is great [http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Main_Page") one limitation at this time no Digital TV stations can be viewed.

So If anyone has ATSC Digital on Hauppauge HVR-1600, please let me know what TV viewing software you are using.

Now regarding vl4-dvb, I did install it after installing firmware, and I saw no difference with or without vl4-dvb, however it seems this is required if you want digital end to work. For analogue simply using the firmware CX18 worked fine.

All feedback is welcomed. 

Note I tested 10.10 RC-1, and it seems to detect hardware better, it detected Conexant CX18, my HDMI output on my Video card, promising release.

Thank You :popcorn:

---

### Post by jilindi on 2010-12-07
> **deejc said:**
> i seem to have fixed this error as i also had it,

instead of running "make menuconfig"
just run "make config"

press the enter key until you reach the point that shows :

```

    * Supported FireWire (IEEE 1394) Adapters
    *
    FireDTV and FloppyDTV (DVB_FIREDTV) [M/n/?] 

```

Press "n"

and then press enter continously until it exits, then run "make"

this stops the error on that card and accepts all the defaults.

=============================================
Ya... Thanks so much. Getting the Hauppauge Model HD-PVR 1212 (Bus 001 Device 005: ID 2040:4903 Hauppauge) working in mythTV is quite an adventure. 

Your direction in overcoming the make fatal error for a missing include file was perfect. 

Thanks again.
John L.

---

