---
title: "How do I get Broadcom BCM4312 wifi to connect?"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by kayve on 2015-01-07
I cannot use my wireless device.  I am looking at this link:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

I just downloaded the 64bit driver from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

root@kayve-VIAO:~# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation

the way it used to work I would have to click a button in system to re-enable it or something.. can't do it.  Don't see any wireless networks.  What is happening in my
system right now is irrelevant.  I am at home using ethernet.  I need to use wifi at a class I am taking.  I cannot get a connection there using Ubuntu, although I can if I boot in god awful Windows 8.

Let me restate my question as posed in the subject:

How do I configure my Ubuntu to use my ethernet at home as I am doing right now but turn on the wifi at school?

The instructions in the help.ubuntu.com link are not clear to me.

[http://paste.ubuntu.com/9686060/](http://paste.ubuntu.com/9686060/)

root@kayve-VIAO:~# lspci -nvn | grep -i net
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
root@kayve-VIAO:~#

root@kayve-VIAO:~# uname -a
Linux kayve-VIAO 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
root@kayve-VIAO:~#

I'm not Karmic Koala anymore.  Someone should update that?  Me?

root@kayve-VIAO:~# lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
root@kayve-VIAO:~#

oh maybe this is a problem

root@kayve-VIAO:/home/kayve/src# ls
hybrid-v35_64-nodebug-pcoem-6_30_223_248.tar  Makefile  vegaprol64
lib                                           src       wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
root@kayve-VIAO:/home/kayve/src# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/3.8.0-35-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
root@kayve-VIAO:/home/kayve/src# ls lib
LICENSE.txt  wlc_hybrid.o_shipped
root@kayve-VIAO:/home/kayve/src#

I seem to have a debian driver for the same Broadcom wifi device.  That can't be good, right?

[http://kayve.net/broadcom.png](http://kayve.net/broadcom.png)

---

### Post by QIII on 2015-01-07
kayve:

Please stop making a series of unanswered posts.  If you have more to add before you get a response, please simply edit the existing post.

If someone responds, by all means make a new post after that.

Thanks.

---

### Post by kayve on 2015-01-07
the "unanswered posts" were more relevant information

I cannot use my wireless device.  I am looking at this link:

[https://help.ubuntu.com/community/Ha...kCardsBroadcom]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")

I just downloaded the 64bit driver from here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

root@kayve-VIAO:~# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation

the way it used to work I would have to click a button in system to  re-enable it or something.. can't do it.  Don't see any wireless  networks.  What is happening in my
system right now is irrelevant.  I am at home using ethernet.  I need to  use wifi at a class I am taking.  I cannot get a connection there using  Ubuntu, although I can if I boot in god awful Windows 8.

Let me restate my question as posed in the subject:

How do I configure my Ubuntu to use my ethernet at home as I am doing right now but turn on the wifi at school?

The instructions in the help.ubuntu.com link are not clear to me.

Here is more relevant information:

[http://paste.ubuntu.com/9686060/](http://paste.ubuntu.com/9686060/)

root@kayve-VIAO:~# lspci -nvn | grep -i net
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 0c)
root@kayve-VIAO:~#

root@kayve-VIAO:~# uname -a
Linux kayve-VIAO 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
root@kayve-VIAO:~#

I'm not Karmic Koala anymore.  Someone should update that?  Me?

root@kayve-VIAO:~# lsb_release -a
LSB Version:     core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
root@kayve-VIAO:~#

oh maybe this is a problem

root@kayve-VIAO:/home/kayve/src# ls
hybrid-v35_64-nodebug-pcoem-6_30_223_248.tar  Makefile  vegaprol64
lib                                           src       wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb
root@kayve-VIAO:/home/kayve/src# make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make: *** /lib/modules/3.8.0-35-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
root@kayve-VIAO:/home/kayve/src# ls lib
LICENSE.txt  wlc_hybrid.o_shipped
root@kayve-VIAO:/home/kayve/src

I seem to have a debian driver for the same Broadcom wifi device.  That can't be good, right?

Here is the window that used to work for me but doesn't anymore

[http://kayve.net/broadcom.png](http://kayve.net/broadcom.png)

---

### Post by QIII on 2015-01-07
Merged into Networking & Wireless.

Please also do not start multiple threads regarding the same issue.  If you would like your thread moved, click the "Report Post" button and ask a member of the staff to move it.

---

### Post by ajgreeny on 2015-01-07
Is this problem solved yet?  This thread is in such a messy state that I can not follow what has or has not happened.

If not have a look at the sticky at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by praseodym on 2015-01-07
Kernel 3.8 in Ubuntu 14.04?! Something went wrong during the dist-upgrade:
```

sudo apt-get install --reinstall linux-image-3.13.0-43-generic linux-headers-3.13.0-43-generic linux-headers-3.13.0-43 dkms build-essential linux-generic
```
Reboot and check
```

uname -a
```

---

### Post by chili555 on 2015-01-07
Then, after you are booted into a 3.13.0-xx kernel, hook up the ethernet and do:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```Reboot. Enjoy.

---

### Post by kayve on 2015-01-07
okay.. btw the automated update dingy went off let it do it's thing then the reinstall linux image command.. so I hope this looks right:

root@kayve-VIAO:~# uname -a
Linux kayve-VIAO 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
root@kayve-VIAO:~#

well so far I am happy I don't have to undim the gnome.. I don't have a wireless device here though.. I guess I could have a trip to starbucks or something...

I mean a wireless router.. my computer does have the broadcom thingie which I guess is a wireless device...

Thank you very much for your help.

---

### Post by chili555 on 2015-01-07
So now you have a proper kernel and installed the driver package. Was a wireless interface created, ideally wlan0?```
iwconfig
```Does it scan and see networks?```
sudo iwlist wlan0 scan
```If it does, it will probably connect when you have an access point available.

---

### Post by kayve on 2015-01-07
.. unfortunately, your suggestions have failed.

[http://paste.ubuntu.com/9690795/](http://paste.ubuntu.com/9690795/)

[http://kayve.net/barnes_test.png](http://kayve.net/barnes_test.png)

I can see no wireless networks.. Maybe I am confused about how to make that happen?  It is a bit of a catch 22 when you are somewhere you need to do wifi

---

### Post by chili555 on 2015-01-07
It doesn't appear that you have yet installed the driver. Please try again:```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```And then reboot.

---

### Post by kayve on 2015-01-07
[http://paste.ubuntu.com/9690883/](http://paste.ubuntu.com/9690883/)

The second one said it is already up to date.  Should I uninstall first?

---

### Post by chili555 on 2015-01-07
Nope, just reboot and paste:```
lsmod | grep -e b43 -e wl
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by kayve on 2015-01-07
I hope I didn't make a boo boo 

[http://paste.ubuntu.com/9690904/](http://paste.ubuntu.com/9690904/)

---

### Post by chili555 on 2015-01-07
> **kayve said:**
> I hope I didn't make a boo boo 

[http://paste.ubuntu.com/9690904/](http://paste.ubuntu.com/9690904/)Now reboot, please.

---

### Post by kayve on 2015-01-07
yeah I have been knowing that wlan0 has been boo booed

[http://paste.ubuntu.com/9691075/](http://paste.ubuntu.com/9691075/)

OK.. just btw... I went back to Starbucks.. I had done what you had said.. I did reboot at least once.. maybe I didn't after the latest install.. the above pastebin I did what you said at Starbucks.. now I am home on ethernet.  I will do what you said again.  I just rebooted.

oh shoot. 

[http://paste.ubuntu.com/9691090/](http://paste.ubuntu.com/9691090/)

I have a feeling I should have rebooted at Starbucks.  Consarnt.

---

### Post by CharlesA on 2015-01-08
The edit button exists for a reason: It is cleaner and easier to follow for those helping you if you edit your previous post instead of making a new post.

Posts merged.

---

### Post by kayve on 2015-01-08
I can't tell you if it is working here, I have to go back to Starbucks but that might not happen until tomorrow.

I'm not sure what to delete right now, I have a feeling it might be fixed, but I promise I will edit tomorrow after I can provide the necessary data to determine whether it is or is not fixed.

it's fixed  Thank you very much.  [http://kayve.net/fixed.png](http://kayve.net/fixed.png)

that was silly of me not to realize I could determine if it was fixed here.

---

### Post by lisati on 2015-01-08
> **kayve said:**
> it's fixed  Thank you very much.  [http://kayve.net/fixed.png](http://kayve.net/fixed.png)

that was silly of me not to realize I could determine if it was fixed here.

I've merged your two posts, the "edit post" button exists for a reason.

 If your problem is fixed, please mark the thread solved using the "Thread tools" menu.

---

### Post by chili555 on 2015-01-08
> root@kayve-VIAO:~# lsmod | grep -e b43 -e wl
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
root@kayve-VIAO:~# iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@kayve-VIAO:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 8C:04:FF:36:97:9B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"HOME-979B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
<snip>Looks awesome! Now can you click the Network Manager icon, see the network you want to connect to, supply the password and connect? [http://www.oulu.fi/it/graphics/nmgui.png](http://www.oulu.fi/it/graphics/nmgui.png)

---

