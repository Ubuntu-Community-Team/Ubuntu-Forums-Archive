---
title: "Wireless doesnt work after hibernation"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by Kavjik on 2007-08-03
If i do the following:
1. Hibernate Ubuntu
2. Start Windows XP.
3. Shutdown or Hibernate Windows XP
4. Resume Ubuntu.

Then Wireless networking wont work.
When i see a list over the network cards, then Ubuntu thinks that my wireless is a standard Non Wireless card:confused:

It takes a lot of time to Boot when i havn't hibernated, so i realy want it to work.

My computer is a HP Pavillion dv2130ea.

Sorry if my english is bad.

---

### Post by noob12 on 2007-08-03
This might be a bug, but there might be workarounds.  

First try **sudo /etc/init.d/networking restart** to see if that works.  

We can probably do better, but we need to understand more about whats going on.

Can you check your BIOS settings to see if wireless is enabled by default on startup?

Can you post the output of these commands before hibernation, and then again after resuming Ubuntu?

```

lshw -C network

ifconfig -a

iwconfig

```

Also what version of Ubuntu are you running and can you please post **uname -rv**

---

### Post by Kavjik on 2007-08-03
I cant replicate the problem, maybe thats because i have uninstalled som KDE Networking tools that i didn't need (I had them because of problems with Samba.)

If it happens again, then i will post the output of those commands.

But i did do the uname -rv:
2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007

---

