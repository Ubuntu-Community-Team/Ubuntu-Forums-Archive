---
title: "Feisty, wg111 v2 &amp; kismet problem"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by pctips on 2007-09-09
Hello
I've just installed Kubuntu Feisty and it automatically detects my wg111 v2 wireless adapter. However, I can't use kismet:

[B]root@pctips-desktop:~# kismet -c rt8180,wlan0,wg111v2
Server options:   -c rt8180,wlan0,wg111v2
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (wg111v2): Enabling monitor mode for rt8180 source interface wlan0 channel 6...
FATAL: SetIFFlags: Unknown interface wlan0: Operation not permitted
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...[/B]

Chipset is a Realtek 8187 and USB ID is 0846:4240. After an "ifdown wlan0" I can manually enter Monitor mode, but even airodump doesn't work:

[B]root@pctips-desktop:~# airodump-ng wlan0
ioctl(SIOCSIFFLAGS) failed: Operation not permitted[/B]

Can someone help me?

Thank you

---

### Post by CountSessine on 2007-10-09
I don't think you have a Realtek 8187. The NetGear wg111v2 (0846:4240) uses an Intersil Prism GT. I have one myself. It 'just works' for standard internet connectivity in ubuntu, but I don't seem to be able to start it in monitor mode. 

I'm not sure, but I don't think that the current prism54 driver supports monitor mode for USB PrismGT softmac devices.

---

### Post by CountSessine on 2007-10-10
Yes - poking around the prism54 forums, it looks like there have been 2 versions of the WG111v2 (!). The first, with the USBid 4240 is a Prism GT -based device (what you and I have), and the second, with id 6a00, is a realtek or ralink -based device.

---

