---
title: "Networking with a USBLink"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by SteMMo on 2007-02-27
Hi all !
I'm trying to connect an Ubuntu machine with a Win2000 machine via USBLink 2.0 cable.
This is a host-host cable based on Prolific PL-2501.

When i attached the cable is saw in the dmesg messages:

[17180116.668000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17180117.568000] usb0: register 'plusb' at usb-0000:00:07.2-1, Prolific PL-2301/PL-2302, ae:1e:3a:f5:9d:ab
[17180117.568000] usbcore: registered new driver plusb

Well, i suppose the kernel had load the plusb driver (even if it recognized a PL-2301 chip).

I also found:

[17179610.912000] usb0: register 'plusb' at usb-0000:00:07.2-1, Prolific PL-2301/PL-2302, ae:1f:f6:2e:0c:d3
[17179610.912000] usbcore: registered new driver plusb

so i installed
'sudo ifconfig usb0 192.168.1.1 pointopoint 192.168.1.2'

Now if i run 'ifconfig' i see a network card:

usb0      Link encap:Ethernet  HWaddr AE:1F:F6:2E:0C:D3
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ac1f:f6ff:fe2e:cd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:145665 dropped:0 overruns:0 frame:0
          TX packets:6 errors:63 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

Ubuntu machine on 192.168.1.1 and the Windows machine on 192.168.1.2
But if i run 'ping 192.168.1.2' i have no reply. The same on the other side ...

Please, where is the problem ?
Is the connection possible ? (I mean between Ubuntu and Windows...)
Is there any application to check and use this connection ??

Thanks !
ciao !!   Wink

---

### Post by SnappyU on 2008-06-13
A bit belated, but I tried running the sudo command on the other machine with the ips swapped, and they linked up with ping working.

Now trying to bridge the network so that one can surf the web through the other. :)

---

