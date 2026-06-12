---
title: "[SOLVED] Wireless connected, but no net?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by tacticalbread on 2008-09-18
I was using wireless internet at my college, and I closed my laptop, and put it into sleep mode, but when I opened my laptop up again, the wireless internet wasn't working. It says that it's connected, signal strength 100%, but no pages will load, they just keep loading forever. I know it's not the internet's problem, because I'm using it now, via Ethernet, and I know the wireless isn't down, because I connected with my PSP just fine.

when I first installed Ubuntu, I installed NDISwrapper, and my wireless worked fine, and I haven't messed with that at all.

anyone know what I can do to fix it?

---

### Post by pytheas22 on 2008-09-18
If you type:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0
```

and wait a few seconds, then connect to the wireless network again, does it work?  If not, does it work if you do a full reboot of the computer?

If that doesn't help, the next time that this problem occurs, please run the following commands and post the output here:
```

dmesg | tail
lshw -C Network
ndiswrapper -l
ifconfig wlan0
cat /etc/resolv.conf
host google.com

```

---

### Post by tacticalbread on 2008-09-18
from the first command I got "ERROR: Module ndiswrapper does not exist in /proc/modules"

the second, nothing, so I guess that's what worked.

and the third "wlan0: error fetching interface information: Device not found"

but it worked!

thanks so much. :D

---

### Post by pytheas22 on 2008-09-18
It sounds then like the ndiswrapper module wasn't loaded after you resumed your computer.  Either it must have been unloaded by you or an application (not likely), or for some reason when you resumed, the module wasn't reinserted like it was supposed to be (more likely).

Perhaps this was just a one-time fluke, but if it happens again, let me know; you can write a script to automatically reinsert ndiswrapper (otherwise you'd have to run 'sudo modprobe ndiswrapper' manually after each resume, which is not a big deal but is probably a bit inconvenient).

---

### Post by tacticalbread on 2008-09-18
well, this is the first time this has happened, and I've been using Ubuntu only for about a week now.

if it happens again, I'll post here.

thanks again for your help. (:

---

### Post by tacticalbread on 2008-09-19
sorry to double post, but it happened again, after putting in sleep mode.

I tried sudo rmmod ndiswrapper, then sudo modprobe ndiswrapper, and it still didn't work.

I shut down my PC, and came to my friends house, turned it on, and it worked fine. -_-

I have yet to try it at home, but I will very soon.

edit: home now, and it works fine. I resumed it from sleep mode, and no problems.

---

### Post by pytheas22 on 2008-09-19
That's strange.  Maybe the behavior is not as predictable as we thought then.  The next time the wireless isn't working after being in sleep mode, please post the output of:
```

lsmod | grep ndis
dmesg | grep -e ndis -e wlan -e adio -e rror
iwconfig
iwlist scan
```

---

