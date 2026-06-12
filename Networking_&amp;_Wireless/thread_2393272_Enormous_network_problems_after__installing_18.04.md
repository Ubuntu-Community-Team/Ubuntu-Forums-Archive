---
title: "Enormous network problems after  installing 18.04"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by mynot on 2018-06-01
I have installed 18.04 on a single os machine. Everything (apparently)  works ok except networking. I thought I had it solved following replies to an earlier query, but I find the problem is more general than just Chromium.

Sometimes web browsers and email will be fine for a few minutes. Then email  send will timeout, the browser will timeout and I can't ping anything, even on the local network. Then things will work again, then they won't. The browser will sit for ages on a "Waiting for.." or "Resolving host" message before saying it can't contact the network, then it will continue trying and may, or may not, succeed.

I've spent 14 days on this. The problem is the same if I use the distribution disk or my installation. I've tried various commands - netstat, nmcli, ifconfig and they don't indicate any obvious errors.

I've just tried installing Mint alongside Ubuntu but it hung on a name resolution error involving NTP, which seems to be related.

I've tied several DNS addresses with no improvement.

Now I think it's time to take the lot and drop it in the sea!!

(Unless anyone can suggest what else I might do).
Thanks

[Next day]. After bombing out of the Mint install last night, rebooted to Ubuntu 18.04  - worked perfectly for the rest of the evening. Started again this morning and back to the same problems. Also ran namebench last night and found I have been using the recommended DNS all along.

---

### Post by slickymaster on 2018-06-01
*Thread moved to **Networking & Wireless**.*

---

### Post by mynot on 2018-06-02
OK, I'm closing this thread (short as it is) because I think the problem is associated with the driver for my network card. I'll follow it up on a more appropriate thread.

---

