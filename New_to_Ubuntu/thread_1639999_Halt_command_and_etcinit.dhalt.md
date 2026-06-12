---
title: "Halt command and /etc/init.d/halt"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by awp2513_ on 2010-12-07
Hi,

I am using Ubuntu 10.04 Netbook Remix. I was taking a look into the differences between the shutdown command and the halt command. While I was looking, I found that the halt script in /etc/init.d actually calls the halt command. This got me to wondering what actually happens when I just type "halt" (with a -d parameter that isn't specified in the man page, maybe this is another post...)

I wanted to convince myself that the halt script was actually being run. I've added echoes and file touches but they were never hit. I even added scripts both before and after it in priority (priority 89 and priority 91) just to see, but those never appeared to run either (not that I really expected the one after to run).

Does somebody out there know and could describe the series of events that happens after using the halt command? I might be making it more complicated than it is (halt just switches the runlevel to 0, the rc0.d scripts get run, the end), but again, I haven't been able to prove it to myself.

Thanks in advance!

---

### Post by cariboo on 2010-12-07
If you look at the halt script, it references /etc/default/halt, where the script says halt=poweroff.

---

