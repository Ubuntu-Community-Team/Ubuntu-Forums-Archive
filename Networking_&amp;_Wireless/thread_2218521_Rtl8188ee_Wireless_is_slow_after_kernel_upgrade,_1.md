---
title: "Rtl8188ee: Wireless is slow after kernel upgrade, 14.04"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by bshatt1987 on 2014-04-21
Hi guys.  By ridiculous I mean that it's gotten really, really slow.  It was fine with the last kernel that was used in the beta (kernel 3.13.0-23-generic) but when the actual release date came I ran 
```
sudo apt-get dist-upgrade
``` and it installed the latest kernel (3.13.0-24-generic) and that's when the wireless problems started.
I had troubles with my wireless before and did this, which was suggested in a post I made on the issue before
```
   sudo modprobe -rv rtl8188ee
 sudo modprobe -v rtl8188ee swenc=1 ips=0 fwlps=0
 echo "options rtl8188ee swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8188ee.conf
 
```
That seemed to fix things up until the kernel upgrade that was performed.
Upon boot, at the grub menu, I can choose the former kernel and the wifi seems to work but when I boot with the new kernel it's just...so slow.  Videos are out of the question and it has trouble even loading text based forum sites, like Reddit, in a reasonable amount of time.  Any thoughts, anyone?  Should I just keep using the earlier kernel version?


Edit - Also, I've tried reinstalling the driver for my card, [using these instructions]("http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver") but I get an error when I try to do the "make" command.
Errors that occur:
```
make
make -C /lib/modules/3.13.0-24-generic/build M=/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.o
/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.c: In function ‘rtl_action_proc’:
/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.c:885:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.c:886:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.c: In function ‘rtl_send_smps_action’:
/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.c:1451:24: error: ‘struct ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched/base.o] Error 1
make[1]: *** [_module_/home/ben/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [all] Error 2
ben@ben-laptop:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patched$
```


Also, what's the difference between rtl8188ee and rtl8188ce?  I'm coming upon a lot of similar issues in my searching for answers but they've all got to do with rtl8188ce, whereas mine is 8188ee.

---

### Post by SLaCK3r on 2014-04-21
Hey man, I had the exact same issue with the exact same card. I downgraded to 12.04LTS and everything works perfectly now. I think the downgrade is worth it to save you frustration for a problem that doesn't seem to be resolved in this new OS version.

---

### Post by bshatt1987 on 2014-04-21
Alright, I'll keep that in mind, thanks.  For now I'm just using the previous kernel and it seems to be working pretty well.  These Realtek cards are a joke, though, right?  I'd rather have a Broadcom, despite how much trouble my old one caused me.  At least once it was working it didn't flake out like these Realtek pieces.

---

