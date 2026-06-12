---
title: "[SOLVED] Intel Pro/Wireless 3945 ABG--Wicd Problem"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by mggreen14 on 2008-09-06
I have a toshiba satellite A105-S4074 with an Intel Pro/Wireless 3945 ABG wireless card. I am dual booting vista and unbuntu hardy. My wireless connects fine with windows but as soon as I switch to ubuntu Wicd finds my network and I use my WEP passphrase but Wicd gets hooked on obtaining ip address and then eventually times out. I've been reading the forums and newbie's guides but I can't seem to figure it out. Any help would be appreciated.

---

### Post by chocbar31 on 2008-09-06
I had problems with Hardy and that wifi card. Have you tried adding the backport modules? Worked for me before I switched to Ibex. That issue is solved in this version.

If you haven't tried this yet, give it a try in your terminal.


sudo apt-get install linux-backports-modules-hardy-generic

---

### Post by mggreen14 on 2008-09-06
Thanks. I'll try that out when I get to a wired connection. I'll let you know how it works.

---

### Post by chocbar31 on 2008-09-06
Sure.

Came from this thread.

[http://ubuntuforums.org/showthread.php?t=745592]("http://ubuntuforums.org/showthread.php?t=745592")

Hope it works for ya!

---

### Post by mggreen14 on 2008-09-06
I'm happy to say that it connected right up and I'm using my ubuntu partition as we speak. Thanks for all your help.

---

### Post by chocbar31 on 2008-09-17
> **mggreen14 said:**
> I'm happy to say that it connected right up and I'm using my ubuntu partition as we speak. Thanks for all your help.

YAY...happy surfing!

:guitar:

---

