---
title: "JACK Control can't start Server"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-16
Output from JACK Control:
```
17:29:47.346 Patchbay deactivated.
17:29:47.350 Statistics reset.
17:29:47.387 ALSA connection graph change.
17:29:47.585 ALSA connection change.
17:29:50.228 Startup script...
17:29:50.228 artsshell -q terminate
sh: artsshell: not found
17:29:50.630 Startup script terminated with exit status=32512.
17:29:50.630 JACK is starting...
17:29:50.630 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
17:29:50.631 JACK was started with PID=19216.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 2014832368, from thread 2014832368] (1: Operation not permitted)
cannot create engine
17:29:50.770 JACK was stopped successfully.
17:29:50.770 Post-shutdown script...
17:29:50.771 killall jackd
jackd: no process found
17:29:51.179 Post-shutdown script terminated with exit status=256.
17:29:52.791 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by nathan726 on 2009-11-16
Go into setup (on the settings tab, under Parameters) clear the "Realtime" checkbox.

---

### Post by coldReactive on 2009-11-16
> **nathan726 said:**
> Go into setup (on the settings tab, under Parameters) clear the "Realtime" checkbox.

Thank you, that solved it.

---

