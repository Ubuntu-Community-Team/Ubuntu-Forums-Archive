---
title: "Network Manager 0.7 and Novatel XU870"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by mozi on 2008-10-12
Hi,
I have installed NM 0.7 from launchpad in hardy and it doesn't connect with network, I get such output from logs:

Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'iPlus' 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Oct 12 23:22:15 mozi-laptop NetworkManager: <debug> [1223846535.497429] nm_serial_device_open(): (ttyUSB0) opening device... 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Oct 12 23:22:15 mozi-laptop NetworkManager: <WARN>  init_done(): Modem initialization failed 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 
Oct 12 23:22:15 mozi-laptop NetworkManager: <debug> [1223846535.635355] nm_serial_device_close(): Closing device 'ttyUSB0' 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Marking connection 'iPlus' invalid. 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  Activation (ttyUSB0) failed. 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Oct 12 23:22:15 mozi-laptop NetworkManager: <info>  (ttyUSB0): deactivating device. 
Oct 12 23:22:15 mozi-laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Oct 12 23:22:15 mozi-laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed

Have you any ideas how to fix it? Thanks in advance,
Mark

---

### Post by 2GooD on 2008-10-30
Did you solve this yet?

I get *exactly* the same log messages when I try to use my Huawei HSDPA USB modem model E220.

---

### Post by mozi on 2008-10-30
no I haven't solved it in hardy but I installed the 8.10 version  and it seems that it has been fixed :)

---

### Post by 2GooD on 2008-10-30
> **mozi said:**
> no I haven't solved it in hardy but I installed the 8.10 version  and it seems that it has been fixed :)

Maybe not the same issue then.

I got it working by accident now: I had it working before with wvdial so I tried that again. Worked. Now the PIN code was set, and then I was able to connect with NetworkManager. It seems like NetworkManager can't handle the PIN code for me.

\David

---

### Post by rcerreto on 2008-11-01
I'm experiencing the same issue.
NetworkManager appears not to correctly use the provided PIN.
Once I unlock the modem sending the AT+CPIN=<mypin> sequence via an external program, NetworkManager works fine and I can connect without any further problem.

---

### Post by stoffe on 2008-11-02
Thanks guys, it was the pin alright when I had the exact same error. I put the SIM in a phone and removed the PIN and then it works. Has anyone seen a bug for this or should we file one?

---

### Post by rcerreto on 2008-11-05
In case you'd like, for safety reasons, to keep using a PIN you can unlock the card by issuing an appropriate AT command:

AT+CPIN=<yourPINhere>

for instance by adding an entry in /etc/wvdial.conf:

[Dialer pin]
Modem = /dev/ttyUSB0
Init1 = AT+CPIN=<yourPINhere>

then:
$> sudo wvdial pin
will unlock the card

---

### Post by rcerreto on 2008-11-05
> **stoffe said:**
> Thanks guys, it was the pin alright when I had the exact same error. I put the SIM in a phone and removed the PIN and then it works. Has anyone seen a bug for this or should we file one?

As far as I know, no bug has been filed. If you know how to do it, that could help. Thanks.

---

