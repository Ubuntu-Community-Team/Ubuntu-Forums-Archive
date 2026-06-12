---
title: "Maverick slower and slower"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by Perseverance on 2010-11-06
Hi. I got a thing that is driving me crazy lately. Each and every time i boot it takes longer and longer.Also my drum roll is delayed 3-4 secs after the login screen is displayed.For 3-4 seconds after i log in the speaker volume icon in the indicator applet is empty(i dont know what that means as if i mute it it stays filled). After that i have no problems. I use to do a lot of reboots since i have to use my windows OS for Autocad and Solidworks. The problem occurred about a week after i installed 10.10 x64. I dont think it is a machine issue since 10.04 was swift as hell. However my params are:
Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz
4 GB DDR3
1GB ATI Mobility 5650
Western Digital 500 GB
Kernel - 2.6.35-22-generic
So any suggestions ?Can my current kernel drivers have some issues with x64 architecture.I didn't want to upgrade to 2.6.36 since i think it is not finally released and if it is it will come with update (right?).

---

### Post by HermanAB on 2010-11-06
Howdy,

Some ideas:
Run top to see what is going on.

Browse the startup system log: 
$ sudo tail -n 1000 -f /var/log/messages | less

Check your DNS with dig.

---

### Post by sikander3786 on 2010-11-06
Hi.

How much time does it actually take to boot up the system to the desktop?

Did you install compiz?

Did you remember adding any custom applications under System > Administration > Startup Applications?

Is any USB thumb drive plugged in while you boot?

And I am sure it is a clean install not and upgrade?

Yes the new kernel will come with the updates. Hang in for that to arrive.

---

### Post by Perseverance on 2010-11-06
How much time does it actually take to boot up the system to the desktop? - initialy it was around 10 sec and there was no sound delay. Now arround 20-25 and 4-5 sound delay.

Did you install compiz? - No , i Havent. I just use normal visual efects from ubuntu appearances

Did you remember adding any custom applications under System > Administration > Startup Applications? I added screenlet applet and removed it immediately since i did not liked it. Also i have disabled the startup of ubuntu one  , SSH , Remote desctop, printer queue applet and visual assistance

Is any USB thumb drive plugged in while you boot? - just the wireless pointer receiver

And I am sure it is a clean install not and upgrade? Clean install from flash Drive.

Yes the new kernel will come with the updates. Hang in for that to arrive.

Could there be issue with the start up of network manager since i have pre-up restoring of iptables settings ?

And does the login drumroll suggests that something else is loading way too slow since it is a start up application too ?

What point DNS Server can have . I have found mine at [http://www.dnsserverlist.org](http://www.dnsserverlist.org)

---

### Post by Perseverance on 2010-11-06
via the tail of the boot log i see this strange time consuming thing : 
```
Nov  6 21:24:23 perseverance kernel: Kernel logging (proc) stopped.
Nov  6 21:24:55 perseverance kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov  6 21:24:55 perseverance rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1093" x-info="http://www.rsyslog.com"] (re)start
Nov  6 21:24:55 perseverance rsyslogd: rsyslogd's groupid changed to 103
Nov  6 21:24:55 perseverance rsyslogd: rsyslogd's userid changed to 101
Nov  6 21:24:55 perseverance kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  6 21:24:55 perseverance kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  6 21:24:55 perseverance kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (Ubuntu 2.6.35-22.35-generic 2.6.35.4) 
```

And 

```
Nov  6 21:24:56 perseverance kernel: [   14.981443] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov  6 21:24:56 perseverance kernel: [   14.981447] [fglrx] Reserved FB block: Unshared offset:f941000, size:3bf000 
Nov  6 21:24:56 perseverance kernel: [   14.981450] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Nov  6 21:25:04 perseverance kernel: [   23.393709] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  6 21:25:15 perseverance kernel: [   33.898252] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by Perseverance on 2010-11-11
Anyone ?

---

### Post by davidmohammed on 2010-11-11
maybe [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913")?  Reading through that, there are various suggestions as to fixes.

---

