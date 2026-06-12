---
title: "Cannot view shared folder of Windows Vista"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by fyz on 2008-11-19
In Vista, I can view (access) shared folder in Ubuntu 8.04.

In Ubuntu 8.04, I **can** see the "Vista computer", **but can not see any shared (public) folders in Vista**. What can be the problem? Anybody help me?:(

---

### Post by lukjad on 2008-11-19
Do you have Samba installed?

```
sudo apt-get install samba
```

---

### Post by fyz on 2008-11-20
> **lukjad007 said:**
> Do you have Samba installed?

```
sudo apt-get install samba
```

Yes. I think I have installed samba, and this is why vista and ubuntu can see each other, but only the "computer". I guess maybe some settings in Vista may prevent those shared folders to be viewed from Ubuntu.

---

### Post by TutonicMonkey on 2008-11-20
I am have the same issue on several computers using 8.10 and I do have samba installed.  

Here is my post on the topic: 

[http://ubuntuforums.org/showthread.php?t=986574&highlight=ubunta+8.10+cannot+see+vista+shares](http://ubuntuforums.org/showthread.php?t=986574&highlight=ubunta+8.10+cannot+see+vista+shares)

I have yet to find an answer.

---

### Post by HermanAB on 2008-11-20
Use smbclient from the command line to debug these issues.  That is the only way to see the error messages.

---

