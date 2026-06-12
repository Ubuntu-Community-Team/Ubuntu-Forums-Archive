---
title: "vino-server failing on boot (14.04)"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by WB0HYQ on 2015-12-17
Lately (over the past couple of weeks) when I boot into Ubuntu/Xubuntu 14.04, I get a system error that "vino-server" failed to start. When I run the command manually, I get this:

```

bill@bill-UBU:~$ /usr/lib/vino/vino-server

(vino-server:3606): EggSMClient-CRITICAL **: egg_sm_client_set_mode: assertion 'global_client == NULL || global_client_mode == EGG_SM_CLIENT_MODE_DISABLED' failed
17/12/2015 10:21:05 AM Autoprobing TCP port in (all) network interface
17/12/2015 10:21:05 AM Listening IPv6://[::]:5900
17/12/2015 10:21:05 AM Listening IPv4://0.0.0.0:5900
17/12/2015 10:21:05 AM Autoprobing selected port 5900
17/12/2015 10:21:05 AM Advertising security type: 'TLS' (18)
17/12/2015 10:21:05 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
17/12/2015 10:21:05 AM Listening IPv6://[::]:5900
17/12/2015 10:21:05 AM Listening IPv4://0.0.0.0:5900
17/12/2015 10:21:05 AM Clearing securityTypes
17/12/2015 10:21:05 AM Advertising security type: 'TLS' (18)
17/12/2015 10:21:05 AM Clearing securityTypes
17/12/2015 10:21:05 AM Advertising security type: 'TLS' (18)
17/12/2015 10:21:05 AM Advertising authentication type: 'No Authentication' (1)
17/12/2015 10:21:05 AM Re-binding socket to listen for VNC connections on TCP port 5900 in (all) interface
17/12/2015 10:21:05 AM Listening IPv6://[::]:5900
17/12/2015 10:21:05 AM Listening IPv4://0.0.0.0:5900
17/12/2015 10:21:05 AM Clearing securityTypes
17/12/2015 10:21:05 AM Clearing authTypes
17/12/2015 10:21:05 AM Advertising security type: 'TLS' (18)
17/12/2015 10:21:05 AM Advertising authentication type: 'VNC Authentication' (2)
connect: Operation now in progress
connect: Operation now in progress
connect: Operation now in progress
*** Error in `/usr/lib/vino/vino-server': free(): invalid pointer: 0x00007feddbe4f7b8 ***
Aborted (core dumped)
bill@bill-UBU:~$ 


```

This happens on my main (64-bit) desktop (running XFCE4) and on my 32-bit laptop (default Ubuntu) Unity). I know it has to do with remote access to the computer. I rarely do that, and if I do, I can connect (from my Windows 7 machines), but all I get is a grey screen and nothing further. The systems connect, but that's it. I think this may be a separate problem because I have NEVER been able to connect since upgrading to Ubuntu 14.04.

Bill

---

### Post by deepakdeshp on 2015-12-17
Please see if this helps

[http://ubuntuforums.org/showthread.php?t=2282400](http://ubuntuforums.org/showthread.php?t=2282400)

---

### Post by WB0HYQ on 2015-12-18
No, that thread only reiterates the advice to try and start it manually. My example above was run a half-hour after boot and login, yet it still failed.

Bill

---

### Post by steeldriver on 2015-12-18
```

connect: Operation now in progress
connect: Operation now in progress
connect: Operation now in progress

```

Is that *you* trying to connect, or somebody else? is the port open to the internet?

---

### Post by WB0HYQ on 2015-12-18
No. Not me, nor anyone else on my LAN that I know of. I do get those three statements after every attempt to start the server.

Bill

---

