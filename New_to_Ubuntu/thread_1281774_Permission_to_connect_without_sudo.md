---
title: "Permission to connect without sudo"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by Clopin on 2009-10-03
Heya.

I bought a M-Audio FireWire Solo today, and believe I need to run the qjackctrl (JACK Control Panel) using sudo, otherwise it won't give me permission.

**How would I make the app have permission to do the connections without doing "sudo"?**

The error I get is (As stated, I do not get this error when doing sudo):
```
21:49:20.380 Patchbay deactivated.
21:49:20.394 Statistics reset.
21:49:20.489 ALSA connection graph change.
21:49:20.736 ALSA connection change.
21:49:26.453 Startup script...
21:49:26.454 artsshell -q terminate
sh: artsshell: not found
21:49:26.855 Startup script terminated with exit status=32512.
21:49:26.855 JACK is starting...
21:49:26.855 /usr/bin/jackd -v -R -P89 -t2000 -dfreebob -dhw:0 -r48000 -p256 -n3 -D
21:49:26.856 JACK was started with PID=4205.
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_net.so
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
cannot use real-time scheduling (FIFO at priority 10) [for thread -1211025728, from thread -1211025728] (1: Operation not permitted)
cannot create engine
cleaning up shared memory
cleaning up files
unregistering server `default'
21:49:26.870 JACK was stopped successfully.
21:49:26.870 Post-shutdown script...
21:49:26.871 killall jackd
jackd: no process killed
21:49:27.276 Post-shutdown script terminated with exit status=256.
21:49:28.941 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

I'm installing it all using the guide here:
[http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/](http://westcoastsuccess.wordpress.com/2008/03/23/m-audio-firewire-solo-ubuntu/)

The problem is at the step after starting Ardour, and then setting the Connections using the JACK Control Panel. If I run the control panel in sudo I can only connect with Ardour if it's in sudo as well. But if I run ardour in sudo, it won't find my audio drivers, and therefore not play anything.

---

### Post by inobe on 2009-10-03
system> administration> users and groups> click your user name> properties> tick use sound devices.

---

### Post by Clopin on 2009-10-03
Already got all of them ticked.

---

### Post by inobe on 2009-10-03
> **Clopin said:**
> Already got all of them ticked.

then i don't understand why it isn't working unless you followed a guide that could have "possibly" broke something, anything is following guides.

if you haven't logged out and back in after the changes ?


make sure no devices are connected prior to changes.

---

