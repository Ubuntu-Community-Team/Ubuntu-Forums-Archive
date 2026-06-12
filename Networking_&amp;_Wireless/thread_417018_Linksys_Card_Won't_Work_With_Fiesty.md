---
title: "Linksys Card Won't Work With Fiesty"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by Dr.Awesome on 2007-04-21
I upgraded to Fiesty last night.  Before that, I had no problems using my Linksys Wireless Card.  But now, I am unable to see the card under "networks."  I'm pretty inexperienced with Ubuntu, but Edgy had been working fine.

The card is a Linksys Wireless-B card, model number WPC11 ver. 4

Any help would be greatly appreciated.

---

### Post by smartboyathome on 2007-04-21
Try searching the forum for this. I saw an answer for this last night.

---

### Post by Dr.Awesome on 2007-04-21
I have searched the forums but have had no luck in finding a solution.  If you see the thread with the solution, will you post the link?

Thanks,
Dr.A

---

### Post by tturrisi on 2007-04-21
I'm using a Linksys WPC11-v4 right now!
You need the rt8180 drivers.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

---

### Post by Dr.Awesome on 2007-04-21
> **tturrisi said:**
> I'm using a Linksys WPC11-v4 right now!
You need the rt8180 drivers.
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

I went to the site that you linked and downloaded the folder and extracted it (rtl9190-0.21). I'm still unable to install the driver correctly.  Can you help me? I am completely inexperienced with linux.

Thanks in advance,
Dr.A

---

