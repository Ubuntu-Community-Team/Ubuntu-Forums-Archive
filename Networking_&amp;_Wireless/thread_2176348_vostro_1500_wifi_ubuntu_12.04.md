---
title: "vostro 1500 wifi ubuntu 12.04"
date: 2013-09-23
forum: Networking &amp; Wireless
---

### Post by chrtylee on 2013-09-23
I tried doing a terminal install that i found on the forums and i got this message:

An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting.



also when trying the popup about restricted software it just keeps failing, please help

---

### Post by varunendra on 2013-09-23
If you even tried installing the restricted driver, we need to purge it first -
```
sudo apt-get purge bcmwl-kernel-source
```

Then install what is actually needed for your card, and load the driver -
```
sudo apt-get install firmware-b43-lpphy-installer
sudo modprobe -rv b43
sudo modprobe -v b43
```
Is wireless up?

---

### Post by chrtylee on 2013-09-23
the wireless was working to the point that i could see connections and supposedly connect to them, but the internet was not accessible after connecting, and i seem to have to manually connect by adding a connection. not sure if that is normal or not.



never mind now its suddenly working.

---

### Post by chrtylee on 2013-09-23
ill create another thread if needed, but how do i disable the touchpad when using an external mouse?

---

### Post by varunendra on 2013-09-23
> **chrtylee said:**
> never mind now its suddenly working.

Keep it on test-bed for a while, do a couple of reboots to see if it's stable and consistent. Post back if a problem occurs (I hope there won't be any).

If everything is fine, please mark the thread as [SOLVED]. Thanks !

---

### Post by varunendra on 2013-09-23
> **chrtylee said:**
> ill create another thread if needed, but how do i disable the touchpad when using an external mouse?

Doesn't your laptop have a shortcut key to do that? It is usually a hardware feature in most laptops/netbooks these days. If not, start a new thread and give me its link. If no elegant solution was found, I think I can do it the ugly way - by kicking the relevant driver out. ;)

---

