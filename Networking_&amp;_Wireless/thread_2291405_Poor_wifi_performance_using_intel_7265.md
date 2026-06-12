---
title: "Poor wifi performance using intel 7265"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by villindesign on 2015-08-19
I have a Intel NUC with a Intel 7265 Wireless card. Ever other computer in my house is 50+Mbps on speedtest,net, but this NUC running Ubuntu 15.04 gets less than 4Mbps. I reviewed and followed some of the steps at an older thread ([http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265](http://ubuntuforums.org/showthread.php?t=2261834&highlight=intel+7265)), but since there appears to be newer firmware, i am unsure if I should try all of those methods. I did try adding 

```
[COLOR=#000000]options iwlwifi 11n_disable=8[/COLOR]
```
[COLOR=#000000]And
```
options iwlwifi 11n_disable=1
```[/COLOR]
to the end of ```
[FONT=Ubuntu Mono][COLOR=#000000]/etc/modprobe.d/iwlwifi.conf[/COLOR][/FONT]
```[FONT=Ubuntu Mono][COLOR=#000000] However, no improvement occurred. Is there any updated information on improving the performance of this wireless card? Thanks
Britt[/COLOR][/FONT]

---

### Post by chili555 on 2015-08-21
I hope you don't have both 11n_disable=1 and =8 in the file. Can you please check?```
cat /etc/modprobe.d/iwlwifi.conf
```If there are both, we'll need to remove one. I suggest that, for now, =8 remain.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

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

---

### Post by villindesign on 2015-08-21
I've tried both, but not at the same time :)

currently

```
 britt@britt-desktop:~$ cat /etc/modprobe.d/iwlwifi.conf# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
#added myself
options iwlwifi 11n_disable=8
 
```
My router is an apple airport extreme which severely limits configuration options. Currently, the wireless security is WPA2 Personal and not any WEP/WPA mixed mode security. There are two bands, a 2.4 GHz and a 5GHz. The intel 7265 is connected to the 5GHz at the moment, but my problems occur on both bands. The 2.4 GHZ band is set to channel 1, and the 5GHz band is set to channel 36. They were both set to auto before. This router does not have the ability to turn off a particular speed as far as i know, and is capable of 802.11a/b/g/n/ac speeds. It has 80MHZ wide channels. I am using the airport utility to configure it on a macbook. 

Looks I am set for the US:
```
britt@britt-desktop:~$ sudo iw reg get
[sudo] password for britt: 
country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)



```

I set the Network Manager to ignore IPv6 and will reboot to test. I've also noticed that only the download speed seems to be slower; the upload is as expected.Thanks for the assistance.

PS. Iceland is a wonderful place. I've been there in the summer and winter and would love to live there permanently :)

---

### Post by chili555 on 2015-08-21
> **villindesign said:**
> 

PS. Iceland is a wonderful place. I've been there in the summer and winter and would love to live there permanently :)It is indeed! I have only been there as a tourist but plan to return as soon as I can. I only use IS in my example because it is pretty neutral; no-one doesn't like Iceland!>  Currently, the wireless security is WPA2 Personal and not any WEP/WPA mixed mode security. WPA2-AES (preferred) or WPA2-TKIP (to be avoided)?

---

### Post by villindesign on 2015-08-21
So after a reboot, on the 2.4GHz band I was at 5.5 Mbps down and 11.5 up.

On the 5GHz, i was at 41Mbps down and 12 up! Hopefully that continues. I pay for 50 down and 10 up. Other machines on the network are getting > 80 down and around 12 up. I am using kernel 4.0.0-040000-generic atm also. But can boot into 3.19 if you think that would help.

---

### Post by chili555 on 2015-08-21
I think the later kernel has the best chance of success. 

Which firmware version is loading?```
sudo lshw -C network
```It will be shown something like this:```
*-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: xx:94:6b:99:55:xx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.0.1-040001-generic [COLOR="#FF0000"]firmware=9.221.4.1[/COLOR] build 25532 ip=10.255.16.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:27 memory:f2400000-f2401fff

```Which firmware files do you have on your system?```
ls /lib/firmware | grep 7265
```For comparison, I have:```
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-13.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode
iwlwifi-7265D-13.ucode

```

---

### Post by villindesign on 2015-08-21
```
  *-network       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 59
       serial: 34:13:e8:39:1f:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.0.0-040000-generic[COLOR=#ff0000] firmware=25.17.12.0[/COLOR] ip=10.0.1.29 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn



```

And available firmwares:
```
~$ ls /lib/firmware/ | grep 7265
iwlwifi-7265-10.ucode
iwlwifi-7265-12.ucode
iwlwifi-7265-13.ucode
iwlwifi-7265-8.ucode
iwlwifi-7265-9.ucode
iwlwifi-7265D-10.ucode
iwlwifi-7265D-12.ucode
iwlwifi-7265D-13.ucode



```

I am getting dropped connections and unable to reconnect until reboot.

---

### Post by chili555 on 2015-08-21
> firmware=25.17.[COLOR="#FF0000"]12[/COLOR].0I believe that corresponds to:```
iwlwifi-7265-[COLOR="#FF0000"]12[/COLOR].ucode
```You have newer firmware versions on hand, however, the version of iwlwifi in use in kernel version 4.0.0-xx calls up and uses -12. I am not sure if a later kernel version would use -13 or not. 

What about?> WPA2-AES (preferred) or WPA2-TKIP (to be avoided)Are the different encryption methods available and selectable in the Airport? I hope so as TKIP is not only less secure but also tricky for many Linux drivers.

---

### Post by villindesign on 2015-08-21
The Airport Extreme uses WPA2-AES, so no problems there. According to [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi),  kernal 3.19 uses [iwlwifi-7260-ucode-25.17.12.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.17.12.0.tgz"), and kernel 4.1 uses [iwlwifi-7260-ucode-25.30.13.0.tgz]("https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.30.13.0.tgz"). Still having issues with the wifi though. So, I suppose i have the correct firmware (25.17.12.0).

---

### Post by ajaxian on 2016-07-27
Per this thread: [http://askubuntu.com/questions/583574/intel-dual-band-wireless-7265-dropping-connection/803452#803452](http://askubuntu.com/questions/583574/intel-dual-band-wireless-7265-dropping-connection/803452#803452)

And from reading chili's helpful advice, I was able to **upgrade** my firmware to the latest version by downloading it from git and dropping it in /lib/firmware, which fixed the disconnects, and made my speeds ~100x faster (now only 25x slower than the rate I pay for!)

Copy-pasting due to general laziness:

Wheeee!  After a couple hours putzing around on the Internet, I found a solution that works for 7260/7265 with even newer firmware for 7265**D** devices.


Per the official driver page: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi)


> 7260 and 7265 will not be supported by the newest firmware versions:
> the last firmware that was released for these devices is -17.ucode.
> Bug fixes will be ported to -17.ucode. Note that 7265D can run later
> firmware versions. In order to determine if your 7265 device is a 'D'
> version, you can check the dmesg output:
> 
> Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210 The revision
> number of a 7265D device is 0x210, if you see any other number, you
> have a 7265 device.


So, I ran `dmesg | grep Wireless` and saw I did have device code 0x210.


As such, I was able to use [https://github.com/OpenELEC/iwlwifi-firmware/blob/master/firmware/iwlwifi-7265D-21.ucode](https://github.com/OpenELEC/iwlwifi-firmware/blob/master/firmware/iwlwifi-7265D-21.ucode)


**If you do not have a 7265D per the dmesg command above, instead use: ** [https://github.com/OpenELEC/iwlwifi-firmware/blob/master/firmware/iwlwifi-7265D-17.ucode](https://github.com/OpenELEC/iwlwifi-firmware/blob/master/firmware/iwlwifi-7265D-17.ucode)


Next, I had a look in /lib/firmware, and noticed that I only had the -16.ucode file.  So, I went to the git repo, downloaded the file from git, then used: 
`sudo cp ~/Downloads/iwlwifi-726* /lib/firmware`
restarted my wifi, and actually got a usable connection!


Note that I tried both `11n_disable=8` and `11n_disable=1` (tried each one separately) to no avail.  With this updated firmware, I was able to remove these workarounds.

---

### Post by ajaxian on 2016-07-27
Note that this requires, I believe, a kernel version > 4.3 to work.

---

### Post by truongcan on 2017-02-07
> **ajaxian said:**
> Note that this requires, I believe, a kernel version > 4.3 to work.

A kernel 4.4.0, not working :(

---

