---
title: "NetManager's Wifi can't connect"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by jtodd.fr on 2018-06-20
Dell precision 5520
kernel 4.13.0-45-generic
Ubuntu 16.04 LTS

My wifi suddently doesn't connect any more. Don't know what goes wrong. I completely have no idea and don't know when this happened because I switched to wireless for a while. But sometime I need to use wireless when I move to other place. Now the only message in /var/log/syslog I find related is as below.  

```

Jun 20 17:52:40 u NetworkManager[1051]: <info>  [1529509960.9362] device (wlp2s0): state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jun 20 17:52:40 u NetworkManager[1051]: <info>  [1529509960.9366] manager: NetworkManager state is now CONNECTED_LOCAL
Jun 20 17:52:40 u NetworkManager[1051]: <info>  [1529509960.9369] policy: disabling autoconnect for connection '<ap name>'.
Jun 20 17:52:40 u NetworkManager[1051]: <warn>  [1529509960.9375] device (wlp2s0): Activation: failed for connection '<ap name>'
Jun 20 17:52:40 u NetworkManager[1051]: <info>  [1529509960.9397] device (wlp2s0): state change: failed -> disconnected (reason 'none') [120 30 0]

```

Where to debug this problem? Or how to fix it? Thanks

---

