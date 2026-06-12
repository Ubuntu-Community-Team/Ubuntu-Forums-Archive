---
title: "Sony VAIO Ubuntu 14.04 No wireless or wired internet connection"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by gina3 on 2015-02-02
Hi,

I have a Sony VAIO (quite old) on which I recently installed Ubuntu 14.04.

Everything was working fine, but sometimes, my wireless connection fails (this has happened at work and at home). I tried the general troubleshooting techniques (restarting modem/router, rebooting computer, etc.) but nothing seemed to work.

I also tried this method ([http://ubuntuforums.org/showthread.php?t=1985079](http://ubuntuforums.org/showthread.php?t=1985079)) but all that seems to have done is that now, both my wireless connection **and **ethernet connection do not seem to work. The system says that there's a connection, but every time I ping google, it times out.

I'm not really sure where to even start with network diagnostics, so any help would be much appreciated.

Thanks!
Gina

---

### Post by gordintoronto on 2015-02-03
Can you ping 8.8.8.8

If so, you are not getting a DNS server set up.

I think you followed a suggestion which was for a very different problem than what you experienced.

Perhaps you could run this command: ifconfig -a

Then post the output between Code tags.

---

