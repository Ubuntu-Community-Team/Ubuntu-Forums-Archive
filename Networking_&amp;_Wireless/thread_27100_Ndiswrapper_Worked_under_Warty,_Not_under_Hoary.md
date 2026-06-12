---
title: "Ndiswrapper: Worked under Warty, Not under Hoary?"
date: 2005-04-14
forum: Networking &amp; Wireless
---

### Post by misteral on 2005-04-14
Hopefully someone can help.

I installed Warty a while ago. Was able to get my wireless device (D-Link DWL-G630 Rev B ACX100 based chip) working no problem with ndiswrapper.

When I upgraded to Hoary however, the wireless didn't work.

I tried fidgeting with a bunch of stuff, ended up re-installing. Wireless still didn;t work. When installing, the setup does detect my wireless card, and it's found in the driver database!

I've posted my interfaces info, ifconfig and iwconfig below. As mentioned, it's a dink card, running on a Compaq Armada E500 (which can use Wirelss no problem in W2K or Warty). I use DSL at with a dlink wireless router. The router WAS using an open key - I changed it to a shared key just to see if that was an issue (it wasn't)

Can anyone help?! 

```
allan@misteral:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wireless-essid default
wireless-key XXXXXXXXXX

auto wlan0


allan@misteral:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:4B:93:9B
          inet6 addr: fe80::2d0:59ff:fe4b:939b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:19 dropped:0 overruns:0 carrier:19
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:5166 (5.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89564 (87.4 KiB)  TX bytes:89564 (87.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:4D:48:00
          inet6 addr: fe80::20f:3dff:fe4d:4800/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

allan@misteral:/etc/network$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"default"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:46/100  Signal level:25/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.



```

---

### Post by misteral on 2005-04-14
Messages from dmesg. Not sure what to make from the error messages though - esp since the exact same driver works in Warty?

```
<acx_set_timer> Elapse = 2500000
acx_process_authen: UNVERIFIED.
00:0F:3D:4D:48:00 00:0F:3D:4D:48:00 00:11:95:56:A0:79 00:11:95:56:A0:79 00:11:95:56:A0:79
Algorithm is ok
Got current client for sta hash tab
Found acceptable client
acx_process_authen auth seq step 2.
Authentication FAILED (status code 13: "Responding station does not support the specified authentication algorithm. TRANSLATION: invalid network data or bug in ACX100 driver?"), still waiting for authentication.
acx_set_status: Setting status = 2 (WAIT_AUTH)
<acx_set_timer> Elapse = 1500000
acx_timer: status = 2
resend authen1 request (attempt 2).
Sending authentication1 request, awaiting response!
<acx_set_timer> Elapse = 2500000
acx_process_authen: UNVERIFIED.
00:0F:3D:4D:48:00 00:0F:3D:4D:48:00 00:11:95:56:A0:79 00:11:95:56:A0:79 00:11:95:56:A0:79
Algorithm is ok
Got current client for sta hash tab
Found acceptable client
acx_process_authen auth seq step 2.
Authentication FAILED (status code 13: "Responding station does not support the specified authentication algorithm. TRANSLATION: invalid network data or bug in ACX100 driver?"), still waiting for authentication.
acx_set_status: Setting status = 2 (WAIT_AUTH)
<acx_set_timer> Elapse = 1500000
acx_timer: status = 2
resend authen1 request (attempt 2).
Sending authentication1 request, awaiting response!
<acx_set_timer> Elapse = 2500000
acx_process_authen: UNVERIFIED.
00:0F:3D:4D:48:00 00:0F:3D:4D:48:00 00:11:95:56:A0:79 00:11:95:56:A0:79 00:11:95:56:A0:79
Algorithm is ok
Got current client for sta hash tab
Found acceptable client
acx_process_authen auth seq step 2.
Authentication FAILED (status code 13: "Responding station does not support the specified authentication algorithm. TRANSLATION: invalid network data or bug in ACX100 driver?"), still waiting for authentication.
acx_set_status: Setting status = 2 (WAIT_AUTH)
<acx_set_timer> Elapse = 1500000

```

---

