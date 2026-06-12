---
title: "ipw2100 - activate wlan antenna"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Stoff on 2007-07-23
Hello,

I try to get my ipw2100 card running. So far it did not work out, I suppose it must have something to do with my wlan antenna. Here are my current stats:

```
XXX@computer:/etc/network$ iwconfig
    lo no wireless extensions.

    eth0 no wireless extensions.

    eth1 unassociated ESSID:"XXX" Nickname:"ipw2100"
    Mode:Managed Channel=0 Access Point: Not-Associated
    Bit Rate=0 kb/s Tx-Power:off
    Retry limit:7 RTS thr:off Fragment thr:off
    Power Management:off
    Link Quality:0 Signal level:0 Noise level:0
    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
    Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

What does that all mean? How do I know whether the antenna is switched on?

   ```
 XXX@computer:/etc/network$ dmesg | grep ipw
    [ 20.252000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
    [ 20.252000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
    [ 20.388000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
```

```
    XXX@computer:/etc/network$ lspci | grep Wireless
    02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
```

```
    XXX@computer:/etc/network$ ifconfig
    eth0 Link encap:Ethernet HWaddr 00:40:CA:C5:43:EF
    inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0
    inet6 addr: fe80::240:caff:fec5:43ef/64 Scope:Link
    UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
    RX packets:3454 errors:0 dropped:0 overruns:0 frame:0
    TX packets:4303 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:2980527 (2.8 MiB) TX bytes:677742 (661.8 KiB)
    Interrupt:10 Base address:0xa800

    eth1 Link encap:Ethernet HWaddr 00:0C:F1:01:8B:A1
    inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
    Interrupt:10 Base address:0xa000 Memory:e0200000-e0200fff

    lo Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:4 errors:0 dropped:0 overruns:0 frame:0
    TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:200 (200.0 b) TX bytes:200 (200.0 b)

```

```
    stoff@computer:/etc/network$ iwlist eth1 scan
    eth1 No scan results

```

Don't I get exactly this result due to the non-activated antenna?

```
    XXX@computer:/etc/network$ cat interfaces
    auto lo
    iface lo inet loopback
    address 127.0.0.1
    netmask 255.0.0.0

    auto eth0
    iface eth0 inet static
    address 192.168.2.101
    netmask 255.255.255.0
    gateway 192.168.2.1

    auto eth1
    iface eth1 inet static
    address 192.168.2.101
    netmask 255.255.255.0
    gateway 192.168.2.1
    wireless-essid XXX
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

    # auto eth2
    # iface eth2 inet dhcp

    # auto ath0
    # iface ath0 inet dhcp

    # auto wlan0
    # iface wlan0 inet dhcp

```

This looks fine to me. The eth1 settings work fine with a wlan usb stick though I have dhcp activated then, but this should not cause my problems.

To install the ipw2100 drivers, I consulted [HTML]http://ipw2100.sourceforge.net[/HTML]. No success.

I read at [HTML]http://www.thp.uni-duisburg.de/~me/md41100/MD41100.html[/HTML]  (yes, this MD41100 is my laptop) that I could activate the antenna using wlan_radio_averatec_5110hx. How do I do that?

I also had a look at my bios. I can choose between "disabled" and "last status". Regardless of this setting, I think I should be able to start wlan afterwards.

Additionaly, there is a wlan key plus a LED. But nothing happens upon pressing the key.

More output:

```
XXX@computer:/etc/network$ lsmod | grep ipw
ipw2100                72244  0
ieee80211              34760  1 ipw2100

```

```
XXX@computer:/etc/network$ sudo iwconfig eth1 txpower on
```

does not give me any message. Results from iwconfig have not changed. 

```
XXX@computer:/etc/network$ cat /sys/class/net/eth1/device/power/state
0 

```

I found more information about the antenna.

```
XXX@computer:~$ dmesg | grep switch
[   12.096366] SMP alternatives: switching to UP code
[   20.688000] eth1: Radio is disabled by RF switch.
[ 2802.952000] fsam7400: SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.4.0

```

```
XXX@computer:~$ dmesg | grep eth1
[   20.688000] eth1: Radio is disabled by RF switch.
[   20.900000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 2983.736000] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

What is this RF switch?

```
XXX@computer:~$ dmesg | grep wireless
[ 2802.952000] fsam7400: no supported wireless hardware found
```

What is this fsam7400? What does it have to do with Fujitsu Simens? Is this what I am looking for?

Then I found this: [HTML]http://zwobbl.homelinux.net/[/HTML] I installed it and ended up with:

```
XXX@computer:~$ sudo rfsam on
no bios signature found 
```

The wlan card must work (it did so unter windows 98 se). What can I do? How do I get this antenna activated?

Hopefully you can help me - I would be so happy.

Thanks,

Christoph

---

### Post by Stoff on 2007-07-24
Is there really nobody out there who can help me? :(

---

