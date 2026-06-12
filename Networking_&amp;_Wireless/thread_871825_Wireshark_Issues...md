---
title: "Wireshark Issues.."
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by dfrandin on 2008-07-27
Having recently done a clean reinstall of Ubuntu 8.04 on my laptop, and having a need to sniff some packets, I fired up Wireshark, and to my dismay, no work..  On the previous 7.10 install, Wireshark worked fine from the apt-get install.. Now what I get when I run the normal user Wireshark icon is absolutely no interfaces to select in the interfaces pulldown.. If I run it with the Wireshark (as root) icon, I see all my interfaces, but the second I click on capture or configure or anything, the Wireshark window goes grey, and I have to sudo killall wireshark... This is the Wireshark 1.0.0 apt-get package.. What the heck has changed???

Dave

---

### Post by mrstrano on 2008-09-09
Got exactly the same problem.. Does anybody have a solution?

Dan

---

### Post by newtubunix on 2008-09-11
Had the same problem, if i click Capture>Interfaces>Start,
but when i try Capture>Options and then the interface and then start, all seemed to work fine with me.

(This was as root btw)

---

### Post by war59312 on 2008-09-13
Indeed, this seems to be a bug in version 1.0.3, as version 1.0.2 does not have this problem. 

Thanks for the workaround, indeed works fine if you capture that way.

---

### Post by dfrandin on 2008-09-14
I'm seeing it in the 1.0.0 version that comes with Ubuntu 8.04...Are there .debs available for the newer versions?

Dave

---

### Post by prina on 2008-10-02
I had the exact same issue. Is there any fix available ?
Prina.

---

