---
title: "problem with wifi card aftr using virtualbox"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by julio82 on 2008-05-10
Hi,

I recently installed a new packet : virtualbox-ose-module-générique (well, I think this is the cause of my problem) and since my wifi card is constantly marked as : "unsused"

So I click to fix it, and the message that appears tells that I need to reboot the system. And so do I, but after rebooting, the situation is the same (active wifi card but unused) and even worst because the keyboard disposition changed.
So I uninstalled virtualbox-ose but it won't change anything...


Any Help ? Thank you

---

### Post by froghunter on 2008-05-10
So I am in the same boat as you, strange as that is. I was messing around with virtualbox (the newest release) on my XP dual boot (run Hardy on the other side for everyday use) and when I started Hardy this morning, my wireless card is unused also with no wireless connectivity. I use network manager and am running a Dell Inspiron 6000 which has an Intel 2200 BG card. In Hardy it can 'see' it when I check my network from the terminal, but in network tools (I think) aside from eth0, all I have is some loopbackoption. I am writing from XP right now so a lot of this isn't in front of me. I am going to try uninstalling virtualbox, but the strangest part has got to be that I installed on a separate boot and this may/may not be affecting my Hardy boot. The router works fine from XP on this boot and my N800 with maemo. Sorry for the wordiness.

---

### Post by froghunter on 2008-05-10
So, writing this from Hardy... Under network tools, instead of the loopback interface and etho, i now have eth1 and my wireless came up right away. Again, not sure why uninstalling virtualbox from the XP boot would fix this issue, but it definitely did. Any thoughts on this would be great, and I guess also maybe will try to post over on the virtualbox forum somewhere. Thanks.

---

