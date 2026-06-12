---
title: "Lost WWAN functionality after recent update for 16.04 LTS"
date: 2016-05-19
forum: Networking &amp; Wireless
---

### Post by bhima-pandava on 2016-05-19
I've been running 16.04 for a few weeks on a Soekris Net6501 router with a Sierra MC7710 LTE modem a few days ago I updated to the current kernel and after a subsequent reboot wwan0 disappeared and I was unable to connect using the same qmi-network helper script that I've been using for the past few years. After some basic troubleshooting I'm able to connect using "mmcli --simple-connect" but rather than WWAN0, "wwp2s2f3u3i8" gets created and the available throughput is severely constrained.

I'm not really sure what the preferred way to configure enable, and initiate LTE modems that use QMI is with 16.04, so I'm hoping someone can give me some pointers.

Thanks! 


I'm attaching some information I hope is relevant

```

sudo qmi-network /dev/cdc-wdm0 start
Loading profile...
    APN: drei.at
Starting network with 'qmicli -d /dev/cdc-wdm0 --wds-start-network=drei.at  --client-no-release-cid'...
[19 May 2016, 19:08:19] -Warning ** Error reading from istream: Resource temporarily unavailable
error: couldn't create client for the 'wds' service: CID allocation failed in the CTL client: Transaction timed out
error: network start failed, client not allocated

```

```

ifconfig:

wwp2s2f3u3i8 Link encap:Ethernet  HWaddr ce:03:a2:0b:73:db          inet addr:178.n.0.n  Bcast:178.113.0.91  Mask:255.255.255.252
          inet6 addr: fe80::cc03:a2ff:fe0b:73db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:572760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:686566483 (686.5 MB)  TX bytes:41555493 (41.5 MB)
```


```

mmcli -m 0


/org/freedesktop/ModemManager1/Modem/0 (device id 'nnnn')
  -------------------------
  Hardware |   manufacturer: 'Sierra Wireless, Incorporated'
           |          model: 'MC7710'
           |       revision: 'SWI9200X_03.00.08.02AP R3715 CARMD-EN-10526 2011/11/14 18:42:43'
           |      supported: 'gsm-umts
           |                  lte
           |                  gsm-umts, lte'
           |        current: 'gsm-umts, lte'
           |   equipment id: '35817804nnnnnn'
  -------------------------
  System   |         device: '/sys/devices/pci0000:00/0000:00:17.0/0000:01:00.0/0000:02:02.3/usb1/1-3'
           |        drivers: 'qcserial, qmi_wwan'
           |         plugin: 'Gobi'
           |   primary port: 'cdc-wdm0'
           |          ports: 'ttyUSB0 (qcdm), ttyUSB2 (at), cdc-wdm0 (qmi), wwp2s2f3u3i8 (net)'
  -------------------------
  Numbers  |           own : 'unknown'
  -------------------------
  Status   |           lock: 'sim-pin2'
           | unlock retries: 'sim-pin (3), sim-pin2 (3), sim-puk (10), sim-puk2 (10)'
           |          state: 'connected'
           |    power state: 'on'
           |    access tech: 'lte'
           | signal quality: '52' (recent)
  -------------------------
  Modes    |      supported: 'allowed: 2g, 3g, 4g; preferred: none'
           |        current: 'allowed: 2g, 3g, 4g; preferred: none'
  -------------------------
  Bands    |      supported: 'cdma-bc15-aws, dcs, egsm, pcs, u2100, u900'
           |        current: 'cdma-bc15-aws, dcs, egsm, pcs, u2100, u900'
  -------------------------
  IP       |      supported: 'ipv4, ipv6, ipv4v6'
  -------------------------
  3GPP     |           imei: 'nnnnnnn'
           |  enabled locks: 'none'
           |    operator id: '23210'
           |  operator name: '3 AT'
           |   subscription: 'unknown'
           |   registration: 'home'
  -------------------------
  SIM      |           path: '/org/freedesktop/ModemManager1/SIM/0'


  -------------------------
  Bearers  |          paths: '/org/freedesktop/ModemManager1/Bearer/0'



```

---

### Post by ingineer on 2016-09-17
I too am having this.  Worked fine in 14.04, connection is shown, carrier is shown, but when trying to connect it sits there trying for about 30 seconds then NetManager shows "disconnected".

Modem is a Sierra EM7345 LTE.  
USB ID 1199:a001 Sierra Wireless, Inc.

Also cannot cannot to secure WiFi networks without first adding them manually. NetManger immediately shows a dialog: "CONNECTION ACTIVATION FAILED (2) Active connection removed before it was initialized."

---

### Post by ingineer on 2016-11-11
Any update on this?  I still have the problem.  Updated my EM7345 to FIH7160_V1.2_WW_01.1612.00 to no avail.  Still works perfectly in Win8.1.

---

