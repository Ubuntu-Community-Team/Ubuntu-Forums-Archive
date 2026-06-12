---
title: "ssh welcome message reverts to default"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by wd40s on 2010-12-09
So I've tried many times and many different ways to change the ssh welcome message but every time save it, it will just revert back to the default message the next time I login.

I've edited the /etc/motd and restarted the server and have tried various other ways to change the default message but nothing works.

If anyone can shed some advice or help it'd be much appreciated. I'm on Ubuntu Desktop 10.10 64bit if that makes any difference. Thank you.

---

### Post by wd40s on 2010-12-09
I've used that exact tutorial before posting here. The problem is that I'd save the modified /etc/motd file but the next time I'd login I'd get the default message and if I opened the /etc/motd file again it would have the default message.

All this despite the fact I just changed it. Any other suggestions?

---

### Post by gmargo on 2010-12-09
Read the fine man pages for **motd(5)** and **motd.tail(5)**, which explains why /etc/motd changes and how to prevent it from changing.

---

