---
title: "dell wireless 1395 problem,,,PLZ help!!!!"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by xnuo on 2008-07-10
hi everyone, i am a beginner in linux and i'm having this problem in my system that i haven't been able to resolve... i have a dell vostro 1700 laptop,running ubuntu ultimate edition 1.8 and using a dell wireless 1395 as my wireless card (default for this laptop)

my problem began with the wireless not working (native drivers for linux don' seem to be available at the moment, or so i've read) so i decided to go the NDISWrapper way, using a tutorial that i found on the forum (blacklisting the bcm43xx drivers, installing ndiswrapper, getting the drivers from dell (i think they were the R174291 ones) loading the drivers from NDISwrapper,etc.) and presto! i had wifi working... the only bad thing was that i didn't find a way to make the wifi work at logon other than opening network connections, assigning the location and closing again...but that was not a problem for me)

4 days ago, i wanted to update the system, so i ran the update manager and afterwards i ran the ubuntu ultimate updater, tried to modify some things in my install (like themes, icons, etc) and since then, i have been getting the same messages all over (see the pictures for details) i see the drivers working in ndsiwrapper, but in hardware drivers they say "not in use", and i can see the wireless strength in the connections manager, but when i try to configure it using network tools, it says that it doesn't exist..

can anyone help me??? as i am a new user, don't know what to do...

thanks in advance

---

### Post by stats on 2008-07-10
the driver is in the repo

1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

EDIT: If the driver does not start when you logon, add 'wl' to the end of /etc/modules

---

### Post by xnuo on 2008-07-10
thanks stats, i will get on it as soon as i finish from work.
thank you very much.

---

