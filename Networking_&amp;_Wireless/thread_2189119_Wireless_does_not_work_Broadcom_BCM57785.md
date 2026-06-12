---
title: "Wireless does not work Broadcom BCM57785"
date: 2013-11-20
forum: Networking &amp; Wireless
---

### Post by ximenacardinali on 2013-11-20
Hello, I have a notebook Acer Aspire E1-531 with a Broadcom Card  BCM57785, and today after some upgrades which I don't remember what it  was and a reboot, the computer lost all wireless connection. Even though  I can connect on a wired connection.

Here is some info:

[LIST]
[*]Distribution; Ubuntu 12.04 LTS
[*]Kernel Version: 3.2.0-56-generic
[*]iwconfig does not show wireless interfaces
[*]The module tg3 is loaded
[*]rfkill does not throw any output
[*]I have installed: bcmwl-kernel-source
[/LIST]
   
Attached is the output of all commands!

I will really appreciate if someone can give me hand on this. I'm realy stuck and I have tried thousand things already!

---

### Post by chili555 on 2013-11-20
Your data only includes Broadcom Corporation NetLink BCM57785 Gigabit *Ethernet* PCIe which is, as the name implies, an ethernet card, not wireless. Please show us:```
lspci -nn | grep 0280
```

---

### Post by ximenacardinali on 2013-11-20
Sorry about that! Here is the output:

```
lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
```

---

### Post by chili555 on 2013-11-20
Ahhh! A controversial device to get going. We may have some tweaking to do. Let's start with:```
sudo modprobe wl
dmesg | grep wl
iwconfig
```

---

### Post by ximenacardinali on 2013-11-20
hehe Don't tell me about it! It's eating my brain!

Here is the output:
```
root@magnets:~# modprobe wl
root@magnets:~# dmesg | grep wl
[   21.731586] wl: module license 'MIXED/Proprietary' taints kernel.
 [   21.736682] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.736691] wl 0000:03:00.0: setting latency timer to 64
[   21.774905] INFO @wl_cfg80211_attach : Registered CFG80211 phy
root@magnets:~# iwconfig 
 lo        no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
           Encryption key:off
          Power Management:off[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]


          
eth0      no wireless extensions.

root@magnets:~#
```

---

### Post by chili555 on 2013-11-20
Looks pretty normal so far; let's dig deeper:```
rfkill list all
sudo iwlist eth1 scan
```Running as root, are we? Tsk, tsk!

---

### Post by ximenacardinali on 2013-11-20
hehe, you're right :P

Here:

```
volkan@magnets:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: brcmwl-0: Wireless LAN
     Soft blocked: yes
    Hard blocked: no
volkan@magnets:~$ sudo iwlist eth1 scan
[sudo] password for volkan: 
eth1      Interface doesn't support scanning : Network is down

volkan@magnets:~$
```

---

### Post by chili555 on 2013-11-20
Please try:```
sudo rfkill unblock all
sudo iwlist eth1 scan
```

---

### Post by ximenacardinali on 2013-11-23
Hello There, sorry for the delay.

I did what you told me and also, I downloaded the "official" driver from the broadcom page: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and I ran the following commands:

1. Remove the following modules:
```
rmmod b43
rmmod brcmsmac
rmmod ssb
rmmod bcma
rmmod wl
```

2. Then, I added them to the Blacklist:
```
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf  
```

3. Install the following modules and the driver:
```
modprobe lib80211 
modprobe cfg80211
insmod wl.ko
```

4. Then I added them to /etc/modules:
```
echo "lib80211" >> /etc/modules
echo "cfg80211" >> /etc/modules
echo "wl.ko" >> /etc/modules
```

Then, I had to "Enable Wireless" on the Network Manager, and the wifi start working.
I ran the scan that you told me, and the output is attached,
[ATTACH]248029[/ATTACH]


 But now, I have a really annoying problem: The wifi connection cuts  every now and then, and it's really getting me mad. I'm always doing  something on the web and suddenly the connection cuts, and it's kind of  happening more often than I would like. Any ideas of what can be the  problem?

---

### Post by chili555 on 2013-11-23
> 4. Then I added them to /etc/modules:
Code:

echo "lib80211" >> /etc/modules
echo "cfg80211" >> /etc/modules
echo "wl.ko" >> /etc/modules

First,the terminology is wl and not wl.ko. Second, I hope you don't actually have quotation marks around these, they are not needed. Check:```
cat /etc/modules
``` Last, please run:```
modinfo wl | grep depends
```Is cfg80211 a dependency of wl? Is it a dependency of lib80211? I don't know for sure because I haven't compiled the downloaded version. I doubt it is the superior of the Ubuntu version available in the repositories. Time will tell.

Depending on your findings, I suggest you adjust /etc/modules and reboot.

---

### Post by ximenacardinali on 2013-11-24
Hello there, here is the output:

```
volkan@magnets:~$  cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
wl
cfg80211
lib80211
volkan@magnets:~$ modinfo wl | grep depends
depends:        cfg80211,lib80211
volkan@magnets:~$ 

