---
title: "Lenovo ThinkPad P14s Gen 2a Cellular Issue on 22.04 LTS"
date: 2022-11-13
forum: Networking &amp; Wireless
---

### Post by ciaran4 on 2022-11-13
Hello,

I have a Lenovo ThinkPad P14s Gen 2a
I bought it with windows with the EM120R-GL m.2 3042 cellular card.
I have decided to switch from windows to ubuntu

I installed 22.04 LTS and everything seems to work except...

when I try to use the gnome widget to activate cellular it just keeps flickering connecting then greyed out

if I check on modem manager
```

&#9679; ModemManager.service - Modem Manager     Loaded: loaded (/lib/systemd/system/ModemManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-11-13 00:29:26 MST; 12h ago
   Main PID: 2732 (ModemManager)
      Tasks: 5 (limit: 33324)
     Memory: 8.3M
        CPU: 17.487s
     CGroup: /system.slice/ModemManager.service
             &#9500;&#9472;2732 /usr/sbin/ModemManager
             &#9492;&#9472;4537 /usr/libexec/mbim-proxy


Nov 13 11:55:01 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: [/dev/wwan0mbim0] Registered 'pdc' (version 1.0) client with ID '1'
Nov 13 11:55:01 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <info>  [modem1] QMI-based capability and mode switching support enabled
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <warn>  [modem1/sim2] couldn't load list of emergency numbers: Failed to parse CRSM query result '+CRSM: 148,8,""'
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <warn>  [modem1/sim2] couldn't load list of preferred networks: Operation not allowed
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <info>  [modem1] state changed (unknown -> disabled)
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <info>  [modem1] state changed (disabled -> enabling)
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <warn>  [modem1] Busy
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <warn>  [modem1] Busy
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <warn>  [modem1] couldn't enable interface: 'Invalid transition'
Nov 13 11:55:20 ciaran-ThinkPad-P14s-Gen-2a ModemManager[2732]: <info>  [modem1] state changed (enabling -> disabled)



```

after some googling I think I am running into the "fcc lock" issue
I installed the fcc lock fix packages for the thinkpad x1 but they arent working for me.

any suggestions where to go from here?
do I need to buy a different cellular card like an EM06-A ?

Thanks

---

