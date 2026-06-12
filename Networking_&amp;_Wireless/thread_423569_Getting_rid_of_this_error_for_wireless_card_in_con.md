---
title: "Getting rid of this error for wireless card in console screens?"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by jw29 on 2007-04-26
Hello,

When I do alot of my programming, I prefer to just use a console screen rather than X.

However, this error for my wireless card keeps constantly popping up now in feisty, which is terribly annoyoing because it breaks emacs and my programs that I am testing when it does come up (with the time varying, of course, the rate seems to vary as to how often it occurs, seems to be every 30-45 seconds)...
[   22.112000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

Now, I don't even need my wireless card...I've never used it on Ubuntu, I'm always wired to the network...the wireless card has never been used in the 2 years I've had this laptop.  So I'd prefer to just completely disable the network card, or another solution would be to even install whatever is necessary to keep it from loading that.  I did a updatedb/locate and that file could not be found.

If you could help me, I'd really appreciate it.  This is the 4th version of Ubuntu I've used and I've never had this problem before.

Thank you for any help you could provide.

---

### Post by chili555 on 2007-04-26
I think the error comes about when bcm43xx looks for the needed firmware and can't find it. It's not installed by default since it's proprietary. I would suggest two things: first add bcm43xx to */etc/modprobe.d/blacklist* to keep the process from ever starting.

Second, I'd have a look at */etc/syslog.conf*. This part looks promising for a little uncommenting:```
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8
```Of course, you could even install the firmware. Search the forum for fwcutter.

---

