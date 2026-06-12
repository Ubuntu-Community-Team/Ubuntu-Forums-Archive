---
title: "Belkin F9L 1108-TG"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by michaelenda372 on 2014-08-06
I have tried both this solution:

[http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576](http://ubuntuforums.org/showthread.php?t=2153777&p=12688576#post12688576)

and this one: 

[http://ubuntuforums.org/showthread.php?t=2221847](http://ubuntuforums.org/showthread.php?t=2221847)

**_First solution_**
For the first solution everything was going fine until I ran the "make" command on the fold where I got this whole thing.

make[1]: Entering directory `/usr/src/linux-headers-3.13.0-32-generic'
  CC [M]  /home/michael/rtl8192du/os_dep/ioctl_cfg80211.o
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: ‘struct cfg80211_mgmt_tx_params’ declared inside parameter list [enabled by default]
     u64 *cookie)
     ^
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c: In function ‘cfg80211_rtw_mgmt_tx’:
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
  size_t len = params->len;
                     ^
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
  struct ieee80211_channel *chan = params->chan;
                                         ^
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
  const u8 *buf = params->buf;
                        ^
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c: At top level:
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
  .mgmt_tx = cfg80211_rtw_mgmt_tx,
  ^
/home/michael/rtl8192du/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for ‘rtw_cfg80211_ops.mgmt_tx’) [enabled by default]
make[2]: *** [/home/michael/rtl8192du/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/michael/rtl8192du] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-32-generic'
make: *** [modules] Error 2

Now I have no idea what to do.

**_Second solution_**
This one never seemed to do anything. I ran the line of code and ran the script but nothing happened, not sure if I'm just not doing it right or what.

Any help would be appreciated.

---

### Post by chili555 on 2014-08-07
Please check here: [http://askubuntu.com/questions/507309/belkin-wireless-usb-f9l1101v2-incompatible-w-14-04/507352#507352](http://askubuntu.com/questions/507309/belkin-wireless-usb-f9l1101v2-incompatible-w-14-04/507352#507352)

---

### Post by michaelenda372 on 2014-08-07
Thanks, that worked perfectly.

---

### Post by chili555 on 2014-08-07
> **michaelenda372 said:**
> Thanks, that worked perfectly.Awesome! Don't forget this part:> When a newer kernel version, also known as linux-image, is installed by Update Manager, you will need to re-compile:
Code:
cd rtl8192du[COLOR="#FF0000"]-kernel-version[/COLOR]
make clean
make
sudo make install
sudo modprobe 8192duSince you are using a slightly different version, I've amended as noted.

---

### Post by michaelenda372 on 2014-09-14
Hello again. I had some issues with my computer and had to re-install everything, and instead of going with ubuntu 14.04 I chose to install Elementary OS (which is based of of ubuntu 12.04) just to mix things up. Turns out I mixed things up to much. I followed every step that worked on my ubuntu14.04 install but I get the error.

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-54-generic/build M=/home/michael/rtl8192du-kernel-version  modulesmake: *** /lib/modules/3.5.0-54-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I know that its not strictly ubuntu and would understand if it just doesn't work but if anyone can help it would be great.

---

### Post by chili555 on 2014-09-14
> **michaelenda372 said:**
> Hello again. I had some issues with my computer and had to re-install everything, and instead of going with ubuntu 14.04 I chose to install Elementary OS (which is based of of ubuntu 12.04) just to mix things up. Turns out I mixed things up to much. I followed every step that worked on my ubuntu14.04 install but I get the error.

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-54-generic/build M=/home/michael/rtl8192du-kernel-version  modulesmake: *** /lib/modules/3.5.0-54-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

I know that its not strictly ubuntu and would understand if it just doesn't work but if anyone can help it would be great.The error suggests you need to install linux-headers-generic and try again.

---

### Post by michaelenda372 on 2014-09-14
I ran ```
sudo apt-get install linux-headers-generic
``` and my computer said I have the newest version installed.

---

### Post by chili555 on 2014-09-14
Ah! OK, now I think I finally see it. You tried to compile *kernel-version* which is for newer kernels. I think you need this instead: [https://github.com/lwfinger/rtl8192du/archive/master.zip](https://github.com/lwfinger/rtl8192du/archive/master.zip) It is for older kernels.

---

### Post by michaelenda372 on 2014-09-14
I downloaded the older kernel support and the error message changed slightly.

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.5.0-54-generic/build M=/home/michael/rtl8192du-master  modulesmake: *** /lib/modules/3.5.0-54-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

---

### Post by chili555 on 2014-09-14
Sorry; I will be off for the evening.

---

### Post by michaelenda372 on 2014-09-15
another update, I got passed the problem but now when I try to run the "make" command I get this huge thing.

```

make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.2.0-68-generic-pae/build M=/home/michael/rtl8192du-master  modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-68-generic-pae'
  CC [M]  /home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.o
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_assoc&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:2444:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:2444:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_indicate_sta_disassoc&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:2501:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:2501:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action_p2p&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3165:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3165:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_p2p_action_public&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3197:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3197:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;rtw_cfg80211_rx_action&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3232:2: warning: passing argument 4 of &#8216;cfg80211_rx_mgmt&#8217; makes integer from pointer without a cast [enabled by default]
include/net/cfg80211.h:3135:6: note: expected &#8216;size_t&#8217; but argument is of type &#8216;u8 *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3232:2: error: too many arguments to function &#8216;cfg80211_rx_mgmt&#8217;
include/net/cfg80211.h:3135:6: note: declared here
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: At top level:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3556:5: warning: &#8216;struct cfg80211_mgmt_tx_params&#8217; declared inside parameter list [enabled by default]
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3556:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: In function &#8216;cfg80211_rtw_mgmt_tx&#8217;:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3567:21: error: dereferencing pointer to incomplete type
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3568:41: error: dereferencing pointer to incomplete type
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3569:24: error: dereferencing pointer to incomplete type
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3584:5: warning: passing argument 1 of &#8216;cfg80211_mgmt_tx_status&#8217; from incompatible pointer type [enabled by default]
include/net/cfg80211.h:3151:6: note: expected &#8216;struct net_device *&#8217; but argument is of type &#8216;struct wireless_dev *&#8217;
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c: At top level:
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3650:2: warning: initialization from incompatible pointer type [enabled by default]
/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.c:3650:2: warning: (near initialization for &#8216;rtw_cfg80211_ops.mgmt_tx&#8217;) [enabled by default]
make[2]: *** [/home/michael/rtl8192du-master/os_dep/ioctl_cfg80211.o] Error 1
make[1]: *** [_module_/home/michael/rtl8192du-master] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-68-generic-pae'
make: *** [modules] Error 2

```

---

### Post by chili555 on 2014-09-15
Ole Chili is corn-fused...again, it seems. At the outset of your thread, you said:> make ARCH=i386 CROSS_COMPILE= -C /lib/modules/[COLOR="#FF0000"]3.5.0-54[/COLOR]-genericBut now you say:> make ARCH=i386 CROSS_COMPILE= -C /lib/modules/[COLOR="#FF0000"]3.2.0-68-generic-pae[/COLOR]/build Which kernel version are you booted into? Are you sure you have linux-headers installed for the currently running kernel?? I'm pretty sure you do not:```
uname -r
sudo dpkg -s linux-headers-`uname -r`
```

---

