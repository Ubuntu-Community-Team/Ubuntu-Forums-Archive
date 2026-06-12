---
title: "Have I been hacked?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by NagWolf on 2009-08-06
Hello,
I'm running Ubuntu Server as my Squid/Squidguard solution. I only have an Internal IP on it, no Public IPs, so the Cache Request comes from a Mikrotik Firewall/LineBonder and is directly sent back to the Mikrotik to go Fetch or otherwise send the Cached Items to the Clients.

Problem is I see a lot of Traffic going through the Access.log, even when the Clients are completelly plugged out. In other words, no Requests are being made, but a Bunch of Chinese websites are processed through the Proxy.

Is there a way to check if I might have been hacked on the Ubuntu Server?
If I'm only running Apache (for the Error redirects) and Squid/SquidGuard on it, can I see if there's other processes running that's making use of the Internet?

Hope there's a Guru in the house... :confused:

Thanx so long

Edit: Will repost in Security Section

---

### Post by harry2006 on 2009-08-06
not a solution, but you can make use of netstat to see what are the processes connected to which ip

---

### Post by NagWolf on 2009-08-06
Thanx so long for the reply... as you said, it wont just yet solve it for me, I can see WWW traffic going through and HTTPS etc, but all Local Addresses referenced, are my Proxy's Lan IP... and then a bunch of Ports I wish I could all block without leaving my network crippled

Hope someone else has another suggestion

---

### Post by bodyharvester on 2009-08-06
i dont know much about servers other than linux runs on 80% of servers, arent there passwords you can assign, a public key or something?

edit: linux is pretty secure, i dont think someone is inside your system messing around, otherwise it wouldnt5 be on 80% of servers

---

### Post by Sidewinder1 on 2009-08-06
Hi Nag, you might get more informative responses (not that the above are not) :-) posting your question in either the Security Discussions or Networking & Wireless sub-forums rather than Absolute beginner; your question was/is *way* over my head, let alone an intelligent answer. Good luck, I'm sure there you'll get it sorted out.
Side

---

