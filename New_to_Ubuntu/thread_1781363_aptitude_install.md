---
title: "aptitude install"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by izacboy_123 on 2011-06-13
Hello,

I recently purchased a VPS, as I want to have a go at running some applications I wrote in Python. 

I have logged into my VPS using PuTTy as root, and I wanted to get stuck in, so I tried to use wget to download Python 2.7 Tar, but I got this error:

> -bash: wget: command not found

So I figured it isn't installed, and isn't too much of a problem, so I tried: aptitude install wget - and it seems as if it is working, but it returns these errors:

> Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main wget 1.11.4-2ubuntu1.1
  404 Not Found [IP: 91.189.92.166 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.11.4-2ubuntu1.1_amd64.deb:](http://security.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.11.4-2ubuntu1.1_amd64.deb:) 404 Not Found [IP: 91.189.92.166 80]
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done


I've also tried: aptitude uptade - but that also gives some 404 errors and such.

Any help is much appreciate guys, thanks!

---

### Post by sanderd17 on 2011-06-13
That's a simple problem. You're on Jaunty, and Jaunty has reached the end of life. You should upgrade (preferably to 10.04).

See this documentation: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by izacboy_123 on 2011-06-13
> **sanderd17 said:**
> That's a simple problem. You're on Jaunty, and Jaunty has reached the end of life. You should upgrade (preferably to 10.04).

See this documentation: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[s]Ah, okay! Thanks!

Just out of interest, my VPS provider won't mind me updating the OS installed will they? :S

-

Sorry, I'm a bit of a newbie, I want to make sure that I get this right; What commands should I be running? The documentation seems very confusing.[/s]

-

I went to my VPS Control Panel, and it has the option of rebuilding my VPS tp version 10.10, so I decided to do that as it will completely wipe my VPS and rebuild it, which seems the best option! It is currently being rebuilt, will edit in my result!

Thanks!

-

WOOT!

It rebuilt, I reconnected and did lsb_release -a and it now says 10.10 Maverick!

Thanks for your help sanderd17, even though updating was a little difficult, I learnt a lot of stuff about Ubuntu on the way! Thanks! :-)

---

### Post by sanderd17 on 2011-06-13
No problem, I'm glad I could help.

---

