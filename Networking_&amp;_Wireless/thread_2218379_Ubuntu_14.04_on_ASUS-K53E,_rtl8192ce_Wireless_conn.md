---
title: "Ubuntu 14.04 on ASUS-K53E, rtl8192ce: Wireless connection issue"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by velcro205 on 2014-04-20
Hi! I recently changed from Windows 7 to Ubuntu 12.04 and had some troubles with my wireless card. Now I have upgraded to Ubuntu 14.04, and the issues persist. When I'm using my Laptop, the wifi connection seems to be stable, but after a brief period of time the connection it's lost. The problem aparently It's caused by the wireless driver, rtl8192ce, but I don't know anything about. Hope you could help me, and thanks!!!

---

### Post by CitadelUniversal on 2014-04-20
Have you followed this guide but with your Realtek wireless driver version for Linux - [http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver) - It is very useful and works for me....

---

### Post by velcro205 on 2014-04-20
Thank! I'll give it a try and let you know if it worked for me...

---

### Post by Hadaka on 2014-04-20
Hi, give this a try....
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```
* This is a temp. fix, good to the first boot.Let
it run for awhile..if it helps then do.
```
echo "options rtl8192ce swenc=1" | sudo tee /etc/modprobe.d/rtl8192ce.conf

```
thanks.

---

### Post by velcro205 on 2014-04-20
> **CitadelUniversal said:**
> Have you followed this guide but with your Realtek wireless driver version for Linux - [http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver](http://askubuntu.com/questions/342076/step-by-step-ubuntu-12-04-install-of-realtek-rtl8188ce-driver) - It is very useful and works for me....

Hey! I've tried what you told me, but anything worked out. I followed the steps of the thread, but at the point of use the make command, it shows me this output:

**make**
```
bersayder@bersayder-K53E:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ make
make -C /lib/modules/3.13.0-24-generic/build M=/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
  CC [M]  /home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
 int __devinit rtl_pci_probe(struct pci_dev *pdev,
               ^
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_action_proc’:
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:885:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.freq = hw->conf.channel->center_freq;
                                ^
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:886:32: error: ‘struct ieee80211_conf’ has no member named ‘channel’
       rx_status.band = hw->conf.channel->band;
                                ^
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c: In function ‘rtl_send_smps_action’:
/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:1451:24: error: ‘struct ieee80211_conf’ has no member named ‘channel’
   info->band = hw->conf.channel->band;
                        ^
make[2]: *** [/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/home/bersayder/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
make: *** [all] Error 2
bersayder@bersayder-K53E:~/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013$ 



```

So, I don't know what to do, I'm a little lost at this point, Why does it fail? did I do something wrong?

Thanks for your patience!

---

### Post by velcro205 on 2014-04-20
Hey Hadaka, I also did what you said, but it kept my wireless card trying to connect my modem without success.

---

### Post by CitadelUniversal on 2014-04-22
Please have a look at [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10) & [http://ubuntuforums.org/showthread.php?t=2196520](http://ubuntuforums.org/showthread.php?t=2196520) the instructions in those may help your wireless problems.

---

### Post by velcro205 on 2014-04-22
> **CitadelUniversal said:**
> Please have a look at [http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10) & [http://ubuntuforums.org/showthread.php?t=2196520](http://ubuntuforums.org/showthread.php?t=2196520) the instructions in those may help your wireless problems.

Thanks CytadelUniversal!!! I've followed the answer of the first Link ([http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10](http://askubuntu.com/questions/367587/unable-to-compile-realtek-rtl8188ce-driver-on-ubuntu-13-10)) and did a manual installation as specified in GitHub, so my problem seems to be solved. In case of having troubles, I'll let you know. Thanks for everything, guys !!! :p

---

### Post by martinyt on 2014-05-08
Hello
I have a similar problem. I tried the git-hub solution, but that did not work for me - I could not connect. Now, after an uninstall, my ASUS-PCE-N15 (with the rtl8192ce chipset) does not work at all. And I do not understand why. The Asus-driver does not seem to support ubuntu and I was not able to install it.

All help is mostly appreciated

Martin

---

