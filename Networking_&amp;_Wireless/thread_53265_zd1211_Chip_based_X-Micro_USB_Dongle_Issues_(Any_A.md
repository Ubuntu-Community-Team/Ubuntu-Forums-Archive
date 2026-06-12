---
title: "zd1211 Chip based X-Micro USB Dongle Issues (Any Advice?)"
date: 2005-07-30
forum: Networking &amp; Wireless
---

### Post by kr3mliyn on 2005-07-30
This is my first thread here on Ubuntu Forums... so be nice!

I wasn't exactly sure where this should go, so please feel free to correct/redirect me for assistance.

I have an 
iBook G4, 800Mhz PowerPC, 640MB, 30GB
Advent 7017, 3Ghz Pentium 4, 512MB, 40GB

and I have this one problem with them both... I cannot configure my [X-Micro WLAN 11b USB Adaptor]("http://www.x-micro.com/wlan-usb.htm/") and have successfully (well, it seems okay) compiled the modules using the following resources: -

[http://www.ubuntuforums.org/showthread.php?t=36827&highlight=zd1211]("http://www.ubuntuforums.org/showthread.php?t=36827&highlight=zd1211")

Heres an excerpt...

 > 
2. extract the .tar.gz file to ~/ (tar zxvf sf_zd1211_20050315_src.tar.gz)
3. cd ~/zd1211
4. sudo ln -s /lib/modules/$(uname -r) /lib/modules/2.6.10
5. make KSRC=/usr/src/linux-headers-$(uname -r)
6. sudo make KSRC=/usr/src/linux-headers-$(uname -r) install


This worked PERFECTLY for me, with the mofied drivers available from [http://warder.ath.cx:81/projects.php#zd1211]("http://warder.ath.cx:81/projects.php#zd1211") and the zd1211 site.

But, no matter what I do (within my limited scope of knowledge) I get nothing! :?

ifconfig returns nothing, iwconfig says their aren't any wireless extensions, though lsmod returns: -

 ```

root@myBook:~# lsmod
Module				  Size  Used by
zd1211				253540  0

``` 

Whilst modprobe leaves me in the dark: -

```

root@myBook:~#  modprobe -v zd1211
root@myBook:~#

```
](*,)

I've insmod zd1211 within the zd1211 install directory in my home folder to confirm it's loaded, and what-do-you-know: -

root@myBook:~/zd1211# insmod zd1211.ko
insmod: error inserting 'zd1211.ko': -1 File exists

The exact same problems are occuring on my x86, which seems to have the drivers installed successfully (Note: - I have a Runtop WA1220 PCMCIA (Atmel?) running successfully under ndiswrapper, just looks like my iBook doesn't het to join in on the wireless fun, shame).

Any advice, tips, pointers, resolves would be helpful; ask me what information you need me to include, I'd be more than greatful, peace!

P.S. Ubuntu Hoary with a 2.6.10 kernel.

---

### Post by kr3mliyn on 2005-07-30
Ubuntu Hoary with a 2.6.10 kernel.

---

### Post by brousch on 2005-08-01
Have you done?

[FONT=Courier New]sudo ifconfig wlan0 up[/FONT]

After that you should be able to continue the configuration through the usual System/Admin/Networking

---

### Post by kr3mliyn on 2005-08-01
```
kr3mliyn@a7017:~$ sudo ifconfig wlan0 up
Password:
wlan0: ERROR while getting interface flags: No such device
kr3mliyn@a7017:~$
``` 
...bump!
Thanks for the hint though... any other sugesstions? :|

---

### Post by brousch on 2005-08-01
I just finished a Wiki on how I installed my zd1211. You might try running through it to see what you get.

[https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

---

### Post by kr3mliyn on 2005-08-01
Thanks brousch, I'll check it out! Wish me luck.

P.S. Just downloaded a Breezy ISO for my iBook (typing from my Advent x86), gonna attempt to make zd1211 work with it).

---

### Post by kr3mliyn on 2005-08-01
(u_u;) Why won't Ubuntu just play nice? Your FAQs helpful...

 ```

kr3mliyn@a7017:~$ sudo apt-get install gcc
Password:
Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kr3mliyn@a7017:~$ sudo apt-get install linux-headers-2.6.10-5-386
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.10-5-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kr3mliyn@a7017:~$ sudo ln -s /usr/src/linux-headers-2.6.10-5-386 /usr/src/linux kr3mliyn@a7017:~$ sudo ln -s /lib/modules/2.6.10-5-386 /lib/modules/2.6.10
kr3mliyn@a7017:~$ sudo ln -s /lib/modules/2.6.10/build /usr/src/linux/build
kr3mliyn@a7017:~$ wget http://prdownloads.sourceforge.net/zd1211/sf_zd1211_20050315_src.tar.gz?download
--07:12:51--  http://prdownloads.sourceforge.net/zd1211/sf_zd1211_20050315_src.tar.gz?download
		   => `sf_zd1211_20050315_src.tar.gz?download'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net[66.35.250.217]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

	[  <=>							    ] 20,007		71.56K/s

07:12:51 (71.53 KB/s) - `sf_zd1211_20050315_src.tar.gz?download' saved [20,007]

kr3mliyn@a7017:~$ tar -xvzf sf_zd1211_200050315_src.tar.gz
tar: sf_zd1211_200050315_src.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kr3mliyn@a7017:~$ tar -xvzf sf_zd1211_20050315_src.tar.gz
zd1211/
zd1211/.cdtproject
zd1211/.project
zd1211/CHANGES
zd1211/LICENSE
zd1211/Makefile
zd1211/README
zd1211/src/
zd1211/src/zdconfig
zd1211/src/zd1205.c
zd1211/src/zd1205_proc.c
zd1211/src/zd1211.c
zd1211/src/zdasocsvc.c
zd1211/src/zdauthreq.c
zd1211/src/zdauthrsp.c
zd1211/src/zdbuf.c
zd1211/src/zddebug.c
zd1211/src/zdencrypt.c
zd1211/src/zdglobal.c
zd1211/src/zdhci.c
zd1211/src/zdhw.c
zd1211/src/zdmic.c
zd1211/src/zdmmrx.c
zd1211/src/zdpmfilter.c
zd1211/src/zdpsmon.c
zd1211/src/zdshared.c
zd1211/src/zdsynch.c
zd1211/src/zdtkipseed.c
zd1211/src/zdusb.c
zd1211/src/WS11UPh.h
zd1211/src/WS11UPhR.h
zd1211/src/WS11UPhm.h
zd1211/src/WS11Ub.h
zd1211/src/WS11Ur.h
zd1211/src/zd1205.h
zd1211/src/zd1211.h
zd1211/src/zd80211.h
zd1211/src/zdapi.h
zd1211/src/zdbuf.h
zd1211/src/zdcompat.h
zd1211/src/zddebug.h
zd1211/src/zdencrypt.h
zd1211/src/zdequates.h
zd1211/src/zdglobal.h
zd1211/src/zdhci.h
zd1211/src/zdhw.h
zd1211/src/zdinlinef.h
zd1211/src/zdmic.h
zd1211/src/zdmmrx.h
zd1211/src/zdpmfilter.h
zd1211/src/zdpsmon.h
zd1211/src/zdshared.h
zd1211/src/zdsm.h
zd1211/src/zdsorts.h
zd1211/src/zdtkipseed.h
zd1211/src/zdtypes.h
zd1211/src/zdusb.h
zd1211/src/zdutils.h
zd1211/src/zdversion.h
zd1211/tools/
zd1211/tools/Makefile
zd1211/tools/apdbg.c
kr3mliyn@a7017:~$ cd ~/zd1211
kr3mliyn@a7017:~/zd1211$ sudo Make Clean
sudo: Make: command not found
kr3mliyn@a7017:~/zd1211$ sudo make clean
kr3mliyn@a7017:~/zd1211$ sudo make
/lib/modules/2.6.10/build
/home/kr3mliyn/zd1211
-I/home/kr3mliyn/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -Wno-unused -pipe -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DfTX_GAIN_OFDM=0
make -C /lib/modules/2.6.10/build SUBDIRS=/home/kr3mliyn/zd1211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/kr3mliyn/zd1211/src/zd1205.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdasocsvc.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdauthreq.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdauthrsp.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdmmrx.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdshared.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdhci.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdglobal.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdencrypt.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdpmfilter.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdpsmon.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdsynch.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdbuf.o
  CC [M]  /home/kr3mliyn/zd1211/src/zd1205_proc.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdhw.o
  CC [M]  /home/kr3mliyn/zd1211/src/zddebug.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdtkipseed.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdmic.o
  CC [M]  /home/kr3mliyn/zd1211/src/zdusb.o
  CC [M]  /home/kr3mliyn/zd1211/src/zd1211.o
  LD [M]  /home/kr3mliyn/zd1211/zd1211.o
  Building modules, stage 2.
  MODPOST
  CC	  /home/kr3mliyn/zd1211/zd1211.mod.o
  LD [M]  /home/kr3mliyn/zd1211/zd1211.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
kr3mliyn@a7017:~/zd1211$ sudo make install
/lib/modules/2.6.10/build
/home/kr3mliyn/zd1211
-I/home/kr3mliyn/zd1211/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -Wno-unused -pipe -DAMAC -DGCCK -DOFDM -DUSE_EP4_SET_REG -DfTX_GAIN_OFDM=0
make -C /lib/modules/2.6.10/build SUBDIRS=/home/kr3mliyn/zd1211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
mkdir -p /lib/modules/2.6.10/net
cp zd1211.ko /lib/modules/2.6.10/net
depmod -a
gcc -o apdbg tools/apdbg.c
chmod +x apdbg
cp ./apdbg /usr/local/sbin/apdbg
kr3mliyn@a7017:~/zd1211$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
kr3mliyn@a7017:~/zd1211$ sudo modprobe zd1211
kr3mliyn@a7017:~/zd1211$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
kr3mliyn@a7017:~/zd1211$
``` 
...bump v2.0...

Note: - You might wanna change: -

 > sudo Make Clean
  sudo Make
  sudo Make Install 
To their lowercase counterparts, potential stumbling block for complete &quot;copy + paste&quot; nubes... not that I'd ever just 'copy and paste'... ;)

---

### Post by brousch on 2005-08-01
Thanks, I will change them to 'make'. In my opinion, a good HowTo can be done with mostly copy and paste.

Incidentally, did the Howto work for you?

I ran into a couple of other headaches today:

I had trouble with 128-Bit WEP, although 64-Bit worked OK. I don't know if it is my wifi router or my usb dongle though.

Also it turns out that Ubuntu does not like both the eth0 and wlan0 using dhclient at the same time. I was unable to connect to my wireless due to problems getting an IP Address and couldn't figure out what was going on. Then I noticed that eth0 had been activated at bootup. As soon as I [FONT=Courier New]ifdown eth0[/FONT] I was able to use wlan0.

That's a tip to stick in the old noggin!

---

### Post by kr3mliyn on 2005-08-02
Hey brousch. Your HOWTOs helpful in grasping the process, but I probably should have just dumped the last few lines of my attempt at your guide: -

 ```
kr3mliyn@a7017:~/zd1211$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
``` 

Still no luck! Ah well. I'm re-defecting back to Gentoo on my iBook for the time being (2.6.12 kernel seems to be fine in their world, and all I really want is wireless on my iBook, theres even a neat hack utilising [Airport Extreme Internet Sharing through MacOnLinux]("http://forums.gentoo.org/viewtopic-t-365647.html") which should be interesting). My Advent will stay Ubuntu though, and this time, Gnome's coming with me, fond memories of Fluxbox, but Gnome just feels that little bit more complete and it actually has a rather nice standard interace.

Gonna search high and low for a way of making my Advent "zd1211" (or even zd1201, I'm getting desperate!)

Ja Matta Ne brousch-san! I'll keep you updated!

---

### Post by brousch on 2005-08-02
I encountered similar errors last night. The way I fixed it was:

Unplug the dongle
Reboot
[FONT=Courier New]sudo ifdown eth0[/FONT] (and any other network devices you may have hanging around)
Plug in the dongle
[FONT=Courier New]sudo ifup wlan0[/FONT]
System -> Admin -> Networking
Select wlan0
Deactivate
Select wlan0
Activate
Twiddle thumbs
Click the OK to close networking
[FONT=Courier New]sudo dhclient wlan0[/FONT]

I ran into this due to the previously mentioned problems with 128-Bit WEP. It seemed to totally screw up my wireless and I could only fix it by rebooting.

BTW, it seems you have to close the Networking window in order for the interface to come up. I ran into this with a Dial-up connection a while ago too.

---

### Post by kr3mliyn on 2005-08-03
As a last port of call, I tried your quick FAQ... nothing doing it seems... :cry:, ah well, Gentoo's currently doing its thing (screwed up earlier, didn't make the kernel, just configured settings and yaboot (PPC equivalent of LILO) gave me the heads up... woo... hoo... :neutral:).

Thanks for your help though man, I'll definatly give it another pop when Breezy comes out, used to be a x86 Solaris kid (don't ask), but I've made the transition, and even though I've still got love for UNIX/BSD, Linux has so many flavours, and I'm forever curious... so, looks like I won't be commiting to an OS for  long while.

Peace brousch!

---

### Post by jr_G-man on 2005-08-27
I am in the process of getting my ZD1211-based adapter working.  I have posted a blog entry about my experiences with it so far here:  [http://www.bloglines.com/blog/jrgman?id=5](http://www.bloglines.com/blog/jrgman?id=5)

I have some updates though.  I'll let you know when I post them, if you like.

---

### Post by Arneball on 2006-02-14
Hello there! After having som difficults installing zd1201 (!) i try zd1211 instead (1201 was wrong drivers, 2 days for nothing :P )

while make install i get: (translated from swedish to english)
cp: can't take status on "zd1211.ko" the file or the path doesnot exist

i've tried finding that file to manually copy it to /lib/modules/2.6.12-10-386/net but i couldn't find it. What to do next?
Thx

---

