---
title: "How to configure your DNS nameserver to work locally"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by this.ronny on 2013-11-26
I was having a lot of trouble configuring my DNS to work with 127.0.0.1, since I'm not a hard core tech, I couldn't make sense of most of the instructions.  Fortunately the solution is very simple.  However, I noticed that every search I did avoided this simple solution.  Probably because most of the people asking the question were thinking on a more technical level.  Therefore, even though I've seen this answer posted elsewhere, and it might seem too obvious for most people, I'm putting it here again for the average user to find.

So here is the super simple solution.

(based on an answer I found in [http://askubuntu.com/questions/143819/how-do-i-configure-my-static-dns-in-interfaces](http://askubuntu.com/questions/143819/how-do-i-configure-my-static-dns-in-interfaces) )

Step 1 - select Network Connections app
[ATTACH=CONFIG]248106[/ATTACH]


Step 2 - select your connection and hit "Edit"
[ATTACH=CONFIG]248107[/ATTACH]

Step 3 - under the IpV4 tab, go to the "Additional DNS Servers line", and add your localhost (127.0.0.1)

[ATTACH=CONFIG]248108[/ATTACH]


[ATTACH=CONFIG]248109[/ATTACH]


Viola!

---

