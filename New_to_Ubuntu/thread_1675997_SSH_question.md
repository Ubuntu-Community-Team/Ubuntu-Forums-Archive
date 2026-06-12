---
title: "SSH question"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Vistz on 2011-01-26
I have a question about encrypting your data while you're browsing using SSH. I know that one of the uses of a VPS is to use it to encrypt your data via ssh socks proxy. You would do:

```
ssh -D 22 user@something.com
```

However, let's say you're on an unprotected wireless network(like at an airport or something) and you type in the command shown above. After you type it in, you are prompted for a password. Won't someone be able to find out your password since you're still on the unprotected network?

---

### Post by khelben1979 on 2011-01-26
Using [sniffer software]("http://en.wikipedia.org/wiki/Packet_analyzer") I know it's possible to sniff up passwords on unprotected networks. So the answer should be yes. I'm no expert at [ssh]("http://en.wikipedia.org/wiki/Secure_Shell"), but you can check the wikipedia document if you're interested to read some.

---

