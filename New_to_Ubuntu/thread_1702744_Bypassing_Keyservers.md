---
title: "Bypassing Keyservers"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by devadittya on 2011-03-08
Hi,

I just installed 10.10 yesterday, and everything has been going along smooth. I was trying to install the latest wine (1.3.x) and ran into problems. As I understand, I need to add an extra repository for that. However, I am not able to do so because I cannot seem to connect to the keyserver. I have tried different keyservers (MIT) etc, and I think it has something to do with my university firewall. Is there anyway to bypass this entire process. 
I am running Arch on my other system, and have never run into Keyserver issues. I am not really concerned about breaking my system, and would be glad if I can do without this bureaucracy. 

Thanks :)

---

### Post by Ben Page on 2011-03-08
I had this issue not long ago.

You can either drop your firewall (for a brief time), I mean the hardware firewall on your router, or open port 11371 on your firewall. Opening the port is the best solution.

---

### Post by devadittya on 2011-03-08
I simply cannot get that done because my university wouldn't allow that. Can I not completely bypass the keyserver requirement?

---

### Post by Ben Page on 2011-03-08
You can force apt to get keys from port 80, then, or any other port that you know is open

```
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 <key>
```

---

### Post by devadittya on 2011-03-08
Thanks. That worked :)

A quick question: The key is a requirement by apt, or is the requirement Ubuntu specific?

---

### Post by Ben Page on 2011-03-08
> **devadittya said:**
> Thanks. That worked :)

A quick question: The key is a requirement by apt, or is the requirement Ubuntu specific?

Not sure how to answer that, Ubuntu requires aptitude and aptitude requires GPG keys for authentication, I guess...

And mark as solved, please ;)

---

### Post by mcduck on 2011-03-08
> **devadittya said:**
> Thanks. That worked :)

A quick question: The key is a requirement by apt, or is the requirement Ubuntu specific?

It's requirement of apt, used to make sure that all downloaded packages come from the real source and nobody has been able to alter their contents.

So it's not Ubuntu-specific, but an integral part of every Linux distribution that uses apt for package management.

---

