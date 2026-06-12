---
title: "cant connect to servers"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by fire_storm on 2006-09-03
hi

i cant update nor download sofware i only can connect firefoc to the internet

i use d-link router dsl-524T

thank you

---

### Post by mssever on 2006-09-03
What errors do you get? You'll get the most helpful errors if you open up a terminal (Applications > Accessories > Terminal) and type the following:
```
sudo apt-get update && sudo apt-get upgrade
```
Paste the result of that command here, then we'll know ow to help you.

---

### Post by fire_storm on 2006-09-03
well here is some of what i got

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) dapper Release.gpg
  Could not connect to ae.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release

Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to ae.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources

---

### Post by claydoh on 2006-09-03
There may be some updates or server problems on the repos, as I am getting similar , security.ubuntu.com and Kubuntu.org, and even us.archive.ubuntu.com, but they seem to be coming back up for me

---

### Post by fire_storm on 2006-09-03
i am not sure about that because it worked once and never again well if u get it 2 that means that my router isnt the problem

---

### Post by Iowan on 2006-09-03
I recently installed Dapper, then got the updates...
On my dialup, it took 3 days.  Along the way, I had several "failed" messages.  The next update session sometimes succeeded on updates that failed the previous attempt.  Yes, it seems like some of the servers were either busy or having problems.

---

