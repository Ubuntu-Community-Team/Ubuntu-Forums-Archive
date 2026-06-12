---
title: "ipw3945 packet injection"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by El Lance-O on 2007-08-23
I have looked around googling and such for a patch to allow packet injection with the ipw3945 driver, but I haven't been able to find a straight answer. So I decided to ask the Ubuntu collective.

Is there one? I'm using an Intel n chipset in my Inspiron E1505n.

Any ideas?

---

### Post by jakev383 on 2007-08-23
Not to sound obtuse, but have you tried it? I played with airosnort with my e1505 and was able to switch to promisc mode without any issues, and while I did not try it I would assume if it was able to do that then injection would work as well.  Am I wrong there?

---

### Post by wieman01 on 2007-08-23
It might as well be supported out of the box, I concur. So it was the case when I tested my IPW2200. No patches were required.

_**EDIT:**_
Check these out:

[http://forums.remote-exploit.org/archive/index.php/t-6912.html]("http://forums.remote-exploit.org/archive/index.php/t-6912.html")

[http://www.youtube.com/watch?v=voyvusZdcn8]("http://www.youtube.com/watch?v=voyvusZdcn8")

---

### Post by El Lance-O on 2007-08-24
I haven't tried it yet, didn't bother seeing as I read it needed to be patched/use of madwifi.

I guess I could just try it out, I'll report what happens.

---

### Post by jakev383 on 2007-08-26
> **El Lance-O said:**
> I haven't tried it yet, didn't bother seeing as I read it needed to be patched/use of madwifi.

I guess I could just try it out, I'll report what happens.

Please do.  I'd be interested.
It may have been patched from the repo already..... I don't know how to check patches with deb files or I'd check to see what package provided drivers for it.....

---

### Post by tturrisi on 2007-08-26
Howto packet injection using ipw3945
[http://www.aircrack-ng.org/doku.php?id=ipw3945](http://www.aircrack-ng.org/doku.php?id=ipw3945)

---

### Post by El Lance-O on 2007-09-03
I'm having trouble understanding what to do here.

I tried doing it without patching, and it collects IV's pretty slow, or at least slow considering you need several thousands of them.

I really don't want to screw up my driver and end up not being able to connect to the internet normally because I will probably end up doing that if someone doesn't hold my hand and lead me step by step. :)

---

