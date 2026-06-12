---
title: "Running Dionaea Honeypot"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by J3 Remy on 2013-10-02
I have installed Dionaea in a test environment and I have had success  getting it to start.  With that said however I have received the  following errors when I do run it:

processor processor.c:346-warning: bistreams/2013-10-1 <-> bistreams/%Y-%m-%d/
python module.c:330-warning start module.c [COLOR=SeaGreen](needs to be started?  how?)[/COLOR]
ihandlers dionaea/ihandlers.py:60-warning: START THE IHANDLERS [COLOR=SeaGreen](uncommented the "//" in the .conf still getting this error)[/COLOR]
log signals.c:48-warning: sigint_cb loop0xb7745440 w 0xa015c00 revents 1024

chroot root has to match workingdir, try -r /var/dionaea/ [COLOR=SeaGreen](tried following this, still get the same error message)[/COLOR]

I appreciate in advance any advice/guidance.

J3

---

