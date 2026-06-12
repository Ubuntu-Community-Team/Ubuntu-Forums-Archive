---
title: "router / wireless inaccessible"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by S_D_T on 2010-11-21
I finally made to leap to Ubuntu. Ditched windows and installed 10.10. on a clean drive.

When I first boot Ubuntu can't access my wireless connection, and I'm unable to access
my router.
After rebooting (sometimes twice) everything works fine.

Hope someone can help, I'm totally new to Ubuntu so simple instructions would be nice thanks.

---

### Post by apollothethird on 2010-11-21
> **S_D_T said:**
> I finally made to leap to Ubuntu. Ditched windows and installed 10.10. on a clean drive.

When I first boot Ubuntu can't access my wireless connection, and I'm unable to access
my router.
After rebooting (sometimes twice) everything works fine.

Hope someone can help, I'm totally new to Ubuntu so simple instructions would be nice thanks.

Set the option “Available to all users” in the NetworkManager Applet.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by S_D_T on 2010-11-21
"available to all users" option is already set

---

### Post by apollothethird on 2010-11-21
> **S_D_T said:**
> "available to all users" option is already set

What is the strength shown for your wireless signal.  Did you try repositioning the Wireless Router for a more consistent and stronger signal?

Consider changing the channel at the router.  There are occasions where certain signals become corrupted due to wireless phone traffic.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by S_D_T on 2010-11-23
I've messed about with channels, my signal strength is currently @ 85%.
No difference.

I'm using an edimaxEW-7318USG  usb dongle. I should have said before..sorry

---

### Post by S_D_T on 2010-11-27
Don't know if this counts as a fix but..
If I boot without the dongle attached and then insert the dongle into it's usb port
it connects to the wlan just fine.

---

### Post by admiralspark on 2010-11-27
I'm assuming you're on a laptop? Regardless of whether you are or not, could you open a terminal and post the results of this command back here:
```
lspci | grep Network
```
So that we know what kind of wireless card you have. Make sure it's a capital N!

---

### Post by S_D_T on 2010-11-27
Tried that and nothing happened.

Not on a laptop using an old pc I was given

---

### Post by S_D_T on 2010-12-15
I got a new router and so far everything has worked fine. About a week now.

---

### Post by Hippytaff on 2010-12-15
with the wireless plugged in can you do
```

lsusb | grep -i net

```
and
```

sudo lshw -C network

```

---

