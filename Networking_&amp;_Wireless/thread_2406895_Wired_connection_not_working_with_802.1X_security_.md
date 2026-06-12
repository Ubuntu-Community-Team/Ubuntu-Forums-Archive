---
title: "Wired connection not working with 802.1X security on Ubuntu 18.04"
date: 2018-11-27
forum: Networking &amp; Wireless
---

### Post by rerodrig on 2018-11-27
Hi, i can't connect anymore to a wired connection that requires authentication (802.1x security / PEAP) after installing Ubuntu 18.04.

Here are some extra information:

The kernel version:
> 4.15.0-39-generic.

Device:
> Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)

Syslog: 
> Nov 27 15:15:39 lnxcit012332 wpa_supplicant[728]: EAP-MSCHAPV2: Authentication succeededNov 27 15:15:39 lnxcit012332 wpa_supplicant[728]: EAP-TLV: TLV Result - Failure
Nov 27 15:15:40 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Nov 27 15:15:52 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-STARTED EAP authentication started
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/DC=cit/CN=CERTCIT-CA' hash=df14d9d8d01baeb2b2112b3400d5cede03267c8eeed103636fcae6d237a46b0c
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/DC=cit/CN=CERTCIT-CA' hash=df14d9d8d01baeb2b2112b3400d5cede03267c8eeed103636fcae6d237a46b0c
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/C=br/ST=sp/L=cps/O=cit/OU=cit/CN=clearpass' hash=6332ba936bdf88be0c7749af64d4a2af683ec61779a78f842bf350e5d94bd96e
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: EAP-MSCHAPV2: Authentication succeeded
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: EAP-TLV: TLV Result - Failure
Nov 27 15:15:55 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <warn>  [1543338962.6194] device (enp7s0): Activation: (ethernet) association took too long.
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <info>  [1543338962.6200] device (enp7s0): state change: config -> failed (reason 'no-secrets', sys-iface-state: 'managed')
Nov 27 15:16:02 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-DISCONNECTED bssid=01:80:c2:00:00:03 reason=3 locally_generated=1
Nov 27 15:16:02 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="" auth_failures=1 duration=10 reason=AUTH_FAILED
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <warn>  [1543338962.6216] device (enp7s0): Activation: failed for connection 'Wired connection 1'
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <info>  [1543338962.6228] device (enp7s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
Nov 27 15:16:03 lnxcit012332 dbus-daemon[1617]: [session uid=1000 pid=1617] Activating service name='org.freedesktop.Notifications' requested by ':1.37' (uid=1000 pid=2061 comm="nm-applet " label="unconfined")
Nov 27 15:16:03 lnxcit012332 dbus-daemon[1617]: [session uid=1000 pid=1617] Successfully activated service 'org.freedesktop.Notifications'

Any ideas?

Thanks!

---

### Post by mitesh.agrwl on 2018-11-27
> **rerodrig said:**
> Hi, i can't connect anymore to a wired connection that requires authentication (802.1x security / PEAP) after installing Ubuntu 18.04.

```
 			 				Nov 27 15:15:39 lnxcit012332 wpa_supplicant[728]: EAP-MSCHAPV2:  Authentication succeededNov 27 15:15:39 lnxcit012332  wpa_supplicant[728]: EAP-TLV: TLV Result - Failure
Nov 27 15:15:40 lnxcit012332 **wpa_supplicant[728]:[SUP]1[/SUP]** enp7s0: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Nov 27 15:15:52 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-STARTED EAP authentication started
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0:  CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/DC=cit/CN=CERTCIT-CA'  hash=df14d9d8d01baeb2b2112b3400d5cede03267c8eeed10  3636fcae6d237a46b0c
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0:  CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/DC=cit/CN=CERTCIT-CA'  hash=df14d9d8d01baeb2b2112b3400d5cede03267c8eeed10  3636fcae6d237a46b0c
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: enp7s0:  CTRL-EVENT-EAP-PEER-CERT depth=0  subject='/C=br/ST=sp/L=cps/O=cit/OU=cit/CN=clearpass'  hash=6332ba936bdf88be0c7749af64d4a2af683ec61779a78  f842bf350e5d94bd96e
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: EAP-MSCHAPV2: Authentication succeeded
Nov 27 15:15:53 lnxcit012332 wpa_supplicant[728]: **EAP-TLV: TLV Result - Failure[SUP]2[/SUP]**
Nov 27 15:15:55 lnxcit012332 wpa_supplicant[728]: enp7s0: CTRL-EVENT-EAP-FAILURE EAP authentication failed
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <warn>   [1543338962.6194] device (enp7s0): Activation: (ethernet) association  took too long.
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <info>   [1543338962.6200] device (enp7s0): state change: config -> failed  (reason 'no-secrets', sys-iface-state: 'managed')
Nov 27 15:16:02 lnxcit012332 wpa_supplicant[728]: enp7s0:  CTRL-EVENT-DISCONNECTED bssid=01:80:c2:00:00:03 reason=3  locally_generated=1
Nov 27 15:16:02 lnxcit012332 wpa_supplicant[728]: enp7s0:**  CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="" auth_failures=1 duration=10  reason=AUTH_FAILED[SUP]3[/SUP]**
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <warn>   [1543338962.6216] device (enp7s0): Activation: failed for connection  'Wired connection 1'
Nov 27 15:16:02 lnxcit012332 NetworkManager[753]: <info>   [1543338962.6228] device (enp7s0): state change: failed ->  disconnected (reason 'none', sys-iface-state: 'managed')
Nov 27 15:16:03 lnxcit012332 dbus-daemon[1617]: [session uid=1000  pid=1617] Activating service name='org.freedesktop.Notifications'  requested by ':1.37' (uid=1000 pid=2061 comm="nm-applet "  label="unconfined")
Nov 27 15:16:03 lnxcit012332 dbus-daemon[1617]: [session uid=1000  pid=1617] Successfully activated service 'org.freedesktop.Notifications' 			 		
```
Any ideas?

Thanks!

It is because you are trying to use: **1** wpa_supplicant which is used for wireless connectivity. **2 **The authentication fails while verifying the EAP_TLV and **3 **It is expecting the values *id* and *ssid* which can be provided in wireless connection and due to lack of it denying the connection!

---

### Post by rerodrig on 2018-11-29
Thanks for answering, but do you have some idea why this is occurring if i'm trying to connect in a wired connection?


The wired connection works in a network without authentication 802.1x/PEAP.


It may be something related to the network driver or network manager?


Apparently I'm using the right driver according to kernel version.

Thanks

---

### Post by mitesh.agrwl on 2018-11-29
> **rerodrig said:**
> Thanks for answering, but do you have some idea why this is occurring if i'm trying to connect in a wired connection?


The wired connection works in a network without authentication 802.1x/PEAP.


It may be something related to the network driver or network manager?


Apparently I'm using the right driver according to kernel version.

Thanks

As far as I remember 802.1x/PEAP can be implemented on wired port also! The security setting in wired network connection also provides the support for PEAP. But there a catch, if the security is designed and implemented to authenticate the wireless connections only (to prevent unauthorised wired connections!), you should contact network administrator to check out the possibility, whether it is allowed or not.

---