### Post by tturrisi on 2007-04-22
Remove the card.
Open a terminal and 
copy+paste each line, one at a time.

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r` 
wget [http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz](http://ovh.dl.sourceforge.net/sourceforge/rtl8180-sa2400/rtl8180-0.21.tar.gz)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
make && make install
depmod -a
modprobe r8180

Insert the card, wait for card led to light up, use System>Administration>Networking to setup the card.
If get errors using apt-get then do:
sudo gedit /etc/apt/sources.list
and uncomment the Universe & MultiUnivers sources.
Save the changes.
do:
sudo apt-get update
Retry installing.

---

### Post by Dr.Awesome on 2007-04-22
thanks for your patience and help.  I followed your instructions and everything seemed to go smoothly until the make && make install command.  This was the output:

warren@ubuntu:~/rtl8180-0.21$ make && make install

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/warren/rtl8180-0.21 MODVERDIR=/home/warren/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
scripts/Makefile.build:17: /home/warren/rtl8180-0.21/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/warren/rtl8180-0.21/Makefile'.  Stop.
make[1]: *** [_module_/home/warren/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [2.6] Error 2

warren@ubuntu:~/rtl8180-0.21$ depmod -a
FATAL: Could not open /lib/modules/2.6.20-15-generic/modules.dep.temp for writing: Permission denied

warren@ubuntu:~/rtl8180-0.21$ modprobe r8180FATAL: Module r8180 not found.

warren@ubuntu:~/rtl8180-0.21$ 

So, I'm not sure what I'm doing wrong.

-D.A.

---

### Post by tturrisi on 2007-04-22
Open a root terminal & do it all again.  (no sudo)
apt-get install build-essential
apt-get install linux-headers-`uname -r`
wget [http://ovh.dl.sourceforge.net/source...80-0.21.tar.gz](http://ovh.dl.sourceforge.net/source...80-0.21.tar.gz)
tar -xvzf rtl8180-0.21.tar.gz
cd rtl8180-0.21
make && make install
depmod -a
modprobe r8180

---

### Post by chamberlain2006 on 2007-04-22
You've put apti-get instead of apt-get on the first line twice.

---

### Post by tturrisi on 2007-04-22
:)   havent you ever apti-getted a package!
thanks...

---

### Post by kweejibo on 2007-04-23
Tried this from root and I still get this:

root@ubuntu:/# tar -xvzf rtl8180-0.21.tar.gz 
rtl8180-0.21/
rtl8180-0.21/Makefile
rtl8180-0.21/AUTHORS
rtl8180-0.21/CHANGES
rtl8180-0.21/COPYING
rtl8180-0.21/INSTALL
rtl8180-0.21/LICENSE
rtl8180-0.21/Makefile26
rtl8180-0.21/README
rtl8180-0.21/README.adhoc
rtl8180-0.21/compat24.h
rtl8180-0.21/ieee80211.h
rtl8180-0.21/ieee80211_crypt.c
rtl8180-0.21/ieee80211_crypt.h
rtl8180-0.21/ieee80211_crypt_wep.c
rtl8180-0.21/ieee80211_module.c
rtl8180-0.21/ieee80211_rx.c
rtl8180-0.21/ieee80211_tx.c
rtl8180-0.21/ieee80211_wx.c
rtl8180-0.21/ieee802_11.h
rtl8180-0.21/module_load
rtl8180-0.21/module_load24
rtl8180-0.21/module_unload
rtl8180-0.21/module_unload24
rtl8180-0.21/r8180.h
rtl8180-0.21/r8180_93cx6.c
rtl8180-0.21/r8180_93cx6.h
rtl8180-0.21/r8180_core.c
rtl8180-0.21/r8180_gct.c
rtl8180-0.21/r8180_gct.h
rtl8180-0.21/r8180_hw.h
rtl8180-0.21/r8180_max2820.c
rtl8180-0.21/r8180_max2820.h
rtl8180-0.21/r8180_pm.c
rtl8180-0.21/r8180_pm.h
rtl8180-0.21/r8180_sa2400.c
rtl8180-0.21/r8180_sa2400.h
rtl8180-0.21/r8180_wx.c
rtl8180-0.21/r8180_wx.h
rtl8180-0.21/README.master
root@ubuntu:/# cd rtl8180-0.21/
root@ubuntu:/rtl8180-0.21# make && make install
make -C /lib/modules/2.6.20-15-386/build SUBDIRS=/rtl8180-0.21 MODVERDIR=/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
scripts/Makefile.build:17: /rtl8180-0.21/Makefile: No such file or directory
make[2]: *** No rule to make target `/rtl8180-0.21/Makefile'.  Stop.
make[1]: *** [_module_/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [2.6] Error 2
root@ubuntu:/rtl8180-0.21# 

Now what?

Josh

---

### Post by Dr.Awesome on 2007-04-23
So, I logged into root and followed the instructions.  I again had error messages beginning with make && make install.  This is what I got:

root@ubuntu:~# tar -xvzf rtl8180-0.21.tar.gz
rtl8180-0.21/
rtl8180-0.21/Makefile
rtl8180-0.21/AUTHORS
rtl8180-0.21/CHANGES
rtl8180-0.21/COPYING
rtl8180-0.21/INSTALL
rtl8180-0.21/LICENSE
rtl8180-0.21/Makefile26
rtl8180-0.21/README
rtl8180-0.21/README.adhoc
rtl8180-0.21/compat24.h
rtl8180-0.21/ieee80211.h
rtl8180-0.21/ieee80211_crypt.c
rtl8180-0.21/ieee80211_crypt.h
rtl8180-0.21/ieee80211_crypt_wep.c
rtl8180-0.21/ieee80211_module.c
rtl8180-0.21/ieee80211_rx.c
rtl8180-0.21/ieee80211_tx.c
rtl8180-0.21/ieee80211_wx.c
rtl8180-0.21/ieee802_11.h
rtl8180-0.21/module_load
rtl8180-0.21/module_load24
rtl8180-0.21/module_unload
rtl8180-0.21/module_unload24
rtl8180-0.21/r8180.h
rtl8180-0.21/r8180_93cx6.c
rtl8180-0.21/r8180_93cx6.h
rtl8180-0.21/r8180_core.c
rtl8180-0.21/r8180_gct.c
rtl8180-0.21/r8180_gct.h
rtl8180-0.21/r8180_hw.h
rtl8180-0.21/r8180_max2820.c
rtl8180-0.21/r8180_max2820.h
rtl8180-0.21/r8180_pm.c
rtl8180-0.21/r8180_pm.h
rtl8180-0.21/r8180_sa2400.c
rtl8180-0.21/r8180_sa2400.h
rtl8180-0.21/r8180_wx.c
rtl8180-0.21/r8180_wx.h
rtl8180-0.21/README.master

root@ubuntu:~# cd rtl8180-0.21

root@ubuntu:~/rtl8180-0.21# make && make install

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/root/rtl8180-0.21 MODVERDIR=/root/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
scripts/Makefile.build:17: /root/rtl8180-0.21/Makefile: No such file or directory
make[2]: *** No rule to make target `/root/rtl8180-0.21/Makefile'.  Stop.
make[1]: *** [_module_/root/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [2.6] Error 2

root@ubuntu:~/rtl8180-0.21# depmod -a

root@ubuntu:~/rtl8180-0.21# modprobe r8180

FATAL: Module r8180 not found.

root@ubuntu:~/rtl8180-0.21#

---

### Post by tturrisi on 2007-04-23
see if this deb of mine will install:
[http://members.cox.net/tonyt/rtl8180-sa2400-modules.deb](http://members.cox.net/tonyt/rtl8180-sa2400-modules.deb)

---

### Post by Rickh123456 on 2007-04-24
Hey Dr.
Can I ask what type of laptop you are using?  I am a new user also.  I read the info on SourceForge, and it looks like the driver has been in development for a while, and is supposed to work with the LInksys wpc11 ver 4.  I have one of these also, and plan to get it working, so I am really curious about your experience.

---

### Post by Dr.Awesome on 2007-04-24
I'm using a Toshiba Satellite.  It's a few years old.  I don't remember the real specs off the top of my head (and I'm so inexperienced with Ubuntu that I don't really even know how to check them).

-D.A.

---

### Post by Dr.Awesome on 2007-04-24
> **tturrisi said:**
> see if this deb of mine will install:
[http://members.cox.net/tonyt/rtl8180-sa2400-modules.deb](http://members.cox.net/tonyt/rtl8180-sa2400-modules.deb)

I clicked the link, but got an error message in the package installer: 
Error: Dependency is not satisfiable: linux-image-2.6.18-3-386|kernal-image-2.6.18-3-386

-D.A.

---

### Post by Sensei_V on 2007-04-24
> **Dr.Awesome said:**
> I clicked the link, but got an error message in the package installer: 
Error: Dependency is not satisfiable: linux-image-2.6.18-3-386|kernal-image-2.6.18-3-386

-D.A.

I get exactly the same problems.  When I run the "make" command, whether as root or not, the directory empties, so the subsequent commands don't have any files to work with.  I've actually had this problem when I've tried the "make" command before on other things under Edgy.  I'm new to Linux and haven't had much luck with building packages outside of apt-get.

When I tried the .deb package, I got the same message in the status section of Package Installer about the linux and kernel images.  Since this is a fresh installation of Feisty, my kernel version is 2.6.20-15-generic, at least that's what I get when I run "uname -r".

---

### Post by ggratto on 2007-04-24
I was having all sorts of issues and was trying wifiradar and a couple of other things when i noticed that there was a ndiswrapper gui....  well I could not get it to work using the cmd line so maybe.   anyway long story short. i got the rtl8180 windows drivers from realtek and selected the inf with the ndiswrapper gui...
gave a odd error about hardware not avalible... but then in the network config tool the WLAN interface showed up and in about 2 minutes I had my connection with WEP...  and the WPC11 v.4 card... Next step WPA.

---

### Post by tturrisi on 2007-04-25
OK.  The link to the download above is no longer valid.
Those modues were for a specific kernel and won't install on Ubuntu kernels.
This package should work though, it's the source code for the tl8180-sa2400.
Download the .deb file and install it using gdebi package installer.  (rt click > select "open w/ gdebi..."
This install ONLY the source code.

Next:
Open a terminal and run module-assistant.  Update & then select tl8180-sa2400 in the List and install the drivers.

Here's the download:
[download]("http://members.cox.net/tonyt/rtl8180-sa2400-source_0.21+cvs20050828-7_all.deb")

---

### Post by Sensei_V on 2007-04-26
> **ggratto said:**
> I was having all sorts of issues and was trying wifiradar and a couple of other things when i noticed that there was a ndiswrapper gui....  well I could not get it to work using the cmd line so maybe.   anyway long story short. i got the rtl8180 windows drivers from realtek and selected the inf with the ndiswrapper gui...
gave a odd error about hardware not avalible... but then in the network config tool the WLAN interface showed up and in about 2 minutes I had my connection with WEP...  and the WPC11 v.4 card... Next step WPA.

I was also able to get the card working using the ndiswrapper gui (package name ndisgtk) which gave me an Administration menu item called Windows Wireless Drivers.  Once I used this to install the Windoze driver from realtek, I had a WiFi section in my Network control panel.  It took me a while to figure it out, but everything is automated if you check the box for roaming mode rather than hard code the SSID, which only gave me WEP options for encryption.  In roaming mode, the NetworkManager applet (nm-applet) gives me a menu showing all the detected networks and their signal strength.  When I select a network, I am prompted for the password/key and told what type of encryption the network is using.

This is where I get stuck:  I enter the password and iwconfig tells me I am associated with the  correct SSID, but still no IP address from ifconfig or access to the web, ping, etc.  It only works if I set the router to use no wireless security, which is  a solution that I'm not comfortable with.  I get the same results from WEP, WPA, and WPA2.  I use an Airport Extreme base station from Apple, and I've heard that Apple's WEP key generation is different from other vendors.  I've looked at [xwepgen]("http://xwepgen.sourceforge.net/index.shtml"), but that seems to be designed for the opposite problem, i.e. getting Apple computers to login to other wireless routers.  Maybe this belongs in a different thread, but any help on WPA or WEP would be appreciated.

Would using the non-Windoze driver from tturrisi help with this problem?

Update: I figured out WPA.  I wrote about it in [another thread]("http://ubuntuforums.org/showthread.php?t=424262").

---

### Post by swordship on 2007-04-27
I'm working as root and I still get the same problem


root@ramblinman:/home/tpawlicki# !15
cd rtl8180-0.21
root@ramblinman:/home/tpawlicki/rtl8180-0.21# !23
make && make install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tpawlicki/rtl8180-0.21 MODVERDIR=/home/tpawlicki/rtl8180-0.21 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
scripts/Makefile.build:17: /home/tpawlicki/rtl8180-0.21/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/tpawlicki/rtl8180-0.21/Makefile'.  Stop.
make[1]: *** [_module_/home/tpawlicki/rtl8180-0.21] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [2.6] Error 2
root@ramblinman:/home/tpawlicki/rtl8180-0.21# depmod -a
root@ramblinman:/home/tpawlicki/rtl8180-0.21# modprobe r8180
FATAL: Module r8180 not found.
root@ramblinman:/home/tpawlicki/rtl8180-0.21#

---

### Post by fwheeler_1 on 2007-04-27
Hi guys-  I see you've been struggling with the same problem I have been in another thread.  I think I've finally got a pretty good picture of what is going on.  The short version is the native driver was blacklisted for some reason.  It can be "unblacklisted" and then the module can be loaded.  Then you can see and configure the card.  I've had the best luck configuring it manually (e.g. not using network-manager, although n-m will see the card after a manual config).

For the long story, please see the thread I've been working in ( [http://ubuntuforums.org/showthread.php?t=414594](http://ubuntuforums.org/showthread.php?t=414594) ) and spead the word to others.  I'm posting this using the card, which has been running fine for about 2 hours.  Good luck to all, Fw

---

### Post by tturrisi on 2007-04-27
> **swordship said:**
> I'm working as root and I still get the same problem

see my last post.

---

### Post by Dr.Awesome on 2007-04-27
> **fwheeler_1 said:**
> Hi guys-  I see you've been struggling with the same problem I have been in another thread.  I think I've finally got a pretty good picture of what is going on.  The short version is the native driver was blacklisted for some reason.  It can be "unblacklisted" and then the module can be loaded.  Then you can see and configure the card.  I've had the best luck configuring it manually (e.g. not using network-manager, although n-m will see the card after a manual config).

For the long story, please see the thread I've been working in ( [http://ubuntuforums.org/showthread.php?t=414594](http://ubuntuforums.org/showthread.php?t=414594) ) and spead the word to others.  I'm posting this using the card, which has been running fine for about 2 hours.  Good luck to all, Fw

I went to your thread and I can now access the wireless network on net-manager, but I still can't access my wireless network to get online.  When I followed your instructions in the terminal, I got the following output:

warren@ubuntu:~$ sudo iwconfig wlan0 essid holysmokesx
warren@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6598
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:af:80:28
Sending on   LPF/wlan0/00:0c:41:af:80:28
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
warren@ubuntu:~$ 

Any suggestions?

-D.A.

---

### Post by fwheeler_1 on 2007-04-27
Hi DA-  Sorry, I didn't notice that you cross-posted in my thread and your thread, or I would have anwered here, instead.  I have a few ideas for your consideration in the other thread.  Sorry for the mixup, --Fw

---

### Post by fwheeler_1 on 2007-04-29
Please see updated post in thread [http://ubuntuforums.org/showthread.php?p=2557243#post2557243](http://ubuntuforums.org/showthread.php?p=2557243#post2557243) for an update on how to make this work with Network Manager.  --Fw

---

