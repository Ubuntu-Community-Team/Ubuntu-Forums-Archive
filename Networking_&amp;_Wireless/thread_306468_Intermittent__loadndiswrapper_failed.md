---
title: "Intermittent : loadndiswrapper failed"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by jazzwhistle on 2006-11-25
Hello

My version and settings for ndiswrapper seem to change at random - and the strangest part is that it often initializes with no problem, but on the next reboot I may get a different version, different settings and failure.  Or I get the same version, same settings but it will fail to initialize  ](*,) 

Once the system boots up correctly and lsmod shows ndiswrapper then I know wlan0 is going to be there and everything is great til I reboot.

I can discern no pattern...help!

*********

SYS ERRORS:
ndiswrapper 1.8

On booting up I sometimes get wireless failure with this sys error:

```
ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512)
ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
```

However sometimes it works:

```
usbcore: registered new driver ndiswrapper
ndiswrapper: driver wusb54 () loaded
ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
```

************

and sometimes version 1.22 pops up, and fails like this:

```
ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536)
ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
```

but sometimes it succeeds beautifully like this:

```
usbcore: registered new driver ndiswrapper
ndiswrapper: driver wusb54 () loaded
ndiswrapper version 1.22 loaded (preempt=no,smp=no)
```

However it can also fail like this:

```
ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536)
ndiswrapper version 1.22 loaded (preempt=no,smp=no)
```

---