```

I reboot the laptop, wireless is working, but still cutting the connection every now and then. Sometimes is really impossible to surf on the Internet, or work on something.

---

### Post by ximenacardinali on 2013-11-24
Also, this is another peculiar thing:

```
volkan@magnets:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:89:84:62:c3:cb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.133d firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: f4:b7:e2:b3:36:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.2.103 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:c0500000-c0503fff
volkan@magnets:~$ 
```

Why the Wireless interface is shown as "eth1"? Can that be a problem?

---

### Post by chili555 on 2013-11-24
The interface created by the Broadcom STA driver is eth1, so there is no problem there. > product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: f4:b7:e2:b3:36:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) [COLOR="#FF0000"]ip=192.168.2.103[/COLOR]You are connected as expected, but we need to see why it drops:```
cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20
```Please run and post this right after a drop.

---

### Post by ximenacardinali on 2013-11-24
I just got an Interruption for around 20 seconds on the network, and I got not a single error on the Syslog :S

Even though, here are some errors that happened around 2 hours before:

```
Nov 24 15:31:23 magnets NetworkManager[859]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 24 15:31:23 magnets NetworkManager[859]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Nov 24 15:31:24 magnets NetworkManager[859]: <info> (eth1): writing resolv.conf to /sbin/resolvconf
Nov 24 15:31:24 magnets NetworkManager[859]: <info> (eth1): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 24 15:31:24 magnets NetworkManager[859]: <info> Policy set 'Cerens' (eth1) as default for IPv4 routing and DNS.
Nov 24 15:31:24 magnets NetworkManager[859]: <info> Activation (eth1) successful, device activated.
Nov 24 15:31:24 magnets NetworkManager[859]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Nov 24 15:31:24 magnets NetworkManager[859]:    keyfile: updating /etc/NetworkManager/system-connections/Cerens
Nov 24 15:31:44 magnets NetworkManager[859]: <info> (eth1): IP6 addrconf timed out or failed.
Nov 24 15:31:44 magnets NetworkManager[859]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 24 15:31:44 magnets NetworkManager[859]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 24 15:31:44 magnets NetworkManager[859]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 24 15:54:35 magnets kernel: [17679.109698] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Nov 24 15:54:35 magnets kernel: [17679.109711] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Nov 24 15:54:35 magnets kernel: [17679.109727] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Nov 24 15:54:35 magnets kernel: [17679.109733] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Nov 24 15:54:35 magnets kernel: [17679.109747] ERROR @wl_dev_intvar_get : error (-1)
Nov 24 15:54:35 magnets kernel: [17679.109752] ERROR @wl_cfg80211_get_tx_power : error (-1)
```

I will still keeping an eye on the syslog!

---

### Post by chili555 on 2013-11-24
> Nov 24 15:54:35 magnets kernel: [17679.109698] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Nov 24 15:54:35 magnets kernel: [17679.109711] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Nov 24 15:54:35 magnets kernel: [17679.109727] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Nov 24 15:54:35 magnets kernel: [17679.109733] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Nov 24 15:54:35 magnets kernel: [17679.109747] ERROR @wl_dev_intvar_get : error (-1)
Nov 24 15:54:35 magnets kernel: [17679.109752] ERROR @wl_cfg80211_get_tx_power : error (-1)This driver and card combination are not happy together. Would you care to try something different?

---

### Post by ximenacardinali on 2013-11-24
Sorry, something different like what? I'm really stuck in here :S

---

### Post by chili555 on 2013-11-24
You are stuck because your device, 14e4:4727 is quite tricky to get going properly. With each newer Ubuntu version and each newer STA driver version, it seems to get trickier! 

You seem to be pretty adept, so, unless you need additional guidance, I'll leave the exact details to you. I suggest you temporarily change /etc/modules to:```
lp
rtc
#wl
#cfg80211
#lib80211
brcmsmac
bcma
```Temporarily change your blacklist file to amend the parts you added as follows:```
blacklist ssb
#blacklist bcma
blacklist b43
#blacklist brcmsmac
blacklist wl
```Then look for any other blacklist files:```
ls /etc/modprobe.d
```If you see any bcm-whatever, let me know its contents and we'll proceed.

Reboot.

This has the effect of using brcmsmac instead of wl, the STA driver. Let's see if the driver and card work and play well together.

---

### Post by ximenacardinali on 2013-11-24
Well, I did what you told me. Wireless connection is working, and I will let you know if I experience any "cuts" on the connection. 
Funny thing, the wireless interface that before was seen as eth1 now is seen correctly as wlan0:

```
volkan@magnets:/etc/modprobe.d$ iwconfig 
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Cerens"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 84:9C:A6:48:97:60   
          Bit Rate=21.7 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:218  Invalid misc:97   Missed beacon:0

