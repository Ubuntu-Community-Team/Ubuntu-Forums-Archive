---
title: "Changing NICs out in Gutsy"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by Levander on 2007-11-06
I just popped out my old Realtek NIC and popped in a new Linksys one.  I was thinking that rebooting, Gutsy would find my new NIC, load the appropriate driver, and I would be good to go.

It does look like Gutsy found my new NIC.  On startup I get a line like:

```

eth0: ADMtek Comet rev 17 at 0xf800, 00:02:2A:B8:23:D7, IRQ 5.

```

And, lsmod does show that the tulip driver is loaded.  The 8139too driver that my old NIC used is not loaded anymore.

But, 'ping <hostname>' just gives me an unknown hostname error.  'sudo /etc/init.d/networking restart' gives me something like:

```

eth0: Error while getting interface flags: No such device
SCIOCSCIFADDR: No such device

```

What step am I missing in installing this new NIC?

---

### Post by Mithrilhall on 2007-11-06
I'm assuming an ifconfig only shows eth0?

Also, if you open /etc/udev/rules.d/30-net_persistent_names.rules (or something like that) with nano or some other editor what do you see (post results please)?

---

### Post by Levander on 2007-11-06
ifconfig only show "lo" - which I assume is for local.

I would post that file, but the machine it is on currently has no network access.  There is no file named exactly what you mention.  But there is a /etc/udev/rules.d/70-persistent-net-rules file.  It contains two uncommented lines that start with the word "SUBSYSTEM".  One is for eth0, which describes my old Realtek card.  I can tell because it mentions the 8139too driver which is what it used.  The other is for eth1, which describes my new card.  I can tell because it mentions the tulip driver, which is what my new card uses.

---

### Post by Levander on 2007-11-06
Oh wait, I got the description of /etc/udev/rules.d/70-persisten-net-rules wrong.

I know the eth0 line is for my old Realtek card because it has the MAC address of the old card on it.

I know the eth1 line is for my new Linksys card because it has the MAC address of the new card on it.

Is it safe to just delete that 70-persistent-net.rules file?  Will it definitely get regenerated on reboot?

---

### Post by Levander on 2007-11-06
Just deleting 70-persisten-net.rules did work.  It was regenerated on boot.  Now, it only has one SUBSYSTEM line for my new NIC and eth0.

After rebooting I did a "ping <hostname>" and got the "Desination unreachable error".  Checking and seeing what was wrong now, I noticed I did not have the network cable plugged into that new NIC tightly.  I plugged it in tightly and "/etc/init.d/networking restart", networking is working again.

Thanks mithirall, where to look for the appropriate file was apparently all I needed.

With my current setup, I'm thinking I'm going to have to switch out NICs on that computer again here pretty soon.  This time I'll make sure I have the network cable plugged in correctly, and if the same thing happens, I'll file a bug.

---

### Post by Levander on 2007-11-06
How do I mark this thread "[SOLVED]".  I clicked the edito button in the original post in this thread, but it won't let me modify the title...

---

