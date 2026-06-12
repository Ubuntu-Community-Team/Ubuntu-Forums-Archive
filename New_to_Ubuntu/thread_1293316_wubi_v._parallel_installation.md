---
title: "wubi v. parallel installation"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-16
With a netbook running on windows xp, what are the differences between and the comparative advantages of running installing Wubi vs. doing a parallel installation of Ubuntu?

---

### Post by oboedad55 on 2009-10-16
> **jmundinger said:**
> With a netbook running on windows xp, what are the differences between and the comparative advantages of running installing Wubi vs. doing a parallel installation of Ubuntu?

A couple of advantages of dual boot; speed, stability, and if windows dies ubuntu will still work. Okay, that's three.

---

### Post by garvinrick4 on 2009-10-16
If you want to do any testing or daily upgrades WUBI is nice.
Uses grubdos4  to boot. Easy to install or uninstall just like a 
folder in Windows. If testing new version and gets a mess just toss
grab live cd and clean install in 10 to 12 minutes. Stable versions just
run with know problems. I know hardware and drivers big issue but you will find out quickly if that is a problem either way. You can try WUBI and see. If you want to partition at later time you can.

---

### Post by QIII on 2009-10-16
Wubi is a test drive, and it's just fine for that.

---

### Post by Bucky Ball on 2009-10-16
Speed.

---

### Post by mapes12 on 2009-10-17
Personally, dual boot:

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by newtocade on 2009-10-17
dual boot...if ubuntu crashes then windows still works... such is my case...make sure its on seperate disks or the partioning is done before you try and install ubuntu...problems galore

---

### Post by Paqman on 2009-10-17
> **Bucky Ball said:**
> Speed.

Not really. The speed difference between a Wubi install on a healthy NTFS partition and a traditional install on ext3 is negligible.

Advantages of Wubi:

[LIST]
[*]Ridiculously easy install
[/LIST]

Disadvantages of Wubi:

[LIST]
[*]Cannot use hibernation.
[*]Vulnerable to power interruptions (although not an issue on laptops, due to their batteries).
[*]Fragmentation of the host filesystem can degrade performance (just as it would for the Windows system running on it). Defragging takes care of this.
[/LIST]

---