eth0      no wireless extensions.

volkan@magnets:/etc/modprobe.d$ 
```

And these are the outputs:

Syslog:
```
volkan@magnets:~$ cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20
Nov 24 19:59:59 magnets NetworkManager[837]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 24 20:00:00 magnets NetworkManager[837]: <info> Policy set 'Cerens' (wlan0) as default for IPv4 routing and DNS.
Nov 24 20:00:00 magnets NetworkManager[837]: <info> Activation (wlan0) successful, device activated.
Nov 24 20:00:00 magnets NetworkManager[837]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 24 20:00:00 magnets NetworkManager[837]: <warn> dnsmasq appeared on DBus: :1.34
Nov 24 20:00:00 magnets NetworkManager[837]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 24 20:00:14 magnets ntpd[3002]: Listen normally on 3 wlan0 192.168.2.103 UDP 123
Nov 24 20:00:14 magnets ntpd[3002]: Listen normally on 4 wlan0 fe80::f6b7:e2ff:feb3:3622 UDP 123
Nov 24 20:00:18 magnets NetworkManager[837]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 24 20:00:18 magnets NetworkManager[837]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 24 20:00:18 magnets NetworkManager[837]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 24 20:00:18 magnets NetworkManager[837]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 24 20:06:56 magnets kernel: [  444.874978] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:8241 brcms_c_wait_for_tx_completion+0x99/0xb0 [brcmsmac]()
Nov 24 20:06:56 magnets kernel: [  444.874989] Modules linked in: bnep rfcomm parport_pc ppdev bluetooth binfmt_misc joydev snd_hda_codec_hdmi snd_hda_codec_realtek bcma arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo videodev v4l2_compat_ioctl32 snd serio_raw soundcore snd_page_alloc mei(C) mac_hid brcmsmac mac80211 brcmutil cfg80211 crc8 cordic lp parport usbhid hid wmi i915 drm_kms_helper drm sdhci_pci sdhci i2c_algo_bit video tg3(O)
Nov 24 20:06:56 magnets kernel: [  444.875169]  [<ffffffffa01b338f>] ieee80211_start_sw_scan+0x7f/0x1c0 [mac80211]
Nov 24 20:06:56 magnets kernel: [  444.875241]  [<ffffffffa01b3745>] __ieee80211_start_scan+0x275/0x2a0 [mac80211]
Nov 24 20:06:56 magnets kernel: [  444.875264]  [<ffffffffa018d4a1>] ? nl80211_trigger_scan+0x101/0x620 [cfg80211]
Nov 24 20:06:56 magnets kernel: [  444.875289]  [<ffffffffa01b4029>] ieee80211_request_scan+0x39/0x60 [mac80211]
Nov 24 20:06:56 magnets kernel: [  444.875319]  [<ffffffffa01c4e6c>] ieee80211_scan+0x6c/0x90 [mac80211]
Nov 24 20:06:56 magnets kernel: [  444.875339]  [<ffffffffa018d708>] nl80211_trigger_scan+0x368/0x620 [cfg80211]
volkan@magnets:~$ 
```

Modules:
```
volkan@magnets:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
#wl
#cfg80211
#lib80211
brcmsmac
bcma
volkan@magnets:~$ 
```

Blacklists:
```
volkan@magnets:/etc/modprobe.d$ cat broadcom-sta-common.conf
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
#blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
volkan@magnets:/etc/modprobe.d$ 
```

```
volkan@magnets:/etc/modprobe.d$ cat blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
#blacklist bcma
volkan@magnets:/etc/modprobe.d$ 
```

```
volkan@magnets:/etc/modprobe.d$ cat blacklist.conf
...
blacklist amd76x_edac
blacklist acer_wmi
blacklist ssb
#blacklist bcma
blacklist b43
#blacklist brcmsmac
volkan@magnets:/etc/modprobe.d$ 
```

I will be waiting any further instructions from you and I will let you know how everything keeps working on this other side.

---

### Post by chili555 on 2013-11-24
So far, so good!> Blacklists:
Code:

volkan@magnets:/etc/modprobe.d$ cat broadcom-sta-common.conf
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
#blacklist brcmsmac
blacklist ssb
[COLOR="#FF0000"]#[/COLOR]install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTSI would comment out that line, too.> volkan@magnets:/etc/modprobe.d$ cat blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
[COLOR="#FF0000"]#[/COLOR]blacklist brcmsmac
#blacklist bcmaAnd that, too. Then, just watch what happens. We are getting closer to understanding 14e4:4727. If all goes well, we'll do some final housekeeping.

---

### Post by ximenacardinali on 2013-11-25
Hello there, I have commented the lines that you told me, and now those files are looking as follow:

```
volkan@magnets:~$ cat /etc/modprobe.d/broadcom-sta-common.conf 
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
#blacklist brcmsmac
blacklist ssb
#install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
volkan@magnets:~$ 
```

And:
```
volkan@magnets:~$ cat /etc/modprobe.d/blacklist-bcm43.conf 
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
#blacklist brcmsmac
#blacklist bcma
volkan@magnets:~$ 
```

Also, the syslog is looking like this:
```
volkan@magnets:~$ cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20Nov 25 23:14:07 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Nov 25 23:14:07 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Nov 25 23:14:07 magnets kernel: [   28.074326] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
Nov 25 23:14:08 magnets NetworkManager[815]: <info> DNS: starting dnsmasq...
Nov 25 23:14:08 magnets NetworkManager[815]: <error> [1385417648.658368] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Nov 25 23:14:08 magnets NetworkManager[815]: <error> [1385417648.658393] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Nov 25 23:14:08 magnets NetworkManager[815]: <warn> DNS: plugin dnsmasq update failed
Nov 25 23:14:08 magnets NetworkManager[815]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 25 23:14:08 magnets NetworkManager[815]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Nov 25 23:14:09 magnets NetworkManager[815]: <info> Policy set 'Cerens' (wlan0) as default for IPv4 routing and DNS.
Nov 25 23:14:09 magnets NetworkManager[815]: <info> Activation (wlan0) successful, device activated.
Nov 25 23:14:09 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Nov 25 23:14:09 magnets NetworkManager[815]: <warn> dnsmasq appeared on DBus: :1.45
Nov 25 23:14:09 magnets NetworkManager[815]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Nov 25 23:14:27 magnets NetworkManager[815]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 25 23:14:27 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 25 23:14:27 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 25 23:14:27 magnets NetworkManager[815]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 25 23:14:32 magnets ntpd[3909]: Listen normally on 3 wlan0 192.168.2.103 UDP 123
Nov 25 23:14:32 magnets ntpd[3909]: Listen normally on 4 wlan0 fe80::f6b7:e2ff:feb3:3622 UDP 123
volkan@magnets:~$ 
```

I'm curious about the errors and warning messages on the syslog. 
For now I didn't experience any connection cuts, I will let you know how is it going after the implementation of these steps :)

---

### Post by chili555 on 2013-11-25
> I'm curious about the errors and warning messages on the syslog. Please see here: [http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict](http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict)> Therefore, if you use network manager (fine in simple set-ups only), then install dnsmasq-base, but not dnsmasq.Let's see which you have installed and try to recify it.```
sudo dpkg -s dnsmasq
sudo dpkg -s dnsmasq-base
```In my simple system, using NM, I have dnsmasq-base and not dnsmasq.

---

### Post by ximenacardinali on 2013-11-28
Hello There, sorry for the delay!

For sudo dpkg -s dnsmasq:
```
 Package `dnsmasq' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents. 
```


