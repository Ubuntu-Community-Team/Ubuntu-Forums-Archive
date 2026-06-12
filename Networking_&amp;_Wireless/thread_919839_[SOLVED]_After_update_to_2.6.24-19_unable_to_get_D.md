---
title: "[SOLVED] After update to 2.6.24-19 unable to get DHCP"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by TheTank on 2008-09-14
Hello all.

Due to some issues with the 2.6.24-16 kernel I upgraded to 2.6.24-19.
Prior to updating my wlan was working fine.

I noticed that after upgrading all my restricted drivers were disabled. 

After reinstalling my wlan drivers I am able to get connection to my router again, but it won't get an address via DHCP.

I have tried everything I could think of and still nothing.

I have a rt73 based USB dongle.
lsmod shows the rt73

iwconfig -v
```

iwconfig  Wireless-Tools version 29
          Compatible with Wireless Extension v11 to v22.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v14 or later,
          Currently compiled with Wireless Extension v22.

```

iwconfig
```

wlan0     RT73 WLAN  ESSID:"LalaLand"  
          Mode:Managed  Frequency=2.462 GHz  Access Point:01:23:45:67:89:10   
          Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=49/100  Signal level:-76 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
The ESSID and AP are correct.

/sbin/modinfo rt73
```

filename:       /lib/modules/2.6.24-19-generic/extra/rt73.ko
license:        GPL
description:    Ralink RT73 802.11abg WLAN Driver 1.0.3.6 CVS 2008091413
author:         http://rt2x00.serialmonkey.com
srcversion:     39C193E2B42A22AA94BB996
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           ifname:Network device name (default wlan%d) (charp)
parm:           firmName:Permit to load a different firmware: (default: rt73.bin)  (charp)

```

Can anyone help?
What info is needed?

---

### Post by TheTank on 2008-09-15
Forgot to mention: I am using the 1.0.3 version of serialmonkey's drivers.

---

### Post by TheTank on 2008-09-15
Booted up today and everything worked.. Strange.
Marked as solved and can be deleated.

---

