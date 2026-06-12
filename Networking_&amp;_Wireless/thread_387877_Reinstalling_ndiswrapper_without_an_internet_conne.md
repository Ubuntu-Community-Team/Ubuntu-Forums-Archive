---
title: "Reinstalling ndiswrapper without an internet connection"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Eschatokyrios on 2007-03-18
I have a laptop running ubuntu 6.06 with ndiswrapper. It was working successfully, but for some reason after a while ndiswrapper stopped working, and the system no longer sees wlan0. Trying to fix that, I somehow screwed up the ndiswrapper program. Whenever I do ndiswrapper -v, it says it can't find module ndiswrapper, and the same error occurs when I do 'modprobe ndiswrapper'. 

I think the only way to fix this is by reinstalling, but how do I reinstall it without an internet connection? I can't compile from source because I don't have source headers, which I can't get without an internet connection. And I obviously can't get it from synaptic without a connection, either. So what should I do?

---

### Post by aysiu on 2007-03-18
Type these commands into the terminal--insert the Ubuntu CD when prompted: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```

---

### Post by Eschatokyrios on 2007-03-24
I did that, and it said ndiswrapper-utils was already installed. This didn't fix the problem. I think ndiswrapper-utils is fine, but the kernel module itself is screwed up.

---

