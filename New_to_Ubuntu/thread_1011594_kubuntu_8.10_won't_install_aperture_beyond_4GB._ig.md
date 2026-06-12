---
title: "kubuntu 8.10 won't install: aperture beyond 4GB. ignoring."
date: 2008-12-14
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-12-14
The live cd stopped at this and didn't load
```
aperture beyond 4GB. ignoring.
```
I search this forum but still cannot find a solution. Can anyone tell me what to do? Or should I give up 8.10 and install 8.04 instead?
Thanks!

My system spec:
AMD Athlon x2 5000+
1G RAM
GeForce 8400GS 256MB
AMD 690G mobo

---

### Post by dwasifar on 2008-12-15
I think that message may be unrelated to your installation problem.  I did an Ubuntu installation last week on hardware that had previously had Gutsy installed.  It threw that same warning with Intrepid, but continued to install.

I'm guessing it's showing you that warning and then hanging up on something else, which makes you think the warning has something to do with the problem.

I suggest you try an alternate CD installation, or Ubuntu instead of Kubuntu, and see what happens.  If you get a successful Ubuntu install you can always *sudo apt-get install kubuntu-desktop* over it.

---

### Post by Martin Marshalek on 2009-01-11
I'm having the same message at boot in my 8.10 amd64 installation. There's nothing wrong with my computer though.

---

### Post by sadaruwan12 on 2009-01-12
> **afeasfaerw23231233 said:**
> The live cd stopped at this and didn't load
```
aperture beyond 4GB. ignoring.
```
I search this forum but still cannot find a solution. Can anyone tell me what to do? Or should I give up 8.10 and install 8.04 instead?
Thanks!

My system spec:
AMD Athlon x2 5000+
1G RAM
GeForce 8400GS 256MB
AMD 690G mobo

Hi,

Check this out and you might be able to get some idea about that massage,
[Take me there]("http://www.gossamer-threads.com/lists/linux/kernel/908549")

there must be some thing else blocking your system from booting up do you have any other  hardware part installed beside what you've mentioned here.
If you're using a 64bit Live CD then this massage is not a bug 'cos I get this frequently with my system but it works with out any problems.

---

