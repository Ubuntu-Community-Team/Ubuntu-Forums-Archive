---
title: "stuck with a Atheros AR5006EG wireless card"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by daniminas on 2007-12-01
Hi all

I was reading a lot before post but still i don't know what i'm missing.

I've an Atheros AR5006EG wireless on an Acer Aspire laptop running Ubuntu 7.10.

I've the restricted driver enabled, and all this:

```
daniel@daniel-laptop:~$ dmesg | grep ath
[   14.932000] ath_hal: module license 'Proprietary' taints kernel.
[   14.936000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.460000] ath_pci: 0.9.4.5 (0.9.3.2)
```

```
daniel@daniel-laptop:~$ lsmod | grep ath
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci
daniel@daniel-laptop:~$ 
```

```
daniel@daniel-laptop:~$ modprobe -l | grep ath
/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.22-14-generic/volatile/ath_hal.ko
daniel@daniel-laptop:~$ 
```

```
daniel@daniel-laptop:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr C6:6F:6C:38:1B:00  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c46f:6cff:fe38:1b00/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:2881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2259 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2022435 (1.9 MB)  TX bytes:338884 (330.9 KB)
          Interrupt:18 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0o
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

daniel@daniel-laptop:~$ 
```


```
daniel@daniel-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

daniel@daniel-laptop:~$ 
```


I really need to fix this, but i'm stuck.

Thanks for any help

Regards and sorry my english

-- Daniel

---

### Post by tturrisi on 2007-12-01
[http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG](http://madwifi.org/wiki/Compatibility/Atheros#AtherosAR5006EG)

---

