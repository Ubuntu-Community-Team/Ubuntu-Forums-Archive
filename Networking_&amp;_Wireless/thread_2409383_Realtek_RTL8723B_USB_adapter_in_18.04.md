---
title: "Realtek RTL8723B USB adapter in 18.04"
date: 2019-01-01
forum: Networking &amp; Wireless
---

### Post by heatopher2 on 2019-01-01
Hi, I've just updated from 16.04 to 18.04, and have had a few teething problems, one of which is that I can't connect to the wifi at all at the moment, although initially it was more or less working OK. One thing that I suppose might be responsible is that I had a modified network manager file which I didn't overwrite during the update. I suppose that it was a bit stupid of me to assume that that wouldn't be a problem. If that's the problem, please just point me to the right place so that I can put it back to the correct settings. 

If not.... I'm referring back here to a thread that I started a couple of years ago, when I first installed this wifi adapter. I have a script called *solvewifi* which I have run every time I can't connect, and it's based on this answer to my post back then:

[https://ubuntuforums.org/showthread.php?t=2349727&p=13595876#post13595876](https://ubuntuforums.org/showthread.php?t=2349727&p=13595876#post13595876)

When I run the script, this is what I get:

```
kizza@heatopher % solvewifi                                                   ~
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-43-lowlatency/build M=/home/kizza/rtl8723bu  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-43-lowlatency'
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/kizza/rtl8723bu/core/rtw_cmd.o
In file included from /home/kizza/rtl8723bu/include/osdep_service.h:36:0,
                 from /home/kizza/rtl8723bu/include/drv_types.h:32,
                 from /home/kizza/rtl8723bu/core/rtw_cmd.c:22:
/home/kizza/rtl8723bu/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/kizza/rtl8723bu/include/osdep_service_linux.h:246:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/kizza/rtl8723bu/include/osdep_service_linux.h:247:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/kizza/rtl8723bu/include/drv_types.h:32:0,
                 from /home/kizza/rtl8723bu/core/rtw_cmd.c:22:
/home/kizza/rtl8723bu/include/osdep_service.h: In function ‘thread_enter’:
/home/kizza/rtl8723bu/include/osdep_service.h:260:2: error: implicit declaration of function ‘allow_signal’; did you mean ‘do_signal’? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/home/kizza/rtl8723bu/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/kizza/rtl8723bu/include/osdep_service.h:265:6: error: implicit declaration of function ‘signal_pending’; did you mean ‘timer_pending’? [-Werror=implicit-function-declaration]
  if (signal_pending (current))
      ^~~~~~~~~~~~~~
      timer_pending
/home/kizza/rtl8723bu/include/osdep_service.h:266:3: error: implicit declaration of function ‘flush_signals’; did you mean ‘do_signal’? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/kizza/rtl8723bu/core/rtw_cmd.o' failed
make[2]: *** [/home/kizza/rtl8723bu/core/rtw_cmd.o] Error 1
Makefile:1551: recipe for target '_module_/home/kizza/rtl8723bu' failed
make[1]: *** [_module_/home/kizza/rtl8723bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-43-lowlatency'
Makefile:321: recipe for target 'modules' failed
make: *** [modules] Error 2
[sudo] password for kizza: 
install -p -m 644 8723bu.ko  /lib/modules/4.15.0-43-lowlatency/kernel/drivers/net/wireless/
install: cannot stat '8723bu.ko': No such file or directory
Makefile:327: recipe for target 'install' failed
make: *** [install] Error 1
insmod /lib/modules/4.15.0-43-lowlatency/kernel/drivers/net/wireless/8723bu.ko 
modprobe: ERROR: could not insert '8723bu': Exec format error
```

Secondly, there's another similar script for when the system has been upgraded, which I call *recompilewifi*, which is based on this post further down that old thread:

[URL="https://ubuntuforums.org/showthread.php?t=2349727&p=13596057#post13596057"]https://ubuntuforums.org/showthread.php?t=2349727&p=13596057#post13596057

[/URL].... and what I get from that is the following:

```
kizza@heatopher % recompilewifi                                               ~
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd */*.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.15.0-43-lowlatency/build M=/home/kizza/rtl8723bu  modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-43-lowlatency'
Makefile:975: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/kizza/rtl8723bu/core/rtw_cmd.o
In file included from /home/kizza/rtl8723bu/include/osdep_service.h:36:0,
                 from /home/kizza/rtl8723bu/include/drv_types.h:32,
                 from /home/kizza/rtl8723bu/core/rtw_cmd.c:22:
/home/kizza/rtl8723bu/include/osdep_service_linux.h: In function ‘_init_timer’:
/home/kizza/rtl8723bu/include/osdep_service_linux.h:246:8: error: ‘_timer {aka struct timer_list}’ has no member named ‘data’
  ptimer->data = (unsigned long)cntx;
        ^~
/home/kizza/rtl8723bu/include/osdep_service_linux.h:247:2: error: implicit declaration of function ‘init_timer’; did you mean ‘_init_timer’? [-Werror=implicit-function-declaration]
  init_timer(ptimer);
  ^~~~~~~~~~
  _init_timer
In file included from /home/kizza/rtl8723bu/include/drv_types.h:32:0,
                 from /home/kizza/rtl8723bu/core/rtw_cmd.c:22:
/home/kizza/rtl8723bu/include/osdep_service.h: In function ‘thread_enter’:
/home/kizza/rtl8723bu/include/osdep_service.h:260:2: error: implicit declaration of function ‘allow_signal’; did you mean ‘do_signal’? [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
  do_signal
/home/kizza/rtl8723bu/include/osdep_service.h: In function ‘flush_signals_thread’:
/home/kizza/rtl8723bu/include/osdep_service.h:265:6: error: implicit declaration of function ‘signal_pending’; did you mean ‘timer_pending’? [-Werror=implicit-function-declaration]
  if (signal_pending (current))
      ^~~~~~~~~~~~~~
      timer_pending
/home/kizza/rtl8723bu/include/osdep_service.h:266:3: error: implicit declaration of function ‘flush_signals’; did you mean ‘do_signal’? [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
   do_signal
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/kizza/rtl8723bu/core/rtw_cmd.o' failed
make[2]: *** [/home/kizza/rtl8723bu/core/rtw_cmd.o] Error 1
Makefile:1551: recipe for target '_module_/home/kizza/rtl8723bu' failed
make[1]: *** [_module_/home/kizza/rtl8723bu] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-43-lowlatency'
Makefile:321: recipe for target 'modules' failed
make: *** [modules] Error 2
install -p -m 644 8723bu.ko  /lib/modules/4.15.0-43-lowlatency/kernel/drivers/net/wireless/
install: cannot stat '8723bu.ko': No such file or directory
Makefile:327: recipe for target 'install' failed
make: *** [install] Error 1
insmod /lib/modules/4.15.0-43-lowlatency/kernel/drivers/net/wireless/8723bu.ko 
modprobe: ERROR: could not insert '8723bu': Exec format error

```

I'm not very confident with this nuts and bolts stuff, so don't really know how to interpret very much!

I do need to add that the wifi gremlins never went away entirely, and that more often than not I would have to run the *solvewifi* script at least once per session, so if someone can help me SOLVEWIFI once and for all, I would be **profoundly grateful** :P

Thanks in advance!

---

### Post by jeremy31 on 2019-01-01
Do a
```
cd rtl8723bu
git pull
sudo apt install git dkms
make
```

If that happens to build without issues do
```
make clean
cd
sudo dkms add rtl8723bu
sudo dkms install rtl8723bu/4.3.6.11_12942.20141204_BTCOEX20140507-4E40
```
Reboot

---

### Post by heatopher2 on 2019-01-01
No good, I'm afraid. Is it the network manager file?

---

### Post by jeremy31 on 2019-01-01
Lets do another approach
```
rm -rf rtl8723bu
sudo apt install git dkms
git clone https://github.com/lwfinger/rtl8723bu.git
cd rtl8723bu
make
sudo make install
```

---

### Post by heatopher2 on 2019-01-01
Done that and rebooted. Still no good. "No networks" or it shows the network and fails to connect :(

---

### Post by jeremy31 on 2019-01-01
See the wireless script link in my signature and post results

---

### Post by heatopher2 on 2019-01-01
```
sudo apt update
sudo apt dist-upgrade
Hit:1 http://gb.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Ign:3 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                     
Get:5 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Get:8 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [413 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [476 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [245 kB]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [235 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [55.7 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [105 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [256 kB]
Get:15 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [178 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [200 kB]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [14.9 kB]
Get:19 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9,088 B]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [39.7 kB]
Get:21 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons [53.3 kB]
Get:22 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [176 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [332 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [770 kB]
Get:25 http://gb.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:26 http://gb.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,812 B]
Fetched 3,815 kB in 3s (1,448 kB/s)                                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  tzdata
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 189 kB of archives.
After this operation, 14.3 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu bionic-updates/main amd64 tzdata all 2018i-0ubuntu0.18.04 [189 kB]
Fetched 189 kB in 0s (1,450 kB/s)
Preconfiguring packages ...
(Reading database ... 462447 files and directories currently installed.)
Preparing to unpack .../tzdata_2018i-0ubuntu0.18.04_all.deb ...
Unpacking tzdata (2018i-0ubuntu0.18.04) over (2018g-0ubuntu0.18.04) ...
Setting up tzdata (2018i-0ubuntu0.18.04) ...

Current default time zone: 'Europe/London'
Local time is now:      Tue  1 Jan 21:51:11 GMT 2019.
Universal Time is now:  Tue Jan  1 21:51:11 UTC 2019.
Run 'dpkg-reconfigure tzdata' if you wish to change it.
```

Just that one for now?

---

### Post by jeremy31 on 2019-01-01
you missed ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by heatopher2 on 2019-01-01
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \                                           
chmod +x wireless-info && \
./wireless-info
--2019-01-01 22:23:45--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 140.82.118.4, 140.82.118.3
Connecting to github.com (github.com)|140.82.118.4|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2019-01-01 22:23:45--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.60.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.60.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17452 (17K) [text/plain]
Saving to: 'wireless-info’

wireless-info                      100%[================================================================>]  17.04K  --.-KB/s    in 0.009s  

Last-modified header missing -- time-stamps turned off.
2019-01-01 22:23:45 (1.79 MB/s) - 'wireless-info’ saved [17452/17452]

[sudo] password for kizza: 

Results saved in "/home/kizza/wireless-info.txt".

Results also archived in "/home/kizza/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.

Do you also want to post them to your default 'pastebinit' provider? [Y/n]: y

Pastebin successful:

http://paste.ubuntu.com/p/d45WpdVgyC/


```

Rebooting now

---

### Post by jeremy31 on 2019-01-01
Try ```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```
Reboot

---

### Post by heatopher2 on 2019-01-01
Still no good, and I'm also now having problems with the wired connection to the router :-& Having to unplug, restart, etc.

Ah, sorry, didn't see that last post. Half a minute.....

```
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf 
[sudo] password for kizza: 
blacklist rtl8xxxu


```

Or was I meant to put this?

```
echo "blacklist rtl8723bu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
blacklist rtl8723bu

```

---

### Post by jeremy31 on 2019-01-01
That is normal, reboot

Don't blacklist rtl8723bu

---

### Post by heatopher2 on 2019-01-01
Or even this? :D

```
echo "blacklist rtl8723bu" | sudo tee /etc/modprobe.d/rtl8723bu.conf
blacklist rtl8723bu

```

> **jeremy31 said:**
> that is normal, reboot

don't blacklist rtl8723bu

ok....

Sorry, I actually don't really understand. I have to **un**blacklist it? No idea how that works....

---

### Post by jeremy31 on 2019-01-01
Remove blacklist ```
sudo rm /etc/modprobe.d/rtl8723bu.conf
```

Forgot that Larry Fingers source uses the concurrent mode
```
sudo dkms uninstall rtl8723bu/4.3.6.11_12942.20141204_BTCOEX20140507-4E40
sudo dkms remove rtl8723bu/4.3.6.11_12942.20141204_BTCOEX20140507-4E40 --all
rm -rf rtl8723bu
git clone https://github.com/jeremyb31/rtl8723bu.git
sudo dkms add ./rtl8723bu
cd rtl8723bu
make 
sudo make install
make clean
```
Reboot

---

### Post by clementc on 2019-01-01
Hi [**heatopher2**]("https://ubuntuforums.org/member.php?u=2055648"),

To un-blacklist a module, please make sure that no file (and particularly rtl8723bu.conf) contains the line: blacklist rtl8723bu

Can you also please try running the following commands in Terminal (you might have to reboot your PC first) and see if this helps:

```
modprobe -rfv 8723bu
modprobe -rtv rtl8xxxu
modprobe -v 8723bu ant_sel=1
modprobe -v rtl8xxxu ant_sel=1
```

---

### Post by heatopher2 on 2019-01-01
I rebooted, and still not OK. Is that because I blacklisted rtl8723bu? I'm getting lost.

> **clementc said:**
> Hi [**heatopher2**]("https://ubuntuforums.org/member.php?u=2055648"),

To un-blacklist a module, please make sure that no file (and particularly rtl8723bu.conf) contains the line: blacklist rtl8723bu

Can you also please try running the following commands in Terminal (you might have to reboot your PC first) and see if this helps:

```
modprobe -rfv 8723bu modprobe -rtv rtl8xxxu
modprobe -v 8723bu ant_sel=1
modprobe -v rtl8xxxu ant_sel=1
```

Again, sorry.... I didn't see this message before posting that last one. I'll do that stuff now......

```
modprobe -rfv 8723bu modprobe -rtv rtl8xxxu
modprobe -v 8723bu ant_sel=1
modprobe -v rtl8xxxu ant_sel=1
modprobe: invalid option -- 't'
insmod /lib/modules/4.15.0-43-lowlatency/kernel/net/mac80211/mac80211.ko 
modprobe: ERROR: could not insert 'rtl8xxxu': Operation not permitted

```

Not connecting, BUT now I can see my network on the drop-down menu

And now it IS connected. Well, that's a relief!!! Is that all done now?

I'm going to try rebooting and see if it connects automatically now....

Well, that seems to be just about OK now, but I'll of course come back here if there are any more issues. Thanks very much, and of course Happy New Year!

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]heatopher2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2055648"),

I am glad to hear that your problem is now fixed.

Happy new year to you too and see you around.

---

### Post by heatopher2 on 2019-01-02
Hey, it was actually still not quite OK when I rebooted this morning, but then I ran the *solvewifi*  script which I mentioned before, and the connection seems stable for  the time being. Not sure why, of course, and whether or not it will  last!

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]heatopher2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2055648"),

You might still have to run the solvewifi script in order to fix your WiFi issues. If I am not mistaken, this is what you were already doing in the past to make it work.

If you need to run this script every time your computer boots up, you could schedule a task to run the script at every boot like this:

1. In Terminal, run: sudo crontab -e
2. Add: @reboot /your/script/path
3. Remove/rename the file: /var/run/crond.reboot (if it is empty).

---

### Post by jeremy31 on 2019-01-02
heatopher2, check ```
uname -r
```
Just to see if the kernel changed

---

