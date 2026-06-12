---
title: "router problems"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by xGutsAndGloryx on 2007-10-03
I am having router problems. If i connect my router all my computer accept the pc running ubuntu connects? does any know of any problem that wouldn't allow linux based computer to connect?

---

### Post by Lambert on 2007-10-03
> **xGutsAndGloryx said:**
> I am having router problems. If i connect my router all my computer accept the pc running ubuntu connects? does any know of any problem that wouldn't allow linux based computer to connect?

What router is this and are all of these hardwire connections?

---

### Post by xGutsAndGloryx on 2007-10-03
its a linksys router & yes all of them are hardwired.

---

### Post by Lambert on 2007-10-03
There's no general reason, just something is not working properly.

Need to troubleshoot

1. Is the device working/recognized hardware by ubuntu
2. Is their a driver for the device loaded for the device.
3. Are you using a static ip or dynamic ip setting
4. How are you trying to connect to the router? via network manager or have you tried another method such as command line

You can post the out put of the following commands here for someone to review.

```

lshw -C network
ifconfig

```

Precede those commands with sudo if it says you don't have permission.

---

