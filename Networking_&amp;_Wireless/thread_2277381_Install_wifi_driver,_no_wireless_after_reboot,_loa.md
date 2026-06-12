---
title: "Install wifi driver, no wireless after reboot, load driver module and can't connect"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by diogo9 on 2015-05-08
So i'm running Lubuntu on a macbook pro 13 (2010).

I install the wifi drivers and everything is okay, driver works beautifully.

After rebooting or shutting down the computer the driver won't show any available networks. (There are a ton around here).

So I remove everything using the b43 driver through sudo modprobe -r b43 bcma mac80211 and after a while I do sudo modprobe b43. Everything is okay and the networks show up.

Then when I try to connect the connection fails and when I do dmesg | grep -e wlan0 I get this

```
[ 1328.138624] wlan0: authenticate with cc:d5:39:e3:c3:52[ 1328.164562] wlan0: send auth to cc:d5:39:e3:c3:52 (try 1/3)
[ 1328.167437] wlan0: authenticated
[ 1333.176932] wlan0: authenticate with cc:d5:39:e3:c3:52
[ 1333.177196] wlan0: send auth to cc:d5:39:e3:c3:52 (try 1/3)
[ 1333.179347] wlan0: authenticated
[ 1338.177552] wlan0: aborting authentication with cc:d5:39:e3:c3:52 by local choice (Reason: 3=DEAUTH_LEAVING)
```

And it just does this over and over and over.

My hardware is a broadcom BCM432b (it's based on the BCM4322).

Can anyone help me with this?

Thank you.

---

### Post by Hadaka on 2015-05-08
Hi, let's look at a couple things.please post the output of..
```
lsmod | egrep "wl|b43'
lspci -n | grep 0280
```
thanks.

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> Hi, let's look at a couple things.please post the output of..
```
lsmod | egrep "wl|b43'
lspci -n | grep 0280
```
thanks.

Output of lsmod

```
$ lsmod | egrep "wl|b43"b43                   396480  0 
bcma                   52320  1 b43
mac80211              652718  1 b43
cfg80211              494362  2 b43,mac80211
ssb                    62352  1 b43

```

Output of lspci

```
$ lspci -n | grep 0280
02:00.0 0280: 14e4:432b (rev 01)
```

---

### Post by Hadaka on 2015-05-08
hi, try this
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms bcmwl-kernel-source
```
then do post 11 at this link
[http://ubuntuforums.org/showthread.php?t=2171596&page=2](http://ubuntuforums.org/showthread.php?t=2171596&page=2)
copy and paste one line at a time.
thanks.

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> hi, try this link
[http://ubuntuforums.org/showthread.php?t=2171596&page=2](http://ubuntuforums.org/showthread.php?t=2171596&page=2)
copy and paste one line at a time.
thanks.

Tried it, same issue persists.

Persists even after your edit.

---

### Post by Hadaka on 2015-05-08
Hi,i edited the last post..did you get that additional command?
please repeat the last post then do WITHOUT BOOTING..
```
echo 'b43' | sudo tee -a /etc/modules 
```
thankS

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> Hi,i edited the last post..did you get that additional command?
please repeat the last post then do WITHOUT BOOTING..
```
echo 'b43' | sudo tee -a /etc/modules 
```
thankS

```
$ echo 'b43' | sudo tee -a /etc/modules
b43

```

Problem persists and no networks are shown anymore.

---

### Post by Hadaka on 2015-05-08
ok.let's do this..first..
```
sudo sed -i '/^b43/ d' /etc/modules
```
#sudo sed -i '/^b43/ d' /etc/modules   <-removes b43 from /etc/modules

boot
then..post the "Info Text file" from this post/link
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
chili555'sguide says we should be using the wl driver...however in all my
eperience with aapl boxes it usually ends up being the b43 driver,anyway please
do the above.
thanks.

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> ok.let's do this..first..
```
sudo sed -i '/^b43/ d' /etc/modules
```
#sudo sed -i '/^b43/ d' /etc/modules   <-removes b43 from /etc/modules

boot
then..post the "Info Text file" from this post/link
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
chili555'sguide says we should be using the wl driver...however in all my
eperience with aapl boxes it usually ends up being the b43 driver,anyway please
do the above.
thanks.


```
$ sudo sed -i '/^b43/ d' /etc/modules
$ 
```

No output after this command.
Output of the script in the link you posted -> [ATTACH]261837[/ATTACH]

---

### Post by Hadaka on 2015-05-08
ok..yeah you do have wl loaded..lets yank that rascal
and stuff the b43 in there..please copy and paste..one line at a time

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
boot
report back please

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> ok..yeah you do have wl loaded..lets yank that rascal
and stuff the b43 in there..please copy and paste..one line at a time

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
boot
report back please

I've done as you instructed.

After booting the situation remains.

The network manager indicates that a wireless device exists yet no networks are available for connection.

I've also executed the following commands to see if I could force the networks to be detected:
```
sudo modprobe -r b43
sudo service network-manager restart
sudo modprobe b43
```

The same situation as described above.

---

### Post by Hadaka on 2015-05-08
ok,why is your dns using 10. ?...are you running adhock?
please post the output of..
```
cat /etc/modules
sudo iwlist wlan0 scan
sudo modprobe -rf b43
sudo modprobe -vv b43
dmesg | egrep 'b43|wlan0'
sudo apt get-install iw
```
thanks.

---

### Post by diogo9 on 2015-05-08
> **Hadaka said:**
> ok,why is your dns using 10. ?...are you running adhock?
please post the output of..
```
cat /etc/modules
sudo iwlist wlan0 scan
sudo modprobe -rf b43
sudo modprobe -vv b43
dmesg | egrep 'b43|wlan0'
sudo apt get-install iw
```
thanks.

School network always gives out weird IP addresses.

```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc
$ 

```





```
$ sudo iwlist wlan0 scan
[sudo] password for diogo: 
wlan0     No scan results


$ 

```



```
$ sudo modprobe -rf b43
$ 

```


```
$ sudo modprobe -vv b43
modprobe: INFO: ../libkmod/libkmod.c:354 kmod_set_log_fn() custom logging function 0x7f2b496a6090 registered
insmod /lib/modules/3.16.0-37-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.16.0-37-generic/kernel/net/wireless/cfg80211.ko 
modprobe: INFO: ../libkmod/libkmod-module.c:861 kmod_module_insert_module() Failed to insert module '/lib/modules/3.16.0-37-generic/kernel/net/wireless/cfg80211.ko': File exists
insmod /lib/modules/3.16.0-37-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.16.0-37-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.16.0-37-generic/kernel/drivers/net/wireless/b43/b43.ko 
modprobe: INFO: ../libkmod/libkmod.c:321 kmod_unref() context 0x7f2b4b3c01f0 released
$ 

```



```
$ dmesg | egrep 'b43|wlan0'
[   13.145628] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   13.176207] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   13.176232] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[   22.552084] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   22.768920] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  249.264213] b43-phy0 ERROR: DMA RX reset timed out
[  249.448202] b43-phy0 ERROR: DMA TX reset timed out
[  279.530822] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[  279.564167] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[  279.564194] b43-phy0 warning: 5 GHz band is unsupported on this PHY
[  279.768130] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  280.001262] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
$ 

