---
title: "How to see traffic on computer?"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by ihatetryingtopickaloginna on 2008-10-05
I walk into the room with my computer and notice the dsl lights are blinking. But there are no programs running that should be accessing the internet. Is there a program that will show what is happening here? I'm still paranoid after using XP for a few months awhile back and just want to know for sure there isn't something bad going on.

Thanks

---

### Post by pytheas22 on 2008-10-05
The lights could represent legitimate traffic, like ARP conversations or something with other computers on your network, so there's not necessarily any cause for concern.

But if you want to monitor the traffic on your machine, probably the easiest program to use is Wireshark, which you can install with:
```

sudo apt-get install wireshark
```

Run it with 'sudo wireshark' and have it create a dump of all the traffic going across your interfaces.  It will show you where the traffic is going to/coming from, and what kind it is.  If you see a lot of TCP traffic going to a strange IP address when you don't have any networking applications (Firefox, Gaim, etc.) open, then you might want to look into it more.  Otherwise, you probably don't need to worry.

---

### Post by jmbargar on 2008-10-05
Iptraf is another tool that can help you. For installing it, just type in a terminal something like this:

> sudo apt-get install iptraf

---

### Post by ihatetryingtopickaloginna on 2008-10-05
Thanks, I'll try both of these.

---

