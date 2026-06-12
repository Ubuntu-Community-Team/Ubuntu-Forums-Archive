---
title: "Ubuntu 12.04 LTS scripts in /if-up.d not executed"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by thomas32 on 2015-01-29
Hello Everybody,

Since yesterday I've been trying to achieve something:


**System:**
Ubuntu 12.04 LTS, Network-Manager package is not installed


**Goal:**
Every time, the *eth0* network interface is started (*if-up.d*) we want to unmount and remount some external sources (different machine) with sshfs OR
Every time, the machine is started/rebooted we want to unmount and remount some external sources with sshfs (different machine)


**Things I tried so far:**
[LIST]
[*]Mount in `rc.local` (doesn't work, seems like network is not established then)
[*]Mount automatically when interfaces are up (`if-up.d`, doesn't work, not executed)
[*]Mount explicitly through `/etc/network/interfaces` with post-up at the end of the `eth0` configuration (doesn't work, not executed)
[/LIST]


**Problem:**
[LIST]
[*]It seems that the scripts in `/etc/network/if-up.d/` are not even executed
[*]It seems the post-up command in `/etc/network/interfaces` is ignored
[*]We are not able to mount the external directory after computer restart / network restart
[/LIST]


**Additional information:**
[LIST]
[*]*/etc/network/interfaces* contains *eth0* interface.
[*]*eth0* connection is automatically started
[*]*eth0* is a static interface
[*]post-up *{FULL_PATH_TO_SCRIPT}/[un]mount-vcomhub01* is not executed either
[*]The two scripts *mount-vcomhub01* and *unmount-vcomhub01* are valid, no problem with execution. The mount is successfully mounted when running this script.
[*]The two scripts are in the correct format (executable, without `.sh` ending)
[*]*/etc/network/run/ifstate* does not contain eth0=eth0 after reboot even though the connection is established
[/LIST]


Does anybody have an idea what could be the problem and what else we could try?
I'm happy about any input as I'm a bit clueless at the moment

---

### Post by steeldriver on 2015-01-29
Sorry if this is obvious but have you tried mounting it via the fstab with an explicit _netdev option?

---

### Post by thomas32 on 2015-01-29
To be honest, no I didn't try it in fstab yet.
The mount requires a password to be entered which is done via a echo "something" | sshfs which I think is not possible like that in fstab. Means we would probably need to setup some authorization file for this to work in fstab I think. (Which could definitely be worth a try)

But for that I would then probably contact our system administrator who was actually working on this issue the last two months. I was just so upset that it still doesn't work and wanted to give myself a try.

Thank you for your input :)

Are the other ideas around?

---

### Post by steeldriver on 2015-01-29
Yes you would need to set up certificate based authentication I think - but you should probably be doing that anyway

---

### Post by thomas32 on 2015-01-29
Okay, so the task will be redirected to our system administrator again if I don't find another solution.

---