```



I'm unable to perform the following command as I don't have a ethernet connection available at the moment.

```

sudo apt-get install iw

```

The situation remained the same though.

---

### Post by Hadaka on 2015-05-09
yes it is going to take an internet connect to fix this, when
you do, please post back and run the wireless script again
please.
thanks

---

### Post by diogo9 on 2015-05-09
> **Hadaka said:**
> yes it is going to take an internet connect to fix this, when
you do, please post back and run the wireless script again
please.
thanks

Done as requested.

[ATTACH]261862[/ATTACH]

Thanks.

---

### Post by Hadaka on 2015-05-09
thanks,please do..
```
sudo apt-get install iw
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
if it doesnt connect..please do the info text again
thanks.

---

### Post by diogo9 on 2015-05-10
> **Hadaka said:**
> thanks,please do..
```
sudo apt-get install iw
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
if it doesnt connect..please do the info text again
thanks.

So I've done as you said.

The networks do show up yet I get this message when I try to connect to a network(basically it tries to connect, it does its little animation and then nothing):
```

$ dmesg | grep -e wlan0
[   23.353153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  235.237557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  271.109910] wlan0: authenticate with 00:1d:68:6b:e5:51
[  271.110304] wlan0: send auth to 00:1d:68:6b:e5:51 (try 1/3)
[  271.112170] wlan0: authenticated
[  276.112098] wlan0: aborting authentication with 00:1d:68:6b:e5:51 by local choice (Reason: 3=DEAUTH_LEAVING)
$ 

```

Here is the attachment as requested.
[ATTACH]261881[/ATTACH]

---

### Post by Hadaka on 2015-05-10
Ok,lets clean up a couple things and then go the other way with this.
please copy and paste.
#This sets your country code to PT...europe/Lisbon, it can make a difference
```
sudo apt-get install iw
sudo iw reg set PT
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```
#
```
sudo rm /etc/modprobe.d/blacklist-broadcom-wireless.conf
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
boot
then do.
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
please run the wireless info script and post it
thanks.

---

### Post by diogo9 on 2015-05-10
> **Hadaka said:**
> Ok,lets clean up a couple things and then go the other way with this.
please copy and paste.
#This sets your country code to PT...europe/Lisbon, it can make a difference
```
sudo apt-get install iw
sudo iw reg set PT
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```
#
```
sudo rm /etc/modprobe.d/blacklist-broadcom-wireless.conf
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
boot
then do.
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
please run the wireless info script and post it
thanks.


After doing what you asked wireless connections are available and I'm able to connect to them.
[ATTACH]261886[/ATTACH]


However as soon as I reboot the wireless connections are no longer available and dmesg returns the following errors:
```

