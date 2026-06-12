---
title: "Telnet problems"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Tanjer1588 on 2008-01-27
So i have been learning how to use telnet lately and i think its a great tool. But i am haveing problems with it. When ever i try to connect to a SMTP server it dosent do any thing all i get is this

```
<name>@<name>-desktop:~$ telnet mail2.atgames.jp 25
Trying 221.253.202.163...

```

and it just stays stuck at tryings. i nmap'ed myself and noticed that my port 25 was not there, so i went into my router to turn it on. after i turned it on its still not workings. so im thinking im doin something wrong. any advice would be wonderful

thank you

---

### Post by amo-ej1 on 2008-01-27
first, not all smtp server will allow access to anyone.

when you portscan yourself and see a port is not open, it most often simply mean that no software is installed/running which uses that port. 

And you shouldn't nmap yourself, use the right tool for the right job, man netstat will get you started.

---

