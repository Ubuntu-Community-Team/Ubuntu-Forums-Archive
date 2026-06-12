---
title: "No wireless since kernel update"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by AndyC_772 on 2007-02-09
I have a Dell Inspiron 8200 laptop with a bcm4306 based wireless 802.11g card. I'm using ndiswrapper, and all was well until this evening's kernel update.

Now after rebooting I have no wireless at all - the LED on my laptop is off, and Network Manager doesn't list a wireless adapter at all.

dmesg reports:
```
[17180091.844000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180091.848000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17180091.848000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180113.332000] nfs: server 192.168.1.201 not responding, still trying
[17180131.760000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180131.760000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17180131.764000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180211.344000] nfs: server 192.168.1.201 OK

```

... and 'sudo modprobe ndiswrapper' gives:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

Any suggestions please?

Andy.

---

### Post by deadowl on 2007-02-09
Okay, this definitely better describes what happened to me than in the last thread. But at least the last thread I looked in helped me to switch back to a wired connection. Well, except for my WiFi led is on. With wired connections in most of the classrooms I have, I could do that, but my wire is like 50' (both a convenience and inconvenience, you see?). In any case, I think the bulk of the problem is definitely ndiswrapper. First I'll try uninstalling ndiswrapper and see if my wireless gets magically detected again, then if there is still no detection I'll install ndiswrapper again and see if it will rework its own magic.

NEW DISCOVERY #1: the Windows Wireless Drivers gui frontend (ndisgtk) doesn't list any drivers for me, perhaps they have to be reloaded.
NEW DISCOVERY #2: uninstalling NDISWrapper does absolutely nothing (used remove, NOT complete remove on Synaptic Package Manager)!
NEW DISCOVERY #3: after reinstalling NDISWrapper, all of a sudden it ndisgtk shows bcmwl5, states that the hardware is present (small victory).
NEW DISCOVERY #4: Network Manager still doesn't show Wireless, will try reboot.
NEW DISCOVERY #5: SOMEONE PLEASE HELP ME!!!! (lol)

---

### Post by jimmymac on 2007-02-10
I had the same problem although not since kernel update.

I've spent a little time away from Ubuntu having tried different distros.  But hey I came back to this one!!  Only with a newer version out, couldn't get my wireless working.

I removed ndiswrapper-utils.
Installed ndiswrapper-utils-1.8  &  ndiswrapper-common

Did all the normal ndiswrapper stuff after and hey presto, it's alive!

HTH

Cheers,

Jimmy

---

### Post by deadowl on 2007-02-10
Thanks for helping me get this done before I actually needed to use wireless again :P.

---

### Post by lojic on 2007-02-10
If you're still having trouble after the -11 update, can you post your wireless hardware info on the following thread?

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

Thanks!

---

### Post by jimmymac on 2007-02-12
I presume that worked then,

In which case, glad to be of service!

It's good to be of help after the masses of help I've had on here!

Cheers,

Jimmy

---

### Post by AndyC_772 on 2007-02-12
Reinstalling ndiswrapper-common and ndiswrapper-utils-1.8 seemed to fix it for now. I've no idea what actually broke it in the first place, though.

---

### Post by trommas on 2007-02-14
> **jimmymac said:**
> I had the same problem although not since kernel update.

I've spent a little time away from Ubuntu having tried different distros.  But hey I came back to this one!!  Only with a newer version out, couldn't get my wireless working.

I removed ndiswrapper-utils.
Installed ndiswrapper-utils-1.8  &  ndiswrapper-common

Did all the normal ndiswrapper stuff after and hey presto, it's alive!

HTH

Cheers,

Jimmy


What is the terminal-code to get this done?

---

### Post by jimmymac on 2007-02-15
sudo aptitude remove ndiswrapper-utils

sudo aptitude install ndiswrapper-utils-1.8 ndiswrapper-common

HTH

Jimmy

---