For sudo dpkg -s dnsmasq-base:
```
 Package: dnsmasq-base
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 512
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: dnsmasq
Version: 2.59-4ubuntu0.1
Replaces: dnsmasq (<< 2.59-4ubuntu0)
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.1.1), libidn11 (>= 1.13), libnetfilter-conntrack3 (>= 0.9.1)
Breaks: dnsmasq (<< 2.59-4ubuntu0)
Conffiles:
 /etc/dbus-1/system.d/dnsmasq.conf 9a18c8a761c2262dbf0c8b3345a85242
Description: Small caching DNS proxy and DHCP/TFTP server
 This package contains the dnsmasq executable and documentation, but
 not the infrastructure required to run it as a system daemon. For
 that, install the dnsmasq package.
Original-Maintainer: Simon Kelley <simon@thekelleys.org.uk>
```

It'S same configuration as you have, right?

---

### Post by chili555 on 2013-11-29
It is the same configuration and, as far as I know, correct configuration. As for the errors in the syslog, let's do some housekeeping first and see if it helps. We have established that brcmsmac is correct for your Ubuntu version and your 14e4:4727 device. Let's remove the wl driver:```
sudo apt-get remove --purge bcmwl-kernel-source
```Since your wireless  seems to be working as expected, aside from the syslog message, wait until you would otherwise reboot and then look at the logs again:```
cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20
```Is the message gone? Better? Worse?

