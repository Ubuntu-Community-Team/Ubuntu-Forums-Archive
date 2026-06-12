---
title: "Unable to connect for networks with password"
date: 2017-05-24
forum: Networking &amp; Wireless
---

### Post by dxvargas on 2017-05-24
I am able to connect to wifi networks that don't require password. But when I try to connect to a network that requires password, the password is not asked, Network Manager tries to connect and of course it fails.

This is the log from /var/log/syslog:

```

NetworkManager[936]: <info>  [1495625898.1943] device (wlp2s0): Activation: starting connection 'true_home2G_b68' (ea2f25dd-98bd-4e72-b660-5ac56c683519)
NetworkManager[936]: <info>  [1495625898.1944] audit: op="connection-activate" uuid="ea2f25dd-98bd-4e72-b660-5ac56c683519" name="true_home2G_b68" pid=2168 uid=1000 result="success"
NetworkManager[936]: <info>  [1495625898.1945] device (wlp2s0): state change: disconnected -> prepare (reason 'none') [30 40 0]
NetworkManager[936]: <info>  [1495625898.1946] manager: NetworkManager state is now CONNECTING
NetworkManager[936]: <info>  [1495625898.1951] device (wlp2s0): state change: prepare -> config (reason 'none') [40 50 0]
NetworkManager[936]: <info>  [1495625898.1953] device (wlp2s0): Activation: (wifi) access point 'true_home2G_b68' has security, but secrets are required.
NetworkManager[936]: <info>  [1495625898.1953] device (wlp2s0): state change: config -> need-auth (reason 'none') [50 60 0]
May 24 13:38:43 dv-XPS-15-9550 NetworkManager[936]: <warn>  [1495625923.2170] device (wlp2s0): No agents were available for this request.
May 24 13:38:43 dv-XPS-15-9550 NetworkManager[936]: <info>  [1495625923.2171] device (wlp2s0): state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 24 13:38:43 dv-XPS-15-9550 gnome-session[1940]: (nm-applet:2168): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 24 13:38:43 dv-XPS-15-9550 NetworkManager[936]: <info>  [1495625923.2174] manager: NetworkManager state is now DISCONNECTED
May 24 13:38:43 dv-XPS-15-9550 NetworkManager[936]: <warn>  [1495625923.2184] device (wlp2s0): Activation: failed for connection 'true_home2G_b68'
May 24 13:38:43 dv-XPS-15-9550 NetworkManager[936]: <info>  [1495625923.2199] device (wlp2s0): state change: failed -> disconnected (reason 'none') [120 30 0]
May 24 13:38:43 dv-XPS-15-9550 kernel: [32456.473864] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready

```

I don't know if it matters, I think this problem started after installation of [anbox]("https://anbox.io/"). After that, in ifconfig results, wlp2s0 was replaced by another entry (anboxlo if I remember correctly). I have uninstall anbox and tried to put back the old settings, but no success.

Please help me here. I will be available to give more information as required.

---

### Post by dxvargas on 2017-05-25
Here it is a full report for my network connections (based on [github.com/UbuntuForums/wireless-info]("https://github.com/UbuntuForums/wireless-info")): [paste.ubuntu.com/24656887]("http://paste.ubuntu.com/24656887/")

---

### Post by dxvargas on 2017-05-26
One think I noticed is that I have no file  /etc/wpa_supplicant.conf which I see that should exist in many places. I  do have thse files in /etc/wpa_supplicant: action_wpa.sh, functions.sh,  ifupdown.sh

---

