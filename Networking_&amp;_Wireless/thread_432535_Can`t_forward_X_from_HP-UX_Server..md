---
title: "Can`t forward X from HP-UX Server."
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by radm on 2007-05-04
I try forward X from my HP-UX server, but it always send me next message:

Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset


Can I set against somebody ?

---

### Post by kkovach on 2007-07-02
I am seeing this similar problem after upgrading to Feisty just a couple weeks ago.  I'm no longer able to forward X from other linux boxes to my laptop.  Any information would be appreciated.

---

### Post by radm on 2007-07-03
I add next step to fix my problem:


Perform these steps on the HP-UX system:

1. Edit the /etc/rc.config.d/xfs by setting RUN_X_FONT_SERVER=1.

2. Use your root ID to execute the '/sbin/init.d/xfs start' command.

Perform these steps on the remote system:

1. Log in as the user who will run program.

2. Execute the 'xset +fp tcp/<hp-ux_hostname>:7000' command.

3. Execute the 'xset fp rehash' command.

4. Execute the 'xset -q' command.

5. Perform an rlogin to the HP system.

6. Execute the  command.

---

