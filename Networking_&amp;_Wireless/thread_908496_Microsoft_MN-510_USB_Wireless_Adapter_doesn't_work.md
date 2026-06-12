---
title: "Microsoft MN-510 USB Wireless Adapter doesn't work"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by someguywhoneedshelp on 2008-09-02
Hi there, I'm trying to get my old Microsoft MN-510 USB adapter working on 64-bit Ubuntu 8.04, and I'm running into some problems.

According to [this help page]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb"), it is supported by the prism2_usb driver. When I plugged it in, Network Manager saw it but failed to connect. Trying to configure it manually on the command line didn't work either.```
me@localhost:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:4A:3B:E0
                    ESSID:"network"
                    Mode:Master
                    Encryption key:off
                    Channel:1
                    Quality:25/100  Signal level:-77 dBm  Noise level:-87 dBm

me@localhost:~$ sudo iwconfig wlan0 essid network
me@localhost:~$ iwconfig wlan0
wlan0     no wireless extensions.
```
Both the power and wireless lights on the adapter were lit up solid, when I used it on a WinXP box the wireless light used to blink.

Here is what I saw in dmesg when I plugged the adapter in and tried to connect:```
[529383.182062] usb 3-1: new full speed USB device using uhci_hcd and address 5
[529383.356633] usb 3-1: configuration #1 chosen from 1 choice
[529385.360417] ident: nic h/w: id=0x8010 1.0.0
[529385.361415] ident: pri f/w: id=0x15 1.1.2
[529385.362409] ident: sta f/w: id=0x1f 1.5.1
[529385.363412] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[529385.364405] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[529385.365410] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[529385.366406] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[529385.367410] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[529385.368406] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[529385.369407] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[529385.370404] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[529385.897128] linkstatus=CONNECTED
[529393.931678] usbctlx_rrid_completor_fn: RID len mismatch, rid=0xfcbe hlen=2 fwlen=-2
[529396.805747] wlan0: no IPv6 routers present
[529427.262068] ADDRCONF(NETDEV_UP): ath0: link is not ready
[529427.479283] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[529432.611929] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[529433.616755] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529434.616203] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529435.619650] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529436.619097] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529437.618544] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529438.140552] ath0: no IPv6 routers present
[529438.617993] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529441.384637] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[529445.377258] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529446.376709] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529447.376160] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529448.375606] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529449.375056] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529450.996716] NETDEV WATCHDOG: wlan0: transmit timed out
[529450.998150] wlan0 rx pipe reset complete.
[529451.000145] wlan0 tx pipe reset complete.
[529451.000267] p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
[529451.000273] p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
[529451.000278] p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
[529451.000283] p80211knetdev_hard_start_xmit: Tx attempt prior to association, frame dropped.
[529454.876016] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[529455.875468] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529456.874911] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529457.874362] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529458.873808] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529459.873258] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529459.873269] prism2mgmt_scan: getconfig(ROAMMODE) failed. result=-5
[529460.872705] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529461.871152] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529462.878596] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[529463.878047] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529464.877495] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529465.876944] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529466.877390] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529467.876838] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529468.875286] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529469.874741] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529469.973207] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[529469.973258] ath_pci: driver unloaded
[529472.137486] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529473.136934] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529474.136379] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529475.135832] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529476.139278] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529477.642443] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529478.648888] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[529479.652333] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529480.655780] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529481.659227] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529482.662673] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529483.666118] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529484.665571] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529499.660290] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529499.660302] prism2mgmt_scan: getconfig(ROAMMODE) failed. result=-5
[529500.667736] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
[529501.667187] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529502.666635] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529503.666078] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529504.669528] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529506.668423] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529507.667871] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529508.667321] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529509.666768] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529510.666218] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529512.665113] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529513.668559] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529514.667008] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529515.666458] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529516.665907] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529517.665353] hfa384x_usbctlx_complete_sync: CTLX[2] error: state(Request failed)
[529518.664804] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529521.679137] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529522.678589] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[529523.678124] hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed)
```

I tried updating the firmware using the [instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb#Updating%20firmware") on the help page, but it's still not working. Here's the output I got after doing that:```
[531099.043315] usb 3-1: new full speed USB device using uhci_hcd and address 6
[531099.221377] usb 3-1: configuration #1 chosen from 1 choice
[531100.680464] ident: nic h/w: id=0x8010 1.0.0
[531100.681473] ident: pri f/w: id=0x15 1.1.2
[531100.682461] ident: sta f/w: id=0x1f 1.5.1
[531100.683468] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[531100.684461] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[531100.685457] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[531100.686469] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[531100.687459] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[531100.688464] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[531100.689455] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[531100.690453] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[531103.992732] PDA Read from 0x007f0000 in EXTDS space.
[531103.997640] PDA Read from 0x007f0000 in EXTDS space.
[531104.037673] Writing 4096 bytes to ram @0x7e2ffe
[531104.045641] Writing 4096 bytes to ram @0x7e3ffe
[531104.053622] Writing 4096 bytes to ram @0x7e4ffe
[531104.061619] Writing 4096 bytes to ram @0x7e5ffe
[531104.069616] Writing 4096 bytes to ram @0x7e6ffe
[531104.077608] Writing 4096 bytes to ram @0x7e7ffe
[531104.085598] Writing 4096 bytes to ram @0x7e8ffe
[531104.093597] Writing 4096 bytes to ram @0x7e9ffe
[531104.100769] Writing 4096 bytes to ram @0x7eaffe
[531104.108596] Writing 4096 bytes to ram @0x7ebffe
[531104.116586] Writing 4096 bytes to ram @0x7ecffe
[531104.124600] Writing 4096 bytes to ram @0x7edffe
[531104.132582] Writing 3010 bytes to ram @0x7eeffe
[531104.138574] Writing 416 bytes to ram @0x7efc20
[531104.139576] Writing 16 bytes to ram @0x7efdd0
[531104.140579] Writing 4044 bytes to ram @0x7f0800
[531104.148605] Writing 3288 bytes to ram @0x7fe000
[531105.221960] ident: nic h/w: id=0x8010 1.0.0
[531105.222953] ident: pri f/w: id=0x15 1.1.2
[531105.223966] ident: sta f/w: id=0x1f 1.8.3
[531105.224954] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[531105.225960] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[531105.226952] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[531105.227959] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/15
[531105.228950] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[531105.229957] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[531105.230949] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[531105.231957] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[531105.604748] linkstatus=DISCONNECTED (unhandled)
[531105.611144] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```Now the wireless light blinks for a few seconds when I plug it in and then goes off, and I can't scan for wireless networks anymore :(```
me@localhost:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```Any idea what's going on here? I would be happy to post any more information if it would be helpful.

---

### Post by someguywhoneedshelp on 2008-09-02
Small update, I tried installing the latest version of the driver from svn. Now when I plug it in the wireless light blinks, but it still doesn't see any wireless networks.

---

### Post by someguywhoneedshelp on 2008-09-04
Sigh. I tried ndiswrapper too, still no luck. The only Windows driver I could find for it was the 32-bit one on driverguide.com, and ndiswrapper tells me it's an invalid driver.

Does anyone have this adapter working?

---

### Post by miceterminator on 2008-10-07
Hey I got exactly the same problem with this device. Reffering to g00gle it looks like there is a problem concerning the USB driver for the prism2.x chips.

beginning of a line of mails discussing this issues

[http://lists.linux-wlan.com/pipermail/linux-wlan-user/2005-December/013584.html](http://lists.linux-wlan.com/pipermail/linux-wlan-user/2005-December/013584.html) a mailing list from 2005 (someone claims that he fixed the issue in the newest version)


[http://lists.linux-wlan.com/pipermail/linux-wlan-devel/2008-January/003730.html](http://lists.linux-wlan.com/pipermail/linux-wlan-devel/2008-January/003730.html)

Unfortunately my Linux skills aren't high enough to follow the discussion of these guys but I hope that someone in this board might be able to help.

As far as I searched the Internet I only found posts which are still open or unsolved concerning this issue. 

btw I have a "Siemens Connectbird USB" w-lan stick which seemed to work well with linux about 6 years ago.

EDIT:

actually could you explain how you did the firmware update and could you please post the dmesg messages when it is blinking? (I'm courious wheather the  hfa384x_usbctlx_complete_sync: CTLX[1] error: state(Request failed) messages are still coming up)

---

