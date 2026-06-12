---
title: "How to recompile and load my WiFi driver"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by John_Rose on 2013-09-26
[SIZE=2]Hello, I am not a technical specialist, just an ordinary user.
[/SIZE]
I am working under Ubuntu 12.04.3 LTS (kernel 3.2.0-53-generic-pae) on a Dell Vostro 3700 portable.[SIZE=2]
My WiFi chip is Broadcom BCM4313.

My WiFi driver is the open source brcmsmac (also known as brcm80211).

The driver does not recognise channel 13 which is annoying when I try to use the network of a friend who must use this channel on his router.
[/SIZE]
There is a solution at [http://133nux.blogspot.com.es/2011/12/missing-channel-13-this-time-broadcom.html]("http://ubuntuforums.org/133nux.blogspot.com.es/2011/12/missing-channel-13-this-time-broadcom.html") which seems to fix this problem according to several users, but it involves changing a line in source code (file brcmsmac/channel.c), and compiling and reloading the driver. I cannot find the source code for the driver in my system and I don't understand the instructions of Broadcom on how to get and use the source code at [http://wireless.kernel.org/en/users/Drivers/brcm80211]("http://wireless.kernel.org/en/users/Drivers/brcm80211") . Could you please guide me on how to download the driver source code, how to put it in the right place, how to compile the driver after editing the channel.c file, and how to reload load the compiled version?

Thanks and best regards, John[SIZE=2]
[/SIZE][SIZE=3]
[/SIZE]

---

### Post by chili555 on 2013-09-26
First, the link you gave is broken. Second, it was written in 2011 which is about 1913 in Linux years. Third, the copy of /drivers/net/wireless/brcm80211/brcmsmac/channel.c that I have, from compat-wireless, doesn't contain the line referred to at all.

What does this tell us?```
iw reg get
```Does the region correctly reflect your country code from here? [http://en.wikipedia.org/wiki/ISO_3166-1](http://en.wikipedia.org/wiki/ISO_3166-1) If you set it:```
sudo iw reg set GB
```^^ Or whatever your correct country code is, if not my example GB. Then does channel 13 appear?```
sudo iwlist wlan0 chan
```If that helps, we can amend one file and make it persistent.

---

### Post by John_Rose on 2013-09-27
Thanks so much, Tarballs R Us.

Both links I gave work for me, the one with the 2011 advice ([http://133nux.blogspot.com.es/2011/12/missing-channel-13-this-time-broadcom.html](http://133nux.blogspot.com.es/2011/12/missing-channel-13-this-time-broadcom.html)) and the one with official information on the brcmsmac WiFi driver ([http://wireless.kernel.org/en/users/Drivers/brcm80211);](http://wireless.kernel.org/en/users/Drivers/brcm80211);) maybe there was a problem when I transposed them.

I have spent hours on his and tried first of course to make sure that the country code was right. It had already been set for France as confirmed by the running your first command:

john@JOHN-PC:~$ iw reg get
country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS

Here is the result for your third command (second one not needed since coutry code was already set):
john@JOHN-PC:~$ sudo iwlist wlan0 chan
[sudo] password for john: 
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.462 GHz (Channel 11)

Please note that for this command, I was connected to a router working on Channel 11. When I swich this router to Channel 13 Ubuntu no longer sees this access point. For convenience I now have two WiFi routers working, one on Channel 11 and one on Channel 13. My Windows XP on dual boot recoginises and works with both networks without problem. When I am connected to the router working on Channel 11, Channel 13 is seen as per the above results (and the Channel 13 router SSID is recognized in the Ubuntu connections utility), but strangely when I am not connected to the Channel 11 router, the connections utility sees the SSID of the Channel 11 router but NOT the SSID of the Channel 13 router.

It seems pretty clear that Broadcom has not taken into account Channels 12 to 14 in developing their driver, see the explanation on the above-mentioned brcmsmac information page:
"This generation of chips contain additional  regulatory support  independent of the driver. The devices use a single  worldwide  regulatory domain, with channels 12-14 (2.4 GHz band) and  channels  52-64 and 100-140 (5 GHz band) restricted to passive operation.   Transmission on those channels is suppressed until appropriate other   traffic is observed on those channels. Within the driver, we use the   ficticious country code "X2" to represent this worldwide regulatory   domain. There is currently no interface to configure a different domain.   The driver reads the SROM country code from the chip and hands it up  to  mac80211 as the regulatory hint, however this information is  otherwise  unused with the driver."

The 2011 blog link is all that I have been able to find which is potentially useful, and at least two persons have said that it worked at that time (indeed a long time ago). If I understand correctly the brcmsmac driver is integrated in the Ubuntu kernel which is why I cannot find the source code on my machine? I really hope you will be able to help me resolve this, since I am soon leaving for a month to the place where there is only Channel 13, and if it can't work on Ubuntu I will be obliged to work there with Mr. Gates' proprietary OS and later transfer my work to the real thing!

Best regards, John

---

### Post by John_Rose on 2013-09-27
Dear Tarballs R Us,

I would like to add two pieces of information:

1. In fact, I see the Channel 13 router with the Ubuntu connections utilitiy sometimes when I am not connected to a network and sometimes when I am connected to the Channel 11 network, but sometimes in either case I cannot see it. In any case, if it is listed and I ask to connect, it tries for several minutes, then asks me for the password, then tries for several minutes then asking again for the password, not being able to connect. My Channel 13 router is set to WPA (TKIP + AES) - I don't see such detail in the Ubuntu connections utility (It's called 'Connexions réseau" in French), it only gives the choice of WPA or WPA2 personal or WPA or WPA2 enterprise.

2. When I first had this problem I was using the Broadcom proprietary wl driver. I understood from the web that the bcrmsmac driver was just as good for most purposes, and since it is open source I switched to it, but the Channel 13 problem remained.

Hope you will be able to help, thanks and best regards, John

---

### Post by John_Rose on 2013-09-27
Dear Tarballs R Us,

It's me again, just to make sure that it is not a problem of security protocol, I checked under different parameters the router on which I had set Channel 13:
* Channel 11 under WEP: it works
* Channel 11 under WPA (TKIP+AES): it works
* Channel 13 under WEP: it doesn't work
* Channel 13 under WPA (TKIP+AES): it doesn't work (this was the case cited in my original message).
Concerning the router on which I had set Channel 11
* It works under WEP and WPA (TKIP+AES) on Channel 11
* It doesn't work under WPA (TKIP+AES) on Channel 13.

Thus for me it is clear that cannel compatibility is indeed the problem.

---

### Post by chili555 on 2013-09-28
> Thus for me it is clear that cannel compatibility is indeed the problem. I agree.

I have been studying this and Googling for two days. Mrs. Chili just remarked, "Hey, brcmsmac man! We're supposed to be on vacation!" Frankly, I have found no way to trick the currently installed brcmsmac driver to happily use channels 12 and 13. I suggest we try a later brcmsmac version as there does seem to be some evidence that the defect has been addressed and a patch applied. Here, for example: [http://www.gossamer-threads.com/lists/linux/kernel/1532375](http://www.gossamer-threads.com/lists/linux/kernel/1532375)> I am working under Ubuntu 12.04.3 LTS (kernel 3.[COLOR="#FF0000"]2[/COLOR].0-53-generic-pae) Are you sure? I thought 12.04.3 used a 3.[COLOR="#FF0000"]8[/COLOR].0-xx kernel. Confirm:```
uname -r
```

---

### Post by Gyokuro on 2013-09-28
> **chili555 said:**
> I agree.

I have been studying this and Googling for two days. Mrs. Chili just remarked, "Hey, brcmsmac man! We're supposed to be on vacation!" Frankly, I have found no way to trick the currently installed brcmsmac driver to happily use channels 12 and 13. I suggest we try a later brcmsmac version as there does seem to be some evidence that the defect has been addressed and a patch applied. Here, for example: [http://www.gossamer-threads.com/lists/linux/kernel/1532375](http://www.gossamer-threads.com/lists/linux/kernel/1532375)Are you sure? I thought 12.04.3 used a 3.[COLOR=#FF0000]8[/COLOR].0-xx kernel. Confirm:```
uname -r
```

If OP installed precise from the beginning and updated/upgraded his/her output of the kernel release is correct. You have kernel 3.8.XX in case you did a fresh install of 12.04.3 or upgraded from 12.04.2 where the LTS Hardware Enablement Stack got started ([https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)) and updated to 12.04.3 which is using parts of raring.

---

### Post by varunendra on 2013-09-28
> **Gyokuro said:**
> If OP installed precise from the beginning and updated/upgraded his/her output of the kernel release is correct. You have kernel 3.8.XX in case you did a fresh install of 12.04.3 or upgraded from 12.04.2 where the LTS Hardware Enablement Stack got started ([https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)) and updated to 12.04.3 which is using parts of raring.
..and I believe it does get upgraded to 3.8.. but maybe takes many successive update/upgrade cycles. Is my belief correct?
A discussion of that sort [post=12800131]here[/post]

---

### Post by John_Rose on 2013-09-29
Thanks so much all, I'm sure that with your continued advice we can solve this problem. I definitely have kernel version 3.2.0-53-generic-pae:
john@JOHN-PC:~$ uname -r
3.2.0-53-generic-pae

I did not do a clean install of                       Ubuntu 12.04.3 LTS, but rather upgraded from the previous long-term support version Ubuntu 10.04 LTS. In the upgrade utility I have been proposed several upgrades to 3.2.0-xx which I have successively installed, no mention about upgrading beyond version 3.2.0.

The 2011 blog that I cited speaks about a fix for the channel 12 & 13 problem committed to kernel versions "3.0.31, 3.3.4 & 3.2.17", but the announcement for this fix saying "commit badc4f07622f0f7093a201638f45e85765f1b5e4 upstream" ([http://www.serverphorums.com/read.php?12,485400](http://www.serverphorums.com/read.php?12,485400)) says "This patch is to be applied to the stable tree for kernel versions 3.2 and 3.3."   

Thus I went to the Linux Wireless site ([http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases)) and downloaded the tarball for the only stable 3.2 version which is 3.2.5-1 (thus older than 3.2.17 announced above). According to the instructions, I decompressed this in my Desktop and ran:
./scripts/driver-select brcmsmac
make
sudo make install

In the make step I got several errors:
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: erreur: implicit declaration of function &#8216;br_port_exists&#8217; [-Werror=implicit-function-declaration] 
cc1: some warnings being treated as errors 
make[3]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.o] Erreur 1 
make[2]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless] Erreur 2 
make[1]: *** [_module_/home/john/Desktop/compat-wireless-3.2.5-1] Erreur 2 
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-53-generic-pae » 
make: *** [modules] Erreur 2

And at the make install step it said "Your old wireless subsystem modules were left intact:"

Does this give you a basis for some more advice? Best regards, John

---

### Post by varunendra on 2013-09-29
> **John_Rose said:**
> 
In the make step I got several errors:
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: erreur: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration] 
cc1: some warnings being treated as errors 
make[3]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.o] Erreur 1 
make[2]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless] Erreur 2 
make[1]: *** [_module_/home/john/Desktop/compat-wireless-3.2.5-1] Erreur 2 
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-53-generic-pae » 
make: *** [modules] Erreur 2
It maybe helpful if we could see the full output of 'make'. Please try again and post the full output.

While posting the outputs, please use the '**Code**' box to preserves its formatting. It also makes your post cleaner, compact and more readable. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by chili555 on 2013-09-29
I think you'd have much better luck if you install the Ubuntu-ized version of compat-wireless. Please open Synaptic package manager and look for and install linux-backports-modules-[COLOR="#FF0000"]cw[/COLOR]-3.3 or even -3.6 if it's available. Then reboot.

---

### Post by John_Rose on 2013-09-29
Thanks Varun, in the meantime I installed 3.2.0-54-generic-pae, just one of many 3.2.0-xx upgrades since I upgraded to Ubuntu 12.04.3 LTS. It gives no improvement for the Channel 13 problem.

The output of make is below (I put in the BB code tags, but since it is just terminal output so still not so beautiful):
```
john@JOHN-PC:~/Desktop/compat-wireless-3.2.5-1$ make
make -C /lib/modules/3.2.0-54-generic-pae/build M=/home/john/Desktop/compat-wireless-3.2.5-1 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.2.0-54-generic-pae »
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/compat/main.o
  LD [M]  /home/john/Desktop/compat-wireless-3.2.5-1/compat/compat.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/mac80211_if.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/ucode_loader.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/ampdu.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/antsel.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/channel.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/main.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy_shim.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/pmu.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/rate.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/stf.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/aiutils.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_cmn.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_lcn.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_n.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_lcn.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phytbl_n.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/phy/phy_qmath.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/otp.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/srom.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/dma.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/nicpci.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/brcms_trace_events.o
  LD [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmutil/utils.o
  LD [M]  /home/john/Desktop/compat-wireless-3.2.5-1/drivers/net/wireless/brcm80211/brcmutil/brcmutil.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/main.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/status.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/sta_info.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/wep.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/wpa.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/scan.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/offchannel.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/ht.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/agg-tx.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/agg-rx.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/ibss.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mlme.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/work.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/iface.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rate.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/michael.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/tkip.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/aes_ccm.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/aes_cmac.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/cfg.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rx.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/spectmgmt.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/tx.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/key.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/util.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/wme.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/event.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/chan.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/led.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/debugfs.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/debugfs_sta.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/debugfs_netdev.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/debugfs_key.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mesh.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mesh_pathtbl.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mesh_plink.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mesh_hwmp.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/pm.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/driver-trace.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_pid_algo.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_pid_debugfs.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_debugfs.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_ht.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/rc80211_minstrel_ht_debugfs.o
  LD [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/mac80211/mac80211.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/rfkill/rfkill-regulator.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/core.o
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/core.c:7:0: attention : « pr_fmt » redéfini [enabled by default]
include/linux/printk.h:152:0: note: ceci est la localisation d'une précédente définition
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/core.c:7:0: attention : « pr_fmt » redéfini [enabled by default]
include/linux/printk.h:152:0: note: ceci est la localisation d'une précédente définition
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/sysfs.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/radiotap.o
  CC [M]  /home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.o
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: erreur: implicit declaration of function ‘br_port_exists’ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.o] Erreur 1
make[2]: *** [/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless] Erreur 2
make[1]: *** [_module_/home/john/Desktop/compat-wireless-3.2.5-1] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-3.2.0-54-generic-pae »
make: *** [modules] Erreur 2
john@JOHN-PC:~/Desktop/compat-wireless-3.2.5-1$
```

Looking forward to your advice, best regards, John

---

### Post by varunendra on 2013-09-29
> **John_Rose said:**
> 
```

/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c: In function ‘cfg80211_change_iface’:
/home/john/Desktop/compat-wireless-3.2.5-1/net/wireless/util.c:810:2: erreur: [COLOR="#FF0000"]implicit declaration of function ‘br_port_exists’[/COLOR] [-Werror=implicit-function-declaration]
```
Looking forward to your advice, best regards, John
I think dr. chili555 already gave you the best one, and I don't think I'm familiar with above errors. They are obviously related to some undefined functions (expected to be in kernel headers, c libraries, but don't exist in your system), which can often be fixed by commenting them out or defining them in the headers, but doesn't look like it is worth the trouble.

It may take too much effort only to force something which is already incompatible with your kernel. Please try what was suggested above.

---

### Post by John_Rose on 2013-09-30
Dear Ms. Chili (thanks Varan),

I installed the most recent cw backports for version 3.6 (linux-backports-modules-cw-3.6.3.2.0-53-generic) and rebooted. Still my Channel 13 router is not easily visible in the connection utility (usually have to wait a long time), and when I select it it does not log in, asking for password after each three minutes or so.

Here are the results of the commands which you advised in your first reply (while online to my Channel 11 router):
```
john@JOHN-PC:~$ iw reg get
country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS

john@JOHN-PC:~$ sudo iwlist wlan0 chan
[sudo] password for john: 
wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.462 GHz (Channel 11)
```

The backport install gave no errors, but it seems I still have the old 3.2.0-54-generic-pae driver installed (sorry I have the French version so some of the following is in French):```

john@JOHN-PC:~$ sudo lshw -C network
  *-network               
       description: Interface réseau sans fil
       produit: BCM4313 802.11bgn Wireless Network Adapter
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:12:00.0
       nom logique: wlan0
       version: 01
       numéro de série: 5c:ac:4c:aa:53:53
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-54-generic-pae firmware=N/A ip=192.168.0.1 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       ressources: irq:17 mémoire:fb400000-fb403fff
  *-network
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:13:00.0
       nom logique: eth0
       version: 03
       numéro de série: a4:ba:db:dd:d4:7e
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:47 portE/S:d000(taille=256) mémoire:d2c04000-d2c04fff mémoire:d2c00000-d2c03fff mémoire:fb300000-fb31ffff
```

What to do now? Thanks and best regards, John

---

### Post by chili555 on 2013-09-30
I see a couple of interesting things here; first:> ip=192.168.0.1Where did you get that IP address? By DHCP from the router? Usually, 192.168.0.1 *IS* the router! 

Second, I see:> firmware=N/ASome versions of brcmsmac require firmware. Although I wonder if the wireless would even start if it required but lacked firmware, let's do some checking:```
modinfo brcmsmac | grep firm
```My much later version says:> firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fwAnd I have the firmware:```
ls /lib/firmware/brcm
```> bcm43xx-0.fw  bcm43xx_hdr-0.fw  brcmfmac43236b.binIf your modinfo mentions firmware and you do not have it, install it:```
sudo apt-get install linux-firmware
```

---

### Post by John_Rose on 2013-09-30
Hi Ms. Chili,

My Channel 13 router is the modem box provided by my ISP. The gateway is 192.168.0.254. It assigned my machine 192.168.0.1 by DHCP. The Channel 11 router is plugged into a LAN port on the ISP box. It's IP number is set to 192.168.0.227.

I have no firmware:```

john@JOHN-PC:~$ modinfo brcmsmac | grep firm
john@JOHN-PC:~$
```

I thought that brcmsmac does not need any and that brcmfmac does?

My system has been running fine for years on all sorts of WiFi routers as long as the channel is less than 12.

Just to test I unloaded and loaded brcmsmac:```

sudo modprobe -r brcmsmac
sudo modprobe brcmsmac
```

and the lshw command shows that I still have the old 3.2.0-54-generic-pae brcmsmac driver. Is that normal when I backport from a later version?

Still hoping, thanks and best regards, John

---

### Post by chili555 on 2013-10-01
> lshw command shows that I still have the old 3.2.0-54-generic-pae brcmsmac driver. Is that normal when I backport from a later version?Yes. The updated driver version will show up in:```
modinfo brcmsmac
```Here is an example from my machine:> version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94Your version may differ slightly, but it should be apparent you are using a version updated from the default in-kernel driver.

Other than trying the live CD for 13.04 and 13.10, I am afraid I have no other suggestions.

---

### Post by John_Rose on 2013-10-02
Dear Ms. Chili,

My system does not seem to show that the driver is backported from a more recent version:```

john@JOHN-PC:~$ modinfo brcmsmac
filename:       /lib/modules/3.2.0-54-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686
```

If we can conclude that the backporting has not been fully implemented, maybe someone could advise on how to finalise it? If not I guess I am stuck without Channel 13!

Thanks and best regards, John

---

### Post by chili555 on 2013-10-02
Please try, with a working wired ethernet connection:```
sudo apt-get install --reinstall linux-backports-modules-cw-3.6--precise-generic 
```Reboot and report any errors along with:```
modinfo brcmsmac
```

---

### Post by John_Rose on 2013-10-03
Thanks Ms. Chili,

The reinstall command results:```

john@JOHN-PC:~$ sudo apt-get install --reinstall linux-backports-modules-cw-3.6--precise-generic
[sudo] password for john: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet linux-backports-modules-cw-3.6--precise-generic
E: Impossible de trouver de paquet correspondant à l'expression rationnelle « linux-backports-modules-cw-3.6--precise-generic »
```

Translation into English:
Reading the package lists... Done
Construction of the tree of dependences       
Reading status information... Done
E: Impossible to find the package linux-backports-modules-cw-3.6--precise-generic
E: Impossible to find the package corresponding to the rational epxresssion « linux-backports-modules-cw-3.6--precise-generic »[/code]

Seems that there was a problem with the term "precise". Tried with the exact package name linux-backports-modules-cw-3.6.3.2.0-53-generic:```

john@JOHN-PC:~$ sudo apt-get install --reinstall linux-backports-modules-cw-3.6.3.2.0-53-generic
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Note : sélection de linux-backports-modules-cw-3.6-3.2.0-53-generic-pae pour l'expression rationnelle « linux-backports-modules-cw-3.6.3.2.0-53-generic »
Note : sélection de linux-backports-modules-cw-3.6-3.2.0-53-generic pour l'expression rationnelle « linux-backports-modules-cw-3.6.3.2.0-53-generic »
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  thunderbird-globalmenu linux-headers-3.2.0-41-generic-pae
  linux-headers-3.2.0-41 mencoder firefox-globalmenu librhythmbox-core5 dkms
  liblzo2-2 update-manager-kde libqt3-mt linux-headers-3.2.0-41-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les NOUVEAUX paquets suivants seront installés :
  linux-backports-modules-cw-3.6-3.2.0-53-generic-pae
0 mis à jour, 1 nouvellement installés, 1 réinstallés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 2 791 ko/5 576 ko dans les archives.
Après cette opération, 7 952 ko d'espace disque supplémentaires seront utilisés.
Réception de : 1 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.6-3.2.0-53-generic-pae i386 3.2.0-53.41 [2 791 kB]
2 791 ko réceptionnés en 2s (976 ko/s)                                         
(Lecture de la base de données... 583994 fichiers et répertoires déjà installés.)
Préparation du remplacement de linux-backports-modules-cw-3.6-3.2.0-53-generic 3.2.0-53.41 (en utilisant .../linux-backports-modules-cw-3.6-3.2.0-53-generic_3.2.0-53.41_i386.deb) ...
Dépaquetage de la mise à jour de linux-backports-modules-cw-3.6-3.2.0-53-generic ...
Sélection du paquet linux-backports-modules-cw-3.6-3.2.0-53-generic-pae précédemment désélectionné.
Dépaquetage de linux-backports-modules-cw-3.6-3.2.0-53-generic-pae (à partir de .../linux-backports-modules-cw-3.6-3.2.0-53-generic-pae_3.2.0-53.41_i386.deb) ...
Paramétrage de linux-backports-modules-cw-3.6-3.2.0-53-generic (3.2.0-53.41) ...
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic
Paramétrage de linux-backports-modules-cw-3.6-3.2.0-53-generic-pae (3.2.0-53.41) ...
update-initramfs: Generating /boot/initrd.img-3.2.0-53-generic-pae
```

Now rebooting, I'm rebooting will post the rest. Best regards, John

---

### Post by John_Rose on 2013-10-03
Still no access to Channel 13.

No errors on reboot, here is the command output:```

john@JOHN-PC:~$ modinfo brcmsmac
filename:       /lib/modules/3.2.0-54-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686
```

Thanks and best regards, John

---

### Post by chili555 on 2013-10-03
I made a mistake and I apologize. It is supposed to be:```
sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic
```...with only a single hyphen between cw and 3.6. The version doesn't change because you reinstalled the compat package for:> sudo apt-get install --reinstall linux-backports-modules-cw-3.6.3.2.0-[COLOR="#FF0000"]53[/COLOR]-generic...however, your currently running kernel version is:> filename:       /lib/modules/3.2.0-[COLOR="#FF0000"]54[/COLOR]-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.koIn other words, you updated the driver for an older kernel version and not for your newer running kernel version. The installation of the -precice-generic package is supposed to take care of that.

---

### Post by John_Rose on 2013-10-04
Here is the install with precise:```


john@JOHN-PC:~$ sudo apt-get install --reinstall linux-backports-modules-cw-3.6-precise-generic
[sudo] password for john: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  thunderbird-globalmenu linux-headers-3.2.0-41-generic-pae
  linux-headers-3.2.0-41 mencoder firefox-globalmenu librhythmbox-core5 dkms
  liblzo2-2 update-manager-kde libqt3-mt linux-headers-3.2.0-41-generic
Veuillez utiliser « apt-get autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  linux-backports-modules-cw-3.6-3.2.0-54-generic
Les NOUVEAUX paquets suivants seront installés :
  linux-backports-modules-cw-3.6-3.2.0-54-generic
  linux-backports-modules-cw-3.6-precise-generic
0 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 2 790 ko dans les archives.
Après cette opération, 7 977 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? O
Réception de : 1 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.6-3.2.0-54-generic i386 3.2.0-54.42 [2 788 kB]
Réception de : 2 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.6-precise-generic i386 3.2.0.54.64 [2 362 B]
2 790 ko réceptionnés en 2s (956 ko/s)                                   
Sélection du paquet linux-backports-modules-cw-3.6-3.2.0-54-generic précédemment désélectionné.
(Lecture de la base de données... 584121 fichiers et répertoires déjà installés.)
Dépaquetage de linux-backports-modules-cw-3.6-3.2.0-54-generic (à partir de .../linux-backports-modules-cw-3.6-3.2.0-54-generic_3.2.0-54.42_i386.deb) ...
Sélection du paquet linux-backports-modules-cw-3.6-precise-generic précédemment désélectionné.
Dépaquetage de linux-backports-modules-cw-3.6-precise-generic (à partir de .../linux-backports-modules-cw-3.6-precise-generic_3.2.0.54.64_i386.deb) ...
Paramétrage de linux-backports-modules-cw-3.6-3.2.0-54-generic (3.2.0-54.42) ...
update-initramfs: Generating /boot/initrd.img-3.2.0-54-generic
Paramétrage de linux-backports-modules-cw-3.6-precise-generic (3.2.0.54.64) ...
john@JOHN-PC:~$
```

Now rebooting...

---

### Post by John_Rose on 2013-10-04
No errors on reboot, still no Channel 13 access.```

john@JOHN-PC:~$ modinfo brcmsmac
filename:       /lib/modules/3.2.0-54-generic-pae/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     99DF92A40D4267D7A7248E2
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,brcmutil,cfg80211,cordic,crc8
intree:         Y
vermagic:       3.2.0-54-generic-pae SMP mod_unload modversions 686 
john@JOHN-PC:~$ 
```

What do you think? Thanks and best regards, John

---

### Post by chili555 on 2013-10-04
> What do you think? I think I am completely out of any further ideas or suggestions. I regret I couldn't be of more help.

---

### Post by John_Rose on 2013-10-04
OK Ms. Chili, thanks nevertheless for all of your help. I believe that the reference to a fix at [http://kernel.opensuse.org/cgit/kernel/commit/?id=badc4f07622f0f7093a201638f45e85765f1b5e4](http://kernel.opensuse.org/cgit/kernel/commit/?id=badc4f07622f0f7093a201638f45e85765f1b5e4) refers to the openSUSE kernel and not to the Linux kernel, so that there seems to be no trace of others having a Channel 12-13 problem with the brcmsmac WiFi driver under 12.04 LTS. It would be great if you could by reporting this problem to the Ubuntu development team, or by giving me advice on how to do it? Thanks again and best regards, John

---

### Post by varunendra on 2013-10-04
Finding and Reporting bugs is considered as contributing to the software development. Although it can be as simple as opening an account at launchpad --> look if a similar bug has already been reported (add yourself to the list if there is) --> submit your problem with symptoms, system configuration, how to reproduce, and as much details as possible.

For an effective and useful bug report, please take a look at this How To : [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs)

---

### Post by John_Rose on 2013-10-05
Hello, it's me again. I looked again at the 2012 report that the 2011 blog fix worked on my version of the Linux kernal (see [http://www.spinics.net/lists/linux-wireless/msg86303.html](http://www.spinics.net/lists/linux-wireless/msg86303.html) and I think that there must be something to it. Ms. Chili said that she did not have LOCALE_RESTRICTED_SET_2G_SHORT in the channel.c program for brcmsmac, but could you please tell me how to access the source code for my version of brcmsmac? Thanks and best regards, John

---

### Post by varunendra on 2013-10-05
> **John_Rose said:**
> could you please tell me how to access the source code for my version of brcmsmac?
The module brcmsmac is part of the kernel, so you will have to download the whole kernel source code to get it. You can then extract and compile (after desired modifications) the source of only brcmsmac module.

To download the kernel source -
```
apt-get source linux-image-$(uname -r)
```
..which will download the source code as a ".tar.gz" archive in your home directory. To be able to build the binary from this source code, you must also have the headers and dpkg-dev packages installed -
```
sudo apt-get install linux-headers-$(uname -r) dpkg-dev
```

For details on how to download the source and build a single package from it (example of another driver): [http://ubuntuforums.org/showthread.php?t=2173847&p=12802894#post12802894](http://ubuntuforums.org/showthread.php?t=2173847&p=12802894#post12802894)

---

### Post by chili555 on 2013-10-05
> **varunendra said:**
> The module brcmsmac is part of the kernel, so you will have to download the whole kernel source code to get it. You could also, and a lot easier, download, modify and install backports: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2)

The file is at backports-3.11-rc3-1/drivers/net/wireless/brcm80211/brcmsmac/channel.c.> Ms. Chili said that she did not have...She is a he, actually.

---

