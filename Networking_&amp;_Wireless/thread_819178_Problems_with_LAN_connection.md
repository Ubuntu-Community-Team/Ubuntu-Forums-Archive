---
title: "Problems with LAN connection"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by ReeRD on 2008-06-05
I'm having problems with LAN connection. I have a small 4 PC LAN (3 Windows machines and 1 Ubuntu machine). I have an Apache server set up on one of the Windows machines. The problem is that download speed to Ubuntu machine is awful. The connection drops at different times and then resumes again. It goes like this: download starts fine and then after half a minute stops completely. After some time it resumes again and then stops again shortly. This cycle continues until the file is downloaded. The periods of idling are much longer than those of downloading.

What I find interesting is that other 2 Windows machines can download the same file absolutely fine - no problems at all. Downloading from the Ubuntu machine is also fine.

Any ideas what could be the problem?

---

### Post by ReeRD on 2008-06-06
Anyone?

---

### Post by lisati on 2008-06-06
Are you running Apache in a virtual machine? If so, this could be part of the problem, as virutal systems don't run as fast as "the real thing"

---

### Post by ReeRD on 2008-06-06
No, it's being run on the physical Windows machine. And as I said, all other Windows machines can download from it just fine, except my Ubuntu box.

---

