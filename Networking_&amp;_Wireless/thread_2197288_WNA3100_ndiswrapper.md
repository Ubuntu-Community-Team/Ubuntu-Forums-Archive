---
title: "WNA3100 ndiswrapper"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by brian.morales7 on 2014-01-03
First, thank you to this amazing community of volunteer's who truly try their best in assisting and helping all the noobs around. KUDOS fo sho.

I have read more than 15+ threads, and attempted many different versions of getting this to work, yet, I feel that I am getting stuck at a very simple and pathetic spot, but because of my limited linux knowledge I'm hitting a brick wall.

As stated in title, I have been at this for two days, on day one, I had installed ubuntu on a partition, which also had windows xp pro. I wanted to get rid of it and do a full switch to linux. Many attempts and commands to get the wifi usb module working brought no success. Though I did see the name of the usb device in the terminal, and I had a driver in the windows wireless drives software app, but no succeed, it seemed to be an issue due to ndiswrapper, but beyond that many folders where permissions restricted. Much of what I was doing in terminal was ending with a blocked door of no permissions allowed etc. I soon found out that it may have to do with the fact that the drive/partition was mounted therefore I couldn't unmount it and THUS... I blasted away windows XP Pro, now I have a fresh full ubuntu install. I wanted to use the folders usr/src to put some system files in, but folder perms there are still blocked for some reason. go figure, thought the fresh install would remove that.

I would really appreciate some assistance, I can do what you ask step by step, or you can toss me some links and commands and I can try to continue figuring it out... but any direction will be greatly appreciated.

Since todays fresh OS install, I have downloaded and attempted to install ndiswrapper, and the netgear driver. I did a ndiswrapper install through the terminal and it looked good but then gave an error

```
Selecting previously unselected package ndiswrapper-dkms.
(Reading database ... 173926 files and directories currently installed.)
Unpacking ndiswrapper-dkms (from .../ndiswrapper-dkms_1.57-1ubuntu1_all.deb) ...
Setting up ndiswrapper-dkms (1.57-1ubuntu1) ...
Loading new ndiswrapper-1.57 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-35-generic
Building initial module for 3.8.0-35-generic
Error! Bad return status for module build on kernel: 3.8.0-35-generic (x86_64)
Consult /var/lib/dkms/ndiswrapper/1.57/build/make.log for more information.
```