I saw this: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1047221](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1047221) > This bug was fixed in the package network-manager - 0.9.6.0-0ubuntu6Which do you have?```
sudo dpkg -s network-manager
```

---

### Post by ximenacardinali on 2013-12-02
Hello there!

I have removed the "bcmwl-kernel-source" and this is the syslog output:

```
volkan@magnets:~$ cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20
Dec  2 16:33:30 magnets kernel: [23383.805002] ieee80211 phy0: wl0: ampdu tx phy error (0x20)
Dec  2 16:33:39 magnets kernel: [23393.309648] ieee80211 phy0: wl0: ampdu tx phy error (0x20)
volkan@magnets:~$ 
```

Also, it seems that I have a previous version of the network-manager:
```
volkan@magnets:~$ sudo dpkg -s network-manager
[sudo] password for volkan: 
Package: network-manager
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 1696
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.9.4.0-0ubuntu4.3
Depends: libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libgudev-1.0-0 (>= 147), libnl-3-200 (>= 3.2.3), libnl-genl-3-200 (>= 3.2.3), libnl-route-3-200, libnm-glib4 (>= 0.9.4.0~git201203162258.69247a0), libnm-util2 (>= 0.9.3.995+git201203081848.bba834f), libpolkit-gobject-1-0 (>= 0.99), upstart-job, lsb-base (>= 3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev, isc-dhcp-client (>= 4.1.1-P1-4), iproute, dnsmasq-base (>= 2.59-4ubuntu0.1), iputils-arping
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: network-manager-pptp, network-manager-gnome | network-manager-kde | plasma-widget-networkmanagement, policykit-1, ppp (>= 2.4.5), iptables, modemmanager
Suggests: avahi-autoipd, python
Breaks: network-manager-gnome (<< 0.8.99), network-manager-kde (<< 1:0.9~~), network-manager-openvpn (<< 0.8.99), network-manager-pptp (<< 0.8.99), network-manager-vpnc (<< 0.8.99), ppp (<< 2.4.5)
Conflicts: connman
Conffiles:
 /etc/init/network-manager.conf 080b2a860317698f65f960687f5363cc
 /etc/dbus-1/system.d/nm-dispatcher.conf 5711a76c31a3763750fe2c331741f679
 /etc/dbus-1/system.d/org.freedesktop.NetworkManager.conf 5d2ea570537233f0504022c0a760c5f8
 /etc/dbus-1/system.d/nm-avahi-autoipd.conf 91ab68968b0dc06c3a55b482b50b3028
 /etc/dbus-1/system.d/nm-dhcp-client.conf 06b1ecfd8f1fa2a501a5f352e2e5e88e
 /etc/NetworkManager/dispatcher.d/01ifupdown e491a5bec6ce58505181d573d38036bc
 /etc/NetworkManager/NetworkManager.conf 725fe5849b897aeda40cc37b83f9e1ef
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when
 available. It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE
 devices, and provides VPN integration with a variety of different VPN
 services.
 .
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager.
 .
 Optional dependencies:
  * policykit-1: Required for reading and writing system connections.
  * ppp: Required for establishing dial-up connections (e.g. via GSM).
  * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
    address configuration.
Homepage: http://www.gnome.org/projects/NetworkManager/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>
volkan@magnets:~$
```

