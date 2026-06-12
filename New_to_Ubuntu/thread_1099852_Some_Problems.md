---
title: "Some Problems"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by Wovaki on 2009-03-18
Hello!

I am having a couple problems.

First, my Anti Virus (ClamTK?) says it has 0 signatures, I tried updating it, but it still says I have 0, and when I try to update it again it says it has already been updated. I tried Reinstalling it but it still won't work.

Is there another anti virus that is reccommended for Linux, I just downloaded and installed Avast! for now until I can get this problem fixed.

Second, FireStarter keeps popping up saying that it is blocking serious incoming attacks...is there anyway to stop these attacks?

Thanks

---

### Post by kestrel1 on 2009-03-18
There is no need to have an anti-virus prog running under Linux.

---

### Post by Wovaki on 2009-03-18
I know there is no need to have one, but I feel I must...I just came over from Windows, and I don't feel comfortable without an AV application.

---

### Post by Helios1276 on 2009-03-18
What version of Clamtk are you using ?

---

### Post by kestrel1 on 2009-03-18
I have been using Linux a fair time now, no AV & no problems. ClamAV should work just fine if you really feel the need. Are you behind a proxy server by any chance.

---

### Post by kestrel1 on 2009-03-18
Do you actually have ClamAV installed as ClamTK is only a gui front end for ClamAV

---

### Post by presence1960 on 2009-03-18
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Wovaki on 2009-03-18
Right now I have it uninstalled, but I guess what ever version is in the Add/Remove applications.

All I did was install it from the Add/Remove, it worked fine before, but after one update I guess it said I have 0 signatures, I didn't notice this till a few days after I updated it last, so I assume it was from a update.

---

### Post by kestrel1 on 2009-03-18
Read the link that Presence1960 gave. It should put your mind at rest as regards viruses.
Good link Presence1960, thanks.

---

### Post by Wovaki on 2009-03-18
I have already read that thread. I send stuff to Windows using friends as well, and if I transfer stuff to Windows I want to make sure it is clean.

---

### Post by t0p on 2009-03-18
> **Wovaki said:**
> 
Second, FireStarter keeps popping up saying that it is blocking serious incoming attacks...is there anyway to stop these attacks?


I don't know about "stopping" the attacks... maybe if you got hold of the attacker and cut off his, uh, connection?  If you tell us more about these attacks, we'll be able to tell you more about it.  But you've told us very little so far.

Anyway, if iptables (your firewall) is blocking these attacks, what's the problem?  They're being blocked.  You're safe.

**EDIT:** Look at your firewall logs to find out the ip address from which the attacks are originating.  Do a **whois** on the ip address, this'll tell you which ISP owns that particular address.  Email their abuse department (abuse@isp_address.com) and tell them about it.

---

### Post by kestrel1 on 2009-03-18
If you are sending files to Windows, you shouldn't have a problem if they are created on Linux, but if they originally came from a Windows machine & are going back to a Windows machine, then it is probably wise to scan them first.Avast is a reasonably AV prog or you could have a look at AVG free Linux edition: [http://free.avg.com/download?prd=afl](http://free.avg.com/download?prd=afl)

---

### Post by Wovaki on 2009-03-18
Its not necessarily files just created in Linux, but also downloads as well, sometimes video clips, etc.

I have Avast! right now, but I don't really like it that much, I have AVG on Windows, so I figured it would be better to have a different scanner than Windows, that way it gets scanned with two different scanners.

---

