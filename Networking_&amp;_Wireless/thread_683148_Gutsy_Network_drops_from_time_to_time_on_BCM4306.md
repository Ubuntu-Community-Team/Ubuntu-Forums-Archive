---
title: "Gutsy: Network drops from time to time on BCM4306"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by lungdart on 2008-01-30
What appears to be randomly over long stretches of time, my network connection will drop with no avail to get it back without a reboot. The network connection is still there of course as tested by wired linux and windows machines,


First off, I have removed network-manager because I find it to be flaky. Not sure if anyone agrees with me on this one, but It is my opinion.

I installed the drivers using the restricted driver manager app, and the default file it downloads from the internet.

I set up the card for a static IP address via the graphical tool in gnome. Here is some output of my configuration:

```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:30:BD:97:22:55  
          inet addr:192.168.0.120  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe97:2255/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2624 errors:0 dropped:29 overruns:0 frame:0
          TX packets:2659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2224926 (2.1 MB)  TX bytes:349407 (341.2 KB)
          Interrupt:5 Base address:0xc000
```

```
$ iwconfig
eth1      IEEE 802.11b/g  ESSID:"lungair"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:D1:46:36:BA   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=81/100  Signal level=-46 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.0.120
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid lungair







auto eth1
```

When my connection drops, this mysterious snippet shows in the messages file:

```
Jan 30 17:54:28 Lung-Zilla kernel: [247107.381828] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:02:30 Lung-Zilla kernel: [247588.408538] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:04:50 Lung-Zilla kernel: [247728.704261] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:06:31 Lung-Zilla kernel: [247828.913873] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:14:32 Lung-Zilla kernel: [248309.932452] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:17:33 Lung-Zilla kernel: [248490.314510] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:24:34 Lung-Zilla kernel: [248911.201888] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:28:26 Lung-Zilla kernel: [249141.720710] SoftMAC: Open Authentication completed with 00:18:d1:46:36:ba
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010160] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010175] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010183] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010190] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010196] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010203] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010210] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010217] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010224] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010230] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010237] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:30:52 Lung-Zilla kernel: [249288.010244] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623297] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623311] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623318] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623324] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623331] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623338] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623344] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623351] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1112
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623357] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623364] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623370] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:36:04 Lung-Zilla kernel: [249599.623377] bcm43xx: TODO: Incomplete code in keymac_write() at /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/wireless/bcm43xx/bcm43xx_main.c:1114
Jan 30 18:39:14 Lung-Zilla kernel: [249789.770537] nfsd: last server has exited
Jan 30 18:39:14 Lung-Zilla kernel: [249789.770546] nfsd: unexporting all filesystems
Jan 30 18:39:14 Lung-Zilla kernel: [249789.775430] RPC: failed to contact local rpcbind server (errno 5).
Jan 30 18:39:14 Lung-Zilla exiting on signal 15
Jan 30 18:40:37 Lung-Zilla syslogd 1.4.1#21ubuntu3: restart.
```

The time of the TODO errors corresponds with my network drop offs, and as you can see, I reset at 18:39:14 to remedy the problem.

Any ideas as to what is going on?
Thanks.

---

### Post by lungdart on 2008-01-30
Oh, and in case more information is needed:

```
$ uname -a
Linux Lung-Zilla 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
```

```
$ lspci | grep -i broadcom
00:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

---

### Post by lungdart on 2008-01-31
16 hours and buried 5 pages. wow.

Regardless, this is a bump.

---

### Post by lungdart on 2008-02-05
Bumpity bump bump, C'mon here people.

---

### Post by baixinhu on 2008-02-05
the only thing i can say is that i have the same problem with bcm4318 and the same drivers... 
i guess some one had some luck with ndiswrapper drivers, but i cant install them... 
you may want to try that and post the results

---

### Post by baixinhu on 2008-02-06
> **lungdart said:**
> Bumpity bump bump, C'mon here people.

try this [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
its kindda working for me now, at least better than restricted drivers... but must be a config problem only

---

### Post by lungdart on 2008-02-07
Thanks for the link. So it does seem to be a general problem with fwcutter eh?

That's too bad, as its so much nicer than ndiswrapper. Maybe Hardy will have better wireless support. When I get a chance, I will try that guide, and post here if it has solved my problem. I will not be doing it now, since I need a wired connection while attempting it.

---

### Post by centered effect on 2008-06-08
just to note, I have had this problem with mulitple laptops since Dapper and my current under Gusty (HP dv6704).

If the system loses signal or the modem loses signal, I still need to reboot, which gets annoying after awhile

---