---

### Post by ximenacardinali on 2013-12-02
Here you can see some more syslog messages after a reboot of the laptop:
```
volkan@magnets:~$ cat /var/log/syslog | grep -e wl -e 80211 -e etwork | tail -n20
Dec  2 20:53:41 magnets NetworkManager[886]: <error> [1386014021.626423] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec  2 20:53:41 magnets NetworkManager[886]: <error> [1386014021.626522] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec  2 20:53:41 magnets NetworkManager[886]: <warn> DNS: plugin dnsmasq update failed
Dec  2 20:53:41 magnets NetworkManager[886]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Dec  2 20:53:41 magnets NetworkManager[886]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec  2 20:53:42 magnets NetworkManager[886]: <info> Policy set 'Cerens' (wlan0) as default for IPv4 routing and DNS.
Dec  2 20:53:42 magnets NetworkManager[886]: <info> Activation (wlan0) successful, device activated.
Dec  2 20:53:42 magnets NetworkManager[886]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec  2 20:53:42 magnets NetworkManager[886]: <warn> dnsmasq appeared on DBus: :1.42
Dec  2 20:53:42 magnets NetworkManager[886]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Dec  2 20:53:42 magnets avahi-daemon[773]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::f6b7:e2ff:feb3:3622.
Dec  2 20:53:42 magnets avahi-daemon[773]: New relevant interface wlan0.IPv6 for mDNS.
Dec  2 20:53:42 magnets avahi-daemon[773]: Registering new address record for fe80::f6b7:e2ff:feb3:3622 on wlan0.*.
Dec  2 20:53:51 magnets kernel: [   38.765862] wlan0: no IPv6 routers present
Dec  2 20:53:54 magnets ntpd[3046]: Listen normally on 3 wlan0 192.168.2.103 UDP 123
Dec  2 20:53:54 magnets ntpd[3046]: Listen normally on 4 wlan0 fe80::f6b7:e2ff:feb3:3622 UDP 123
Dec  2 20:54:00 magnets NetworkManager[886]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec  2 20:54:00 magnets NetworkManager[886]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec  2 20:54:00 magnets NetworkManager[886]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec  2 20:54:00 magnets NetworkManager[886]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
volkan@magnets:~$ 
```

And it seems that with my sources I still don't have the new network-manager version:
```
volkan@magnets:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.9.4.0-0ubuntu4.3
  Candidate: 0.9.4.0-0ubuntu4.3
  Version table:
 *** 0.9.4.0-0ubuntu4.3 0
        500 http://de.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 http://de.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
volkan@magnets:~$ 
```

---

### Post by chili555 on 2013-12-02
After doing so, does your wireless still work correctly? Are the dnsmasq errors gone?```
cat /var/log/syslog | grep dnsmasq
```

---

