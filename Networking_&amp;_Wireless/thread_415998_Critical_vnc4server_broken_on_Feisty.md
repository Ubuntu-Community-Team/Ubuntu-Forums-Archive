---
title: "Critical: vnc4server broken on Feisty"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Emblem Parade on 2007-04-20
Help!

On Edgy, I used Grumpy Mole's excellent tutorial for VNC:

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)

Many people who followed the tutorial found out that a security fix on Edgy had broken vnc4server, so that our clients would close after authentication with an "End of Stream" message. This problem was solvable by downgrading, thus:

sudo aptitude install vnc4server/edgy

Now, we all hoped that Feisty would have this mess fixed. Unfortunately, I just upgraded to Feisty and it's still broken. Much worse is that I do not see any way I can downgrade vnc4server.

Please, whoever is maintaining this package, can you fix this? I'm sure this affects a very large number of users who rely on VNC. I'm currently stuck with a headless Feisty machine that I cannot access.

In the meantime, any ideas for a workaround?

---

### Post by bnuytten on 2007-04-21
> **Emblem Parade said:**
> In the meantime, any ideas for a workaround?

On Ubuntu desktop: System > Preference > Remote Desktop. It starts vino server. Just tested and could connect to my Feisty machine using realVNC client on Windows.

---