diogo@diogo-MacBookPro:~$ dmesg | grep -e wl
[   14.077765] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.084531] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.139159] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   49.026046] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   82.022373] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
diogo@diogo-MacBookPro:~$

```

This is the result of the script following the reboot.
[ATTACH]261887[/ATTACH]

Something confusing is this as it indicates 2 wireless lans which is confusing.
```

diogo@diogo-MacBookPro:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
diogo@diogo-MacBookPro:~$ 

```

---

### Post by Hadaka on 2015-05-10
Hi, ok please do..
```
echo 'wl' | sudo tee -a /etc/modules
```
and boot
now does it connect and stay connect on boot?

---

### Post by diogo9 on 2015-05-10
> **Hadaka said:**
> Hi, ok please do..
```
echo 'wl' | sudo tee -a /etc/modules
```
and boot
now does it connect and stay connect on boot?


No, no networks are available to connect after boot.

It continues to send the scan_results error (-22) when using dmesg | grep -e wlan0

---

### Post by Hadaka on 2015-05-10
ok,  something is odd here..it was running fine on the wl driver..you
booted to see if it would reconnect.,it didnt. so we then injected wl driver on boot up
and it still doesnt connect. dont tell it b43 anything..that has been one of the major 
confusions of this...this broadcom card uses the wl driver..not the b43...so please dont
use that. ok..lets do this..
```
sudo apt-get update
```
post the output of..
```
cat /etc/modules
cat /etc/network/interfaces
cat /etc/rc.local
```
then do.
```
sudo modprobe -rf wl
sudo modprobe -vv wl
dmesg| grep wlan
```
thanks

---

### Post by diogo9 on 2015-05-10
> **Hadaka said:**
> ok,  something is odd here..it was running fine on the wl driver..you
booted to see if it would reconnect.,it didnt. so we then injected wl driver on boot up
and it still doesnt connect. dont tell it b43 anything..that has been one of the major 
confusions of this...this broadcom card uses the wl driver..not the b43...so please dont
use that. ok..lets do this..
```
sudo apt-get update
```
post the output of..
```
cat /etc/modules
cat /etc/network/interfaces
cat /etc/rc.local
```
then do.
```
sudo modprobe -rf wl
sudo modprobe -vv wl
dmesg| grep wlan
```
thanks
Yes it's ridiculous, it works perfectly but as soon as I reboot everything is gone and to get it working again I do a reinstall of the Lubuntu(which is not a solution)

The outputs you requested.
[ATTACH]261890[/ATTACH]
[ATTACH]261891[/ATTACH]
[ATTACH]261892[/ATTACH]

Here is the command line output:
```

$ cat /etc/modules > ModulesOutput.txt
$ cat /etc/network/interfaces > InterfacesOutput.txt
$ cat /etc/rc.local > RCLocalOutput.txt
$ sudo modprobe -rf wl
$ sudo modprobe -vv wl
modprobe: INFO: ../libkmod/libkmod.c:354 kmod_set_log_fn() custom logging function 0x7fc855c64090 registered
insmod /lib/modules/3.16.0-37-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.16.0-37-generic/updates/dkms/wl.ko 
modprobe: INFO: ../libkmod/libkmod.c:321 kmod_unref() context 0x7fc8575171f0 released
$ dmesg | grep wlan
[   13.681893] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   48.020062] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   81.017816] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  124.021730] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  177.017468] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  240.025615] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  247.034092] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  270.025769] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  303.021954] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  346.021687] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  399.021939] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  462.021759] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  525.021540] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  588.021850] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  651.021698] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  714.021810] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  777.021689] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  840.028131] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  903.021606] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  966.017527] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1029.021673] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1092.025936] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1155.021677] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1218.021720] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1281.021845] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1344.026184] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1407.021800] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1470.021690] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1533.021562] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1596.026234] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1659.021814] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1722.025542] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1785.021513] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1848.025698] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1911.022437] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1974.021608] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2037.021580] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2100.021697] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2163.021674] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2226.025751] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2289.021534] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2352.021594] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2415.021880] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2478.037725] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2541.021931] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2604.024077] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 2638.929175] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[ 2639.921672] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
$ 

```

---

### Post by Hadaka on 2015-05-10
see if this makes it work untill boot
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe wl
```
if it connects..please run the wieless script and post
thanks.

---

### Post by diogo9 on 2015-05-11
> **Hadaka said:**
> see if this makes it work untill boot
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo modprobe -rf wl
sudo modprobe wl
```
if it connects..please run the wieless script and post
thanks.

Did as asked.

No connections show up., nothing is available when scanning for networks.
```

$ iwlist wlan0 scan
wlan0     No scan results


$ 

```

---

### Post by Hadaka on 2015-05-11
is it possible for you to change the router setting from TKIP to wpa2-aes
if so please do. also I ask my good friend chili555 to take a look at this and he
suggests..
you do a fresh reboot , then do,```
dmesg > wifi.txt
```
THEN
paste the contents of the file ...wifi.txt to paste.ubuntu.com

---