I saw many threads by [COLOR=#000000]chili555[/COLOR], (kudos for putting up with all us crazy wna'ers) but on one particular he suggested that the member would delete all prev installs first with a certain command, and I did that but the error at that time stated it couldn't remove it all because other things/programs depended on it.
I'm not super confident, but I think my problem is laying with ndiswrapper and getting it to install properly, I can only hope its smooth sailing after that...

My Wired Connection has been working fine.

Again I appreciate anyone who can assist, and I hope I am not too vague in this request, although I'm sure that I am, please ask for any clarifications, and I'll get right on it.

Thanks in advance!

---

### Post by ajgreeny on 2014-01-03
What version of ubuntu, as ndiswrapper is broken in 12.04.

If you are using 12.04 you can compile and install ndiswrapper easily by following the instructions below.
> Download source archive for 1.59 from sourceforge :-
[http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files](http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files)

Install:-
ndisgtk, ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source and ndiswrapper-utils-#.#
plus all dependencies.

Ensure you have installed the linux-header packages for your kernel version.

cd to extracted ndiswrapper-#.## folder

Run these commands in order:-

```
sudo make
sudo make install
sudo modprobe ndiswrapper
```

Now run ndisgtk to install your windows driver.inf file. Wireless connection should now be available.

---

### Post by brian.morales7 on 2014-01-03
Aj thanks a bunch for this guidance. ndiswrapper is broken in 12.04? Gosh, well that explains it... Affirmative I am using 12.04, Yes, I am  I can't believe I didn't run into this sooner on any other posts. I will try your suggestions after work, this afternoon. About 9 hours till then, its bound to be a good Friday... I hope ^-^

In case you or anyone can answer these simple questions before I get home to attempt these, here they are:
-Do I have to uninstall any current packages or installs, whether for ndiswrapper or kernal or anthing? (Last time I ran a removal command it mentioned not being able to remove all of ndiswrapper because some files depended on it. I hope I dont run into that again) If so, please let me know which command I should use to remove previous install of ndiswrapper.
-How can I ensure that I have the header packages installed? On my first OS install, I recall the second day of auto updates contained header packages to be updated. How can I verify that I have the correct headers installed? Is it: [COLOR=#000000][FONT=Consolas]uname -r [/FONT][/COLOR] Also, then how do I know which kernal version I have and which package I need.

Ok someone tell me I'm reading into this too much? In any case, I will do the best I can when I get home ^-^ Thanks Again!

---

### Post by ajgreeny on 2014-01-03
I did not remove any of the ndis(wrapper) packages on my old laptop with a different netgear pcmcia card so still have to various packages still on it and the ndiswrapper archive version 1.59 which I built and installed exactly as I said.

You can find the running kernel version with command **uname -a** and then find out if you have the header packages easiest using synaptic; install it if you haven't already got it; you will never regret doing so, then by searching in synaptic for that version number, eg, **3.8.0-35**

Good luck, I hope it works for you as easily as it did for me, several times, as I had to do it for new kernel versions when I installed them.

---

### Post by brian.morales7 on 2014-01-03
Well I did what you commanded to no avail... Every step seems to have worked fine, except when I go to the drive to install it, it says "Invalid Driver" I tried three different drivers I found at different places but all .inf files were named bcmwlhigh5.inf,  not sure if I missed something so I'll post the terminal progress, 

> brimoknight@Vostro-220-Series:~/Downloads/ndiswrapper-1.59$ sudo apt-get install ndisgtk ndiswrapper-common ndiswrapper-dkms ndiswrapper-source ndiswrapper-utils-1.59
[sudo] password for brimoknight: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndiswrapper-utils-1.59
E: Couldn't find any package by regex 'ndiswrapper-utils-1.59'
brimoknight@Vostro-220-Series:~/Downloads/ndiswrapper-1.59$ sudo make
make -C utils
make[1]: Entering directory `/home/brimoknight/Downloads/ndiswrapper-1.59/utils'
gcc -g -Wall -I../driver  -o loadndisdriver loadndisdriver.c
make[1]: Leaving directory `/home/brimoknight/Downloads/ndiswrapper-1.59/utils'
make -C driver
make[1]: Entering directory `/home/brimoknight/Downloads/ndiswrapper-1.59/driver'
make -C /usr/src/linux-headers-3.8.0-35-generic M=/home/brimoknight/Downloads/ndiswrapper-1.59/driver
make[2]: Entering directory `/usr/src/linux-headers-3.8.0-35-generic'
  LD      /home/brimoknight/Downloads/ndiswrapper-1.59/driver/built-in.o
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/crt_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/hal_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ndis_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ntoskernel_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ntoskernel_io_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/rtl_exports.h
  MKEXPORT /home/brimoknight/Downloads/ndiswrapper-1.59/driver/usb_exports.h
  MKSTUBS /home/brimoknight/Downloads/ndiswrapper-1.59/driver/win2lin_stubs.h
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/crt.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/hal.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/iw_ndis.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/loader.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ndis.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ntoskernel.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ntoskernel_io.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/pe_linker.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/pnp.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/proc.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/rtl.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/wrapmem.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/wrapndis.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/wrapper.o
  CC [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/usb.o
  AS [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/win2lin_stubs.o
  AS [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/lin2win.o
  LD [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ndiswrapper.mod.o
  LD [M]  /home/brimoknight/Downloads/ndiswrapper-1.59/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.8.0-35-generic'
make[1]: Leaving directory `/home/brimoknight/Downloads/ndiswrapper-1.59/driver'
brimoknight@Vostro-220-Series:~/Downloads/ndiswrapper-1.59$ sudo make install
make -C driver install
make[1]: Entering directory `/home/brimoknight/Downloads/ndiswrapper-1.59/driver'
mkdir -p -m 755 /lib/modules/3.8.0-35-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/3.8.0-35-generic/misc
/sbin/depmod -a 3.8.0-35-generic
make[1]: Leaving directory `/home/brimoknight/Downloads/ndiswrapper-1.59/driver'
make -C utils install
make[1]: Entering directory `/home/brimoknight/Downloads/ndiswrapper-1.59/utils'
mkdir -p -m 755 /sbin
mkdir -p -m 755 /usr/sbin
install -m 755 loadndisdriver /sbin
install -m 755 ndiswrapper /usr/sbin
install -m 755 ndiswrapper-buginfo /usr/sbin
make[1]: Leaving directory `/home/brimoknight/Downloads/ndiswrapper-1.59/utils'
mkdir -p -m 755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
brimoknight@Vostro-220-Series:~/Downloads/ndiswrapper-1.59$ sudo modprobe ndiswrapper
brimoknight@Vostro-220-Series:~/Downloads/ndiswrapper-1.59$

At this point im not sure if I just need to find another "valid" driver and that is all or if I actually messed up a step. Well, its been a good 2-3 hours, I wont stop now, but I hope I hear from someone soon, for now, Ill continue researching...

Thanks for all your expertise.

---

### Post by ajgreeny on 2014-01-04
Well, it looks as if the ndsiwrapper installed OK and the module is now loaded as there was no error from the modprobe command, so, yes, it looks as if the driver file or files you have are not appropriate for use with ndiswrapper.

If you've not already seen these two threads they may offer more info and help, or may just confuse you more, of course.  Good luck whatever happens.
[http://ubuntuforums.org/showthread.php?t=1965989](http://ubuntuforums.org/showthread.php?t=1965989)
[http://ubuntuforums.org/showthread.php?t=2055145](http://ubuntuforums.org/showthread.php?t=2055145)

---

### Post by brian.morales7 on 2014-01-05
Awesome! I'm glad ndiswrapper finally works and installed properly. In regards to the driver, I found another driver in the first link you provided, chili555 had posted it, and it worked. It installed and did not say Invalid Driver. Great! I also see that the wireless card is active and found the wireless networks in my area, including my home router.

It all looks like it works, but I'm afraid its not FULLY working. As close as I feel I am, I don't know what I can attempt next.

The issue:
I select my network and the wireless acts as if its connecting, then asks for my network password, great, I enter it correctly, again it seems to be connecting then, it says connection disconnected. I haven't been able to make the connection with my router. I have no clue why it would be so close, right there and not connect fully,

- I updated my router firmware.
- Switched to a lower speed.
- Changed Channels
- Rebooted

Here are some commands I attempted that I saw another member type on another thread with generally the same issue, just in case it could be helpful:

> brimoknight@Vostro-220-Series:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"BrimoKnight"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 74:44:01:8A:35:4D   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:66934   Missed beacon:0

brimoknight@Vostro-220-Series:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9020) present
brimoknight@Vostro-220-Series:~$ dmesg |grep ndis
[   12.707597] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   14.141015] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   14.401703] usbcore: registered new interface driver ndiswrapper
[  362.380635] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  429.115143] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
[  444.709781] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
brimoknight@Vostro-220-Series:~$ 

brimoknight@Vostro-220-Series:~$ sudo cat /var/log/syslog | grep -i ndis | tail -n20
[sudo] password for brimoknight: 
Jan  4 18:42:47 Vostro-220-Series kernel: [149253.782990] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 18:43:03 Vostro-220-Series kernel: [149269.376042] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 18:51:03 Vostro-220-Series kernel: [149749.940960] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 18:58:47 Vostro-220-Series kernel: [150213.777866] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 18:59:03 Vostro-220-Series kernel: [150229.372147] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 19:07:03 Vostro-220-Series kernel: [150709.935523] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 19:08:59 Vostro-220-Series kernel: [150825.339739] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 19:10:18 Vostro-220-Series kernel: [150904.979892] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 19:10:34 Vostro-220-Series kernel: [150920.564694] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 19:21:00 Vostro-220-Series kernel: [151546.955257] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 23:51:56 Vostro-220-Series kernel: [167802.616229] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 23:52:12 Vostro-220-Series kernel: [167818.254187] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 23:52:50 Vostro-220-Series kernel: [   12.707597] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
Jan  4 23:52:50 Vostro-220-Series kernel: [   14.141015] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
Jan  4 23:52:50 Vostro-220-Series kernel: [   14.397751] wlan0: ethernet device 10:0d:7f:28:5c:a1 using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
Jan  4 23:52:50 Vostro-220-Series kernel: [   14.401703] usbcore: registered new interface driver ndiswrapper
Jan  4 23:53:00 Vostro-220-Series NetworkManager[955]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Jan  4 23:58:34 Vostro-220-Series kernel: [  362.380635] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 23:59:40 Vostro-220-Series kernel: [  429.115143] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
Jan  4 23:59:56 Vostro-220-Series kernel: [  444.709781] ndiswrapper (iw_set_freq:436): setting configuration failed (00010003)
brimoknight@Vostro-220-Series:~$ 






In any case, I'm extremely grateful for the progress we have made, I hope it is a very simple thing to get my network connected fully. Anyone out there have any ideas? Or any commands I was supposed to run? Thank you all... 

AJ... thanks again for everything... you've been amazing help... enjoy your weekend!

---

### Post by ajgreeny on 2014-01-05
One of the links I posted mentioned that connecting to an 802.11-n wireless did not work, but worked fine if -b or -g was used.  Have you tried downgrading the router speed temporarily?

---

### Post by brian.morales7 on 2014-01-05
(So, silly I forgot to post about my router setting change attempts on my last post)

Yes, I read both threads (and many more :/) and saw some good things to try, I have brought speed mode to: "Up to 54Mbps"
I also changed preamble to: Long (hoping that would affect something...)

Should I attempt anything in Traffic Meter? Where I can limit speeds I think.
Also curious about IPv6, it is set to: "Disabled" on the router settings, not sure if I should set it to something else (May it be known my home network has worked fine all along with it on "Disabled")

Well, after posting this I will try a reboot, see if anything changes...

In any case, I'm going to assume that everything in the terminal was accurate and correct with no issues found, since it was not mentioned...
Thanks for the suggestions...

Well off to reboot... wish me luck ^-^

UPDATE: Nothing has changed after the reboot. Still the wifi seems to locate my network, attempts to connect to it, and eventually says disconnected without ever having connected. Then it re attempts all over again... until I shut the wifi off...

I then tried to replace the current 64bit driver with the 32bit one to see if it would work.. and nope, it even shut down, and came up with this error screen.. I thought I broke the computer... then I manually shut my pc off then on again, and it let me on to the desktop where I just changed it back to 64bit driver.

Im starting to be worn out by these failed attempts. I dont want to buy another usb wifi stick... hmmm but yea,... Im losing hope fast being thats its about 3-4 days been trying to fix this thing... 

Any one out there have been to this stage of repeated on and off connections?

As always... thanks!

---

