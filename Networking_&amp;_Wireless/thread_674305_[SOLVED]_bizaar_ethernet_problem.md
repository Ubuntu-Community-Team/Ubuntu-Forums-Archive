---
title: "[SOLVED] bizaar ethernet problem"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by The Spy on 2008-01-21
I have a weird problem with my ethernet card. I can connect to the internet, and connect to the computer remotely, but it wont find updates, download packages, or download plug-ins for firefox. I tried connecting via static IP, and dhcp, as well as roaming mode. All did the same thing. I just installed 7.10 on it last night. I previously have xbuntu 7.10 on it, and it worked fine. The motherboard has a built in ethernet port that I was using until I found this problem. So I installed a NIC card, and the same thing. I'm kinda thinking it's a configuration problem. Any ideas on what the problem might be would be appreciated.

---

### Post by chewearn on 2008-01-22
Have you looked into your software sources, make sure all the relevant repositories are enabled?

---

### Post by kirsche on 2008-01-22
what does ```
sudo apt-get update
``` give you?
you have any other http trouble? What repository do you use?

---

### Post by The Spy on 2008-01-23
It worked! I went into the Software Sources, and saw that NOTHING was checked. So I check those that applied, and it works fine, I'm downloading updates right now.
Thanx.

No I haven't had any other http problems. And...refresh my memory on what a repository is and what it does.

---

### Post by chewearn on 2008-01-23
> **The Spy said:**
> It worked! I went into the Software Sources, and saw that NOTHING was checked. So I check those that applied, and it works fine, I'm downloading updates right now.
Thanx.

No I haven't had any other http problems. And...refresh my memory on what a repository is and what it does.


Yes I thought that might be the problem.  Ubuntu (since Gutsy) has the annoying habit of turning off repositories it can't detect during installation.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

