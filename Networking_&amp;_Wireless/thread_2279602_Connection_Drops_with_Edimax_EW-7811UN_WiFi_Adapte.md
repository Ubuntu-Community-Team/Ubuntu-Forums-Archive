---
title: "Connection Drops with Edimax EW-7811UN WiFi Adapter on Ubuntu 14.04.2 Kernel 3.16"
date: 2015-05-24
forum: Networking &amp; Wireless
---

### Post by Geniusberry on 2015-05-24
Hello everybody,

I've experienced quite the difficulties today trying to get the Edimax EW-7811Un WiFi Adapter to work in Ubuntu 14.04.2, despite the Linux support it advertised. I've attached the results from the sticky thread's wifi diagnostics script.[ATTACH]262191[/ATTACH]
 Based on some Googling I've done and random troubleshooting, I've already tried:
[LIST]
[*]Installing a bunch of wifi drivers over ethernet (no luck)
[*]Getting the 3.16 kernel by upgrading to Ubuntu 14.04.2 (opensource drivers still broken)
[*]Installing the driver from the [edimax website]("http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n150/ew-7811un") (it fails to install with errors)
[*]Trying this[ AskUbuntu]("http://askubuntu.com/questions/505969/errors-installing-wireless-driver") post and hand editing the driver (same as above)
[*]Blacklisting the default drivers and trying [pvaret's]("https://github.com/pvaret/rtl8192cu-fixes") fixed 8192cu drivers (it installs and the new driver loads, but the performance of the driver is as bad as the default kernel driver, with a connection drop in seconds)
[*]Trying out what [this blog post]("http://0n35.com/conquering-edimax-ew-7811un-drivers-on-ubuntu-14-04/") recommends and uninstalling pvaret's driver and running [dz0ny's fix]("https://github.com/dz0ny/rt8192cu") (same as the above)
[/LIST]
Throughout all of this, I'm confronted with the same issue, as the wifi will work for a few moments, right to 2 mb downloaded, then the signal will drop to 100 bytes down, while nm-applet shows full strength. I've tested this WiFi adapter on a Mac, and it works fine, with it only having issues in Ubuntu. Any suggestions? Here's what iwconfig shows:
 ```
##### iwconfig ##########################

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Yadav"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Yadav' [AC2]>   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=76/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
And lsusb:

```
##### lsusb #############################
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 04f3:0234 Elan Microelectronics Corp. 
Bus 004 Device 002: ID 05b8:3279 Agiler, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wi
reless Adapter [Realtek RTL8188CUS]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Any help is appreciated and thanks in advance!

---

### Post by chili555 on 2015-05-24
According to* wireless_info*, you are connected to:> Cell 02 - Address: <MAC 'Yadav' [AC2]>
                    ESSID:"Yadav"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:270 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=98/100  Signal level=75/100  There are a few things I see that may be problematic for most Linux wireless drivers.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot. Is connectivity improved?

---

### Post by Geniusberry on 2015-05-24
Hey Chili555, thanks for the quick reply! I tried as many of your suggestions as I could, by disabling IPv6, setting a country code for the US and changing my router settings to WPA2 AES only. I wasn't able to change to N only, as I don't think my router supports it. However, after rebooting unfortunately my situation with the WiFi adapter did not change much, though now it jumps to 700 bytes a second before dropping to 0 in system monitor. Any other things I should try?

---

### Post by chili555 on 2015-05-24
>  I wasn't able to change to N only,My recommendation was:> be certain the router is*** not ***set to use N speeds only; auto B, G and N is preferred.Let's have a look at some diagnostics:```
modinfo 8192cu | grep -i version
lsmod | grep 8192
dmesg | grep -e 8192cu -e wlan 
```Thanks.

---

