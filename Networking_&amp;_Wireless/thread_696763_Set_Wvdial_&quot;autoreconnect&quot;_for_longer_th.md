---
title: "Set Wvdial &quot;autoreconnect&quot; for longer than 5 seconds?"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by Mellowdrone on 2008-02-14
First, let me begin the post by saying wvdial does execute for me and does allow me to have some form of an internet connection. However, as I'm using a modem that takes longer than five seconds to reset (10~15 would be it's ideal time), wvdial completely drops out it's connection and doesn't reconnect, see below:

> WvDial<*1>: Disconnecting at Thu Feb 14 06:20:20 2008
WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
WvDial<*1>: man pppd explains pppd error codes in more detail.
WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds
WvDial<Err>: Cannot open /dev/modem: No such file or directory
WvDial<Err>: Cannot open /dev/modem: No such file or directory
WvDial<Err>: Cannot open /dev/modem: No such file or directory
WvDial<*1>: Disconnecting at Thu Feb 14 06:20:20 2008
len@enigmas-nightmare:~$


Why does this hinder me? Easy - this computer is a 24/7 connected machine, regardless of whether or not I'm here. With the modem taking 10~15 seconds to reset as stated above, wvdial is, for my situation, slightly off, but it's just enough to make using Wvdial for me almost pointless.

How long has this been ongoing? It doesn't matter the modem I use nor the amount of time it's been ongoing, the whole situation is absolutely frustrating. I've used four or five different modems with wvdial, all with differing results and some with very similar results. The one I'm currently using just happens to be my favorite of the crew.

Wvdial only offers an automatic reconnection time of 5 seconds to my current knowledge in regards to it. I've looked for settings via Google, I've man'd wvdial and wvdialconf, but both to no avail. Is there a wrap-around script someone has developed, a setting in wvdial I have simply (and idiotly) overlooked or missed, perhaps something that would help me through this situation?

---

