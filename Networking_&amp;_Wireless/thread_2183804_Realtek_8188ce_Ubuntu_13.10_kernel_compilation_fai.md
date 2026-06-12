---
title: "Realtek 8188ce Ubuntu 13.10 kernel compilation fails"
date: 2013-10-26
forum: Networking &amp; Wireless
---

### Post by ramonoliveira on 2013-10-26
Hi everyone, I'm facing some problems to compile the realtek RTL8188CE drivers to ubuntu 13.10. I've read a lot of articles surfing the web and just found that there are some macros that has been removed in kernel 3.11. Unfortunately I can't use wifi because is dropping every 5 minutes and very slow. Does anybody knows if there is a solution for compiling this driver?

Thanks in advance.

---

### Post by chili555 on 2013-10-26
I think the answer is modifying the pci.h file. Check here: [http://askubuntu.com/questions/354439/problems-with-attempting-to-install-drivers-ubuntu-12-04-realtek/354522](http://askubuntu.com/questions/354439/problems-with-attempting-to-install-drivers-ubuntu-12-04-realtek/354522)

---

### Post by olle.personne on 2013-10-26
I still get this error after editing the pci.h file so there is something still wrong here.

```
make -C /lib/modules/3.11.0-12-generic/build M=/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
       rx_status.band = hw->conf.channel->band;
                                ^
/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function &#8216;rtl_send_smps_action&#8217;:
/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: &#8216;struct ieee80211_conf&#8217; has no member named &#8216;channel&#8217;
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/****/Downloads/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [all] Error 2
```

---

### Post by chili555 on 2013-10-26
May we see the first 20 or so lines of the pci.h file? Please paste them here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by olle.personne on 2013-10-26
Here you go!

[http://paste.ubuntu.com/6308889/](http://paste.ubuntu.com/6308889/)

---

### Post by chili555 on 2013-10-26
Hmmm. It won't compile for me either. 

The only other method I know is this: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) I just compiled it without error or warning on my 13.10 system. However, this is the same driver as already exists in the 3.11 kernel, so I doubt it helps you any. 

What about the in-kernel rtl8188ee isn't working as expected, prompting you to try to compile, in the first case, an *older* version?

---

### Post by ramonoliveira on 2013-10-27
The driver that comes in kernel 3.11 is unstable, the connection is dropping everytime. I use here in my apartment the wifi provided by the univeristy, so the protocol that they use is different. Is something with PEAP and MSCHAPV2 with username and pass. So what do you think that I should do now?

Best regards

---

### Post by olle.personne on 2013-10-27
> **chili555 said:**
> Hmmm. It won't compile for me either. 

The only other method I know is this: [http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281](http://askubuntu.com/questions/337785/wireless-not-working-on-toshiba-satellite-c55-a5281) I just compiled it without error or warning on my 13.10 system. However, this is the same driver as already exists in the 3.11 kernel, so I doubt it helps you any. 

What about the in-kernel rtl8188ee isn't working as expected, prompting you to try to compile, in the first case, an *older* version?

Using the instructions provided in the link you posted, I managed to get my wireless working again! Can't tell yet if it's working better than before but at least it's working :)

Thank you!

---

### Post by chili555 on 2013-10-27
> **ramonoliveira said:**
> The driver that comes in kernel 3.11 is unstable, the connection is dropping everytime. I use here in my apartment the wifi provided by the univeristy, so the protocol that they use is different. Is something with PEAP and MSCHAPV2 with username and pass. So what do you think that I should do now?

Best regardsI assume you set up PEAP in Network Manager.

There are a few things that we can do and one thing we cannot do. First, does this reflect your correct country code and not a blank?```
dmesg | grep CRDA
```Here is mine as an example:> cfg80211: Calling CRDA for country: [COLOR="#FF0000"]US[/COLOR]If it's incorrect, we can fix it.

Second, what does this say about power management?```
iwconfig
```Does this temporary parameter help?```
sudo modprobe -r rtl8188ee
sudo modprobe rtl8188ee ips=0
```The thing we can't help is hinted at at github: [https://github.com/tianon/linux-rtlwifi-8188ce](https://github.com/tianon/linux-rtlwifi-8188ce)> note that this driver is really no better or worse than the one directly in-kernel, since the driver can't fix horrid hardware.Now I don't know if the hardware is horrid or not. I do know that I answer more questions about Realtek than all others combined.

---

### Post by bb1netusaf2004 on 2013-10-28
The driver compilation is failing because of some kernel headers that have changed.  This time the change was deeper than before.  There were some structs that changed and other that were added to replace some that were removed.  Regardless, after several days of work I have a working, compiling driver available here:

[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

There are some compile warnings that will pop up, but they don't affect the driver.  I'll fix the warnings when I get around to it, but for now the driver has been used and works on Ubuntu 13.10. 

And for the record, this driver is MUCH better than the flaky, crappy one that comes with Ubuntu, regardless what anyone says.  My laptop is actually usable now! :-D

EDIT:

If you're curious about the specific changes, I detailed them here on Ask Ubuntu:  [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588)

---

### Post by ramonoliveira on 2013-11-03
> **bb1netusaf2004 said:**
> The driver compilation is failing because of some kernel headers that have changed.  This time the change was deeper than before.  There were some structs that changed and other that were added to replace some that were removed.  Regardless, after several days of work I have a working, compiling driver available here:

[https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)

There are some compile warnings that will pop up, but they don't affect the driver.  I'll fix the warnings when I get around to it, but for now the driver has been used and works on Ubuntu 13.10. 

And for the record, this driver is MUCH better than the flaky, crappy one that comes with Ubuntu, regardless what anyone says.  My laptop is actually usable now! :-D

EDIT:

If you're curious about the specific changes, I detailed them here on Ask Ubuntu:  [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10/367588#367588)

Hi my friend. Thank you for sharing with us this version of driver. In fact the warnings appeared in my screen, but I am not quite sure if it really worked for me. I used the "make" and "make install" commands in terminal to do it. The wifi is still slow. What do you think that I should do now?


Thanks in advance

---

