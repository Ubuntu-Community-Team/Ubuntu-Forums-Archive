---
title: "HOw do I run this command at startup?"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by laredotornado on 2010-08-24
Hi,

How do I have a command launch when I startup my Ubuntu system?  Note that I DON'T want this command to launch when individual users login, I just want it to run once globally upon system bootup.  The command is

java -jar selenium-server-nightly.jar &

Thanks, - Dave

---

### Post by jtarin on 2010-08-24
> **laredotornado said:**
> Hi,

How do I have a command launch when I startup my Ubuntu system?  Note that I DON'T want this command to launch when individual users login, I just want it to run once globally upon system bootup.  The command is

java -jar selenium-server-nightly.jar &

Thanks, - DaveYou can place it in /etc/rc.local

---

