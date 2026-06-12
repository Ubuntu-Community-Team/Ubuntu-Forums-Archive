---
title: "Networking issue on Dell T430"
date: 2021-05-10
forum: Networking &amp; Wireless
---

### Post by mjparry on 2021-05-10
Good evening all,

Let me first begin by saying this is my first time using Ubuntu so please forgive me lack of knowledge in this arena.

I have just installed Ubuntu 20.04.2.0 LTS on a Dell T430. The Dell server is connected via ethernet cable directly to my router (Asus RT-AC86U). Ubuntu is not recognising any network cable being plugged in (Dell server has a connection). I haven't adjusted or changed any settings for the router, server and Ubuntu, it is all in default settings. 

Are there any logs or settings that I can post up to assist you with troubleshooting this issue? I have spent the last couple of hours trawling through the internet trying to find how to solve this but I haven't been successful, most likely due to my lack of knowledge.

Thank you in advance for your help.

---

### Post by mjparry on 2021-05-10
Sorry, I should also mention under network settings it shows as "Cable unplugged"

---

### Post by praseodym on 2021-05-10
Hardware?!

Please show
```

lspci -nnk
```

Does WLAN work?

---

### Post by mjparry on 2021-05-11
Hi praseodym,

Thank you for your prompt response!

Don't I feel like an absolute muppet. The ethernet port that I had connected to my router was solely for the purpose of accessing Dells Integrated Remote Access controller even though this provides an internet connection it doesn't pass through to an installed operating systems. You have to run another cable into another ethernet port for that.

Thank you for your reply, hopefully this helps another newbie like me!

---

