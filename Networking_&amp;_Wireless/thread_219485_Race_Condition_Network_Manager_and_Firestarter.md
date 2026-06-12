---
title: "Race Condition: Network Manager and Firestarter"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by gmc on 2006-07-20
HI Folks,

Does anyone know of a way to delay firestarter from automatically starting before network manager establishes a wireless connection.

As it is now, firestarter complains that the network interface doesn't exist, a few minutes later network manager reports a successful connection to the wireless router, now I have to restart firestarter to firewall the (wireless) network interface.

G.

---

### Post by geco on 2006-07-20
if you launch firestarter from a script - as I think - you may use the "sleep" command...
now you have something as
```

#!/bin/sh

#your main code

firestarter

```

just add "sleep N" before "firestarter", where N is the delay in seconds

---

### Post by gmc on 2006-07-20
> **geco said:**
> if you launch firestarter from a script - as I think - you may use the "sleep" command...
now you have something as
```

#!/bin/sh

#your main code

firestarter

```

just add "sleep N" before "firestarter", where N is the delay in seconds

That is an option, though I was thinking more along the lines of a bash script that tests if the interface is up and then executes firestarter. Unfortunately I've not had any luck finding a sample script that demonstates how to test for the existance of eth0/1, I can canabalize.

My other thought was to put a symlink in /etc/network/if-up.d to firestarter, but it appears network manager doesn't read that directory for scripts to run. :-(

G.

---

### Post by endfx on 2006-07-20
If you want a simple bash script just grep the contents of ifconfig

Here is the psudo code:

output1=`ifconfig eth0 | grep "error"`
output2=`ifconfig eth1 | grep "error"`

if both results contain "error" then neither of them are configured.

example: type "ifconfig eth333" at a command propmt to see the error that you get when an interface doesn't exist.

---