### Post by Geniusberry on 2015-05-25
Oops, sorry. I meant to say that I wasn't able to change the channel width to 20 mhz only in N mode, since I couldn't find the settings for it. Anyway, for [COLOR=#000000][FONT=Ubuntu Mono]modinfo 8192cu | grep -i version[/FONT][/COLOR] I got 
```

version:        v4.0.2_9000.20130911
srcversion:     98913FB8609F2F16E0996C2
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
parm:           rtw_chip_version:int

```
For [COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep 8192 [/FONT][/COLOR]I got
```

8192cu                628527  0 

```
And for [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep -e 8192cu -e wlan [/FONT][/COLOR]I got
```

[   11.705825] 8192cu: module verification failed: signature and/or  required key missing - tainting kernel
[   11.707114] rtl8192cu driver version=v4.0.2_9000.20130911
[   11.859515] usbcore: registered new interface driver rtl8192cu
[   15.385520] rtl8192cu_hal_init in 548ms
[   15.399219] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.407655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.217312] survey done event(13) band:0 for wlan0
[   17.518878] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.267227] survey done event(8) band:0 for wlan0
[   83.222558] survey done event(d) band:0 for wlan0
[  146.179318] survey done event(15) band:0 for wlan0
[  229.089565] survey done event(b) band:0 for wlan0
[  332.508330] survey done event(e) band:0 for wlan0
[  451.876237] survey done event(16) band:0 for wlan0
[  571.763585] survey done event(11) band:0 for wlan0
[  691.650940] survey done event(7) band:0 for wlan0
[  811.538291] survey done event(10) band:0 for wlan0
[  931.425647] survey done event(f) band:0 for wlan0
[ 1051.313001] survey done event(d) band:0 for wlan0
[ 1132.672533] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 80 ms
[ 1171.204351] survey done event(11) band:0 for wlan0
[ 1291.103692] survey done event(a) band:0 for wlan0
[ 1413.057340] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 1056 ms
[ 1413.057349] survey done event(b) band:0 for wlan0
[ 1531.381987] survey done event(8) band:0 for wlan0
[ 1652.827918] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 1056 ms
[ 1652.827927] survey done event(a) band:0 for wlan0
[ 1677.296814] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 128 ms
[ 1709.330971] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 128 ms
[ 1770.641122] survey done event(8) band:0 for wlan0
[ 1890.524359] survey done event(11) band:0 for wlan0
[ 2010.415957] survey done event(b) band:0 for wlan0
[ 2130.319034] survey done event(12) band:0 for wlan0
[ 2250.190667] survey done event(13) band:0 for wlan0
[ 2370.074018] survey done event(b) band:0 for wlan0
[ 2396.009592] issue_probereq_ex(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 80 ms
[ 2396.093383] issue_nulldata(wlan0) to 00:1d:d4:d8:a4:e0, ch:11, 3/3 in 84 ms

```

I see that there seems to be some sort of module issue. Should I switch back to the default or pvaret module, or stay with dz0ny's?


[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---

### Post by chili555 on 2015-05-25
I think I'd try this instead: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)  Note that it has been updated a few days ago.

If you need guidance, I'll be happy to help. At the least, as a part of the process, you will need to remove the blacklist for rtl8192cu and add one for 8192cu.

---

### Post by Geniusberry on 2015-05-25
So, just to be crystal clear, I should compile and install lwfinger's version of the drivers from github, and blacklist the 8192cu driver I'm using right now, and unblacklist the default driver that came with the kernel? Won't there be conflicts with the kernel driver? Thanks again!

---

### Post by chili555 on 2015-05-25
> I should compile and install lwfinger's version of the drivers from github, and blacklist the 8192cu driver I'm using right now, and unblacklist the default driver that came with the kernel? Exactly!> Won't there be conflicts with the kernel driver? No; when you sudo make install the lwfinger version, it will become the new default. You should then reboot and let us see again:```
dmesg | grep rtl
```Is the device plugged in to a USB2 port or USB3? I looked at a case a few days ago where the USB2 port supplied not quite enough power for the device to work correctly.

---

### Post by Geniusberry on 2015-05-25
So, I compiled, installed, blacklisted the old driver and unblacklisted the default driver and rebooted ... to find my system wouldn't boot. 10 panicked boots later, I've found that I can't boot with the WiFi adapter plugged in anymore, and plugging it in after boot results in a system freeze and the CPU fans ramping up to full blast. I'm thinking I should do a make uninstall for the driver right about now?

---

### Post by chili555 on 2015-05-25
Let's see if we can see any clues as to what went wrong:```
cat /var/log/kern.log.1  > wifi.txt
cat /var/log/kern.log  >> wifi.txt
cat wifi.txt | grep -e wlan -e 8192  >  wifi2.txt
```Find the file wifi2.txt and paste it here: [http://paste.ubuntu.com](http://paste.ubuntu.com)  Give me the link in your reply.

You do have 8192cu blacklisted, is that correct? And rtl8192cu is not?

If those blacklists are correct, sudo make uninstall and we'll try to see what went off the tracks.

---

### Post by Geniusberry on 2015-05-25
Yes, I double checked and 8192cu is blacklisted, and I deleted the line in blacklist.conf that blacklisted the rtl8192cu drivers. Here is the link to the info you requested with the wifi adapter unplugged: [http://paste.ubuntu.com/11357039/](http://paste.ubuntu.com/11357039/) 
I also did make uninstall, which completed without errors.

---

### Post by chili555 on 2015-05-25
The driver is certainly verbose, giving all sorts of information that don't appear to be errors. Some of the informational messages are the ones you posted previously above. It appears to me that the last boot with the device inserted yielded:> May 25 14:59:48 hallinux kernel: [   13.214830] Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
May 25 14:59:48 hallinux kernel: [   13.261560] usbcore: registered new interface driver rtl8192cu
May 25 14:59:50 hallinux kernel: [   16.936851] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not readyWe see no errors or other distress.

May I see:```
ls /etc/modprobe.d
cat /etc/modules
```We may need to remove the dkms parts. may we see:```
history | grep dkms
```

---

### Post by Geniusberry on 2015-05-25
For ls modprobe.d I got:
```

alsa-base.conf              blacklist-oss.conf           iwlwifi.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf  mlx4.conf
blacklist.conf              blacklist-watchdog.conf      modesetting.conf
blacklist-firewire.conf     dkms.conf                    vmwgfx-fbdev.conf
blacklist-framebuffer.conf  fbdev-blacklist.conf
blacklist-modem.conf        fglrx-core.conf

```
And for cat /etc/modules I got:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc

```
And for history | grep dkms I get
```

 sudo apt-get update && sudo apt-get install git build-essential linux-headers-generic dkms
   10  sudo make dkms
   95  sudo make dkms
   96  sudo dkms remove 8192cu-4.0.29
   97  sudo dkms remove 8192cu-4.0.29 --all
   98  sudo dkms remove 8192cu/4.0.29 --all
  100  sudo make dkms
  128  sudo aptitude install linux-headers-generic build-essential dkms git
  131  sudo dkms remove 8192cu/4.0.29 --all
  132  sudo dkms add ./rtl8192cu-fixes
  133  sudo dkms install 8192cu/1.10
  143  sudo dkms remove 8192cu/4.0.29 --all
  144  sudo dkms add ./rtl8192cu-fixes
  145  sudo dkms remove 8192cu/1.10 --all
  149  sudo dkms add ./rtl819cu-fixes
  151  sudo dkms add ./rtl8192cu-fixes
  152  sudo dkms install 8192cu/1.10
  163  sudo dkms remove 8192cu/1.10 --all
  165  sudo dkms add ./rtl8192cu-fixes
  166  sudo dkms install 8192cu/1.10
  168  sudo dkms install 8192cu/1.10
  169  sudo dkms remove 8192cu/1.10 --all
  170  sudo dkms add ./rtl8192cu-fixes
  171  sudo dkms install 8192cu/1.10
  180  sudo apt-get update && sudo apt-get install git build-essential linux-headers-generic dkms
  184  sudo dkms remove 8192cu/1.10 --all
  198  sudo make dkms
  255  sudo dkms --help
  256  sudo dkms remove 8192cu/1.10 --all
  258  sudo dkms remove 8192cu/4.0.029 --all
  259  dkms status
  260  sudo dkms remove 8192cu/4.0.29 --all
  545  sudo dkms status
  553  nano dkms.conf 
  579  sudo apt-get install git linux-headers-generic build-essential dkms
  585  sudo dkms status
  586  sudo dkms add ./rtl8192cu-fixes
  587  sudo dkms install 8192cu/1.10
  601  nano dkms.conf 
  617  sudo dkms status
  618  sudo dkms remove 8192cu/1.10 --all
  631  sudo apt-get update && sudo apt-get install git build-essential linux-headers-generic dkms
  638  chmod +x dkms-8192cu.install 
  640  ./dkms-8192cu.install 
  641  nano dkms-8192cu.install 
  647  git clone https://github.com/vincent-t/rt8192cu_dkms.git
  649  cd rt8192cu_dkms/
  657  sudo make install_dkms 8192cu
  661  cd rt8192cu_dkms/
  664  sudo make uninstall_dkms 8192cu
  666  sudo dkms status
  675  rm -r rt8192cu_dkms/
  681  sudo make dkms
  855  history | grep dkms

```
Before I asked my question here, I tried building drivers with dkms for both pvaret and dz0ny several times. I tried to clean up the dkms tree as best I could after each attempt, and now dkms status only shows the fglrx drivers and the dz0ny drivers, but there might be some cruft there still.

---

### Post by chili555 on 2015-05-26
> now dkms status only shows the fglrx drivers and the dz0ny drivers, but there might be some cruft there still. I suggest you remove the dz0ny drivers via dkms. Then look at /etc/modprobe.d/dkms.conf. If there is anything there related to rtl8192cu or 8192cu, remove it. Then, reboot with the device removed. I assume it boots normally. Open a terminal and do:```
tail -f /var/log/syslog
```Watch the terminal and insert the device. You should see the USB bus recognize the device and load the driver rtl8192cu and its dependencies including cfg80211. Ideally, there is no crash or kernel panic, etc. Get out of *tail* with Ctrl+c.

Then, I suggest you reboot with the device inserted. We suspect the boot issue is solved.

If so, I'd compile the lwfinger suite again and reboot.

---

### Post by Geniusberry on 2015-05-26
Okay, so I removed the old dz0ny drivers, and it booted perfectly fine. There was nothing in dkms.conf and the uninstall was error free. Tail also showed that my wifi adapter was being recognized when I plugged it in, and there were no crashes or anything. But after sudo make install with lwfinger's drivers and a reboot, the system froze again. After removing the adapter, it boots fine, though trying to plug it in will also result in a total freeze. Should I uninstall the lwfinger drivers, or is there something I should do with them?

---

### Post by chili555 on 2015-05-26
Were there errors or significant warnings at 'make'? There are four branches of the package and we might try others. What is your exact kernel version? ```
uname -r
```I think I have 3.16.0-something here and I'll experiment.

I'd sudo make uninstall for now.

---

### Post by Geniusberry on 2015-05-27
Nope, during make there was nothing out of the ordinary, just an end message saying it was successful and exiting. My exact kernel version according to uname -r is kernel version 3.16.0-38-generic, and it is up to date. An interesting thing happened as I was removing the driver folder after the make uninstall: for some reason, all the driver files were write protected, and I had to use sudo to remove them, unlike the last time I installed and then uninstalled and deleted the drivers.

---

### Post by chili555 on 2015-05-28
>  as I was removing the driver folder after the make uninstall: for some reason, all the driver files were write protected, and I had to use sudo to remove themThat's a normal consequence of invoking 'sudo make' instead of 'make.' Either is generally acceptable, however, if you sudo made the bits and pieces, you then need to sudo get rid of them!

I am mistified as to why your system crashes with rtlwifi_new. Many here and on askubuntu have built it and solved their issues successfully. I really hesitate to test further as it is a tiny bit risky to forcibly reboot your computer because it's locked up. I wouldn't want the responsibility for damaging, in any way, someone's installation. If, however, you want to take the risk, I'd suggest:

* Compile and install rtlwifi-new with make clean, make and sudo make install;

* Reboot without the device inserted;

* Open a terminal and run:```
cat /var/log/syslog
```

* Make note of the ending timestamp. Here is a sample from my machine:```
May 28 10:17:01 T410 CRON[17149]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```The last entry, in my case, was at 10:17:01.

* Insert the device and let it crash. Wait a few moments for the system to settle. Remove the device;

* Reboot;

* In a terminal:```
less /var/log/syslog
```* Use the arrow keys and PageUp and PageDn keys to scroll back and forth to see and paste into a text document the lines just after the timestamp you noted to see what went wrong. Post them.

If you'd as soon take no further risk, we'll try to see how we can get the in-kernel rtl8192cu to work better.

---

### Post by Geniusberry on 2015-05-30
Sorry for the delay, I just haven't had much time to mess with the system. So, I decided to go with the first route and mess with lwfinger's drivers some more, and as I was preparing to install them, I got a kernel update, so now I'm on 3.16.0-39-generic. I entered the commands you said, and like always, the install went fine, and after the reboot and inserting the wifi adapter the system froze exactly like before. I took note to find the exact lines after putting the adapter in, and the results are at [http://paste.ubuntu.com/11461328/](http://paste.ubuntu.com/11461328/) 
I didn't go through all of it, but a lot of it seems to just be a part of the reboot process. Any suggestions?

---

### Post by chili555 on 2015-05-31
If you recall or wrote down the timestamp, check for the same in /var/log/syslog.1. I see nothing significant in the log you posted.

I see that the ethernet was attached and then connected, please conduct further tests with it detached.

---

### Post by Geniusberry on 2015-06-01
So I re-did the little experiment with the ethernet unplugged, and the resulting log is at [http://paste.ubuntu.com/11506395/](http://paste.ubuntu.com/11506395/)
It's weird though, in that when I tried to open the file up in gedit, it gave an error message saying that it had invalid characters. Less as well as Emacs show the same thing, a bunch of black unreadable characters, so I think the file might possibly be corrupted. It doesn't look like lwfinger's drivers are going too well. Any ideas for where to go next?

---

### Post by chili555 on 2015-06-01
> when I tried to open the file up in gedit, it gave an error message saying that it had invalid characters. Which file? The dmesg you just pasted?

Studying...

EDIT: Was the device ever inserted? I see no driver or other sign of it. I do see:```
Jun  1 17:38:14 hallinux kernel: [    0.284327] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284400] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284475] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284541] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284595] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284638] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284680] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
Jun  1 17:38:14 hallinux kernel: [    0.284723] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
```Are the IRQs set to auto-select in the BIOS? I'd probably try it if not now set.

---

### Post by Geniusberry on 2015-06-02
The syslog file from /var/log/syslog was the one with the weird characters, and yes, the one I just posted. I'm 100% sure that the device was inserted, and that the posted log lines are the ones from right before I inserted the device to after I rebooted and then copied all of it. What do you mean by IRQ's? I haven't looked through the BIOS yet, but I'm willing it take a shot at it.

---

### Post by chili555 on 2015-06-02
Here is a screen capture from a BIOS setup page. Although it is different from yours, I am pretty confident that you'll find a similar page. As you can see, the IRQs are set to auto select. Also, in some cases, previously reluctant wireless devices work better when the BIOS is reset to defaults.

[http://en.wikipedia.org/wiki/Interrupt_request_%28PC_architecture%29](http://en.wikipedia.org/wiki/Interrupt_request_%28PC_architecture%29)

---

### Post by Geniusberry on 2015-06-03
I reset the BIOS to default, but I can't seem to directly find the IRQ settings in my BIOS. The closest I could find was a hardware settings page with subsections on auto connecting PCI, PCI E, and other hardware, all of the settings which were set to auto, except for PS 2 port 60 and 64 emulation, which I doubt is the right setting. Still no luck when I inserted the driver however. At this point I'm about out of ideas with lwfinger's drivers. Any suggestions?

---

### Post by chili555 on 2015-06-03
i regret that I have no other suggestions. Sorry.

---

### Post by Geniusberry on 2015-06-03
Earlier you mentioned something about making the default drivers work better for me. Is there anything that can be done in that avenue? I've also been looking up using ndiswrapper, and was wondering if it could be applicable in this case, as the adapter does have working Windows drivers, and apparently works with Windows XP, which is supposed to be the supported operating system drivers in ndiswrapper. At this point I'm split between just using Windows with this adapter, which I'm going to install anyway, throwing the adapter away, or trying a reinstall with just pure Ubuntu and crossing my fingers that the WiFi fixes will work. Thanks for all your help so far!

---

### Post by chili555 on 2015-06-04
There is but one meaningful driver parameter available in the in-kernel rtl8192cu:```
$ modinfo rtl8192cu
filename:       /lib/modules/4.0.1-040001-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
<snip>
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       4.0.1-040001-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        58:EF:1B:E8:6F:69:F6:97:25:C1:20:58:C9:00:5C:68:4C:A0:4C:FB
sig_hashalgo:   sha512
[COLOR="#FF0000"]parm:           swenc:Set to 1 for software crypto (default 0) (bool)[/COLOR]
parm:           debug:Set debug level (0-5) (default 0) (int)

```We may as well try it:```
sudo -i
echo "options rtl8192cu swenc=1"  >>  /etc/modprobe.d/rtl8192cu.conf
exit
```Reboot. Any improvement?> throwing the adapter awayNow we're getting somewhere! 

ndiswrapper is an option and requires XP drivers, usually .inf and .sys, appropriate to your architecture; either 32- or 64-bit.

---

### Post by Geniusberry on 2015-06-07
I changed the option like you said, and unfortunately, no luck. However, now even without lwfinger's drivers installed, my system will just freeze up whenever I plug the adapter in. I'm curious about trying out ndiswrapper, but I'm not sure what to do with the in kernel drivers right now. Any suggestions?

---

### Post by chili555 on 2015-06-07
> However, now even without lwfinger's drivers installed, my system will just freeze up whenever I plug the adapter in. Something else is horribly wrong then. Generally, the rt28xx suite of drivers is reliable if sometimes tricky to get and stay connected. I have never before now heard of a case where the whole computer simply locked up! Unfortunately, we haven't yet been able to see any sign of the lock-up in the logs. Until we do, we are powerless to troubleshoot it. I suggested a method in a post above, however, the logs you retrieved yielded nothing remarkable.

Do you have an earlier kernel available at the GRUB menu upon booting? Is the behavior the same with any kernel?

---

