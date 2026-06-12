---
title: "Is Ubuntu 8.04 buggy or Just On Intel Graphic Card Machines?"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by mikodo on 2009-05-17
Following another thread in Absolute Beginners the following is stated:

Ubuntu 8.10 has become very stable and has fewer bugs than the last long term service release (8.04) I am currently using it and will recommend it over 9.04 for computers with Intel graphics cards.
__________________


I (regretfully), have one computer (HP a6245n) with Intel chip set, Graphics Media Accelerator 3100, and graphics memory that is increased through allocation in MS Vista. I no longer use MS.

Questions:

1. I chose Hardy in April 09, because it is Long Term and I thought it would less buggy versus Intrepid. It isn't?

2. Why would Intrepid be more suited for Intel cards?

3. How does one know which version suits which computers/graphic cards?

4. I am considering upgrading and will have to upgrade eventually, so to repeat question 3; Specifically, which version do you guys recommend for me? 

I was considering moving up to Jaunty, and now I am not sure what to upgrade to. Is Intel really this problematic with Ubuntu versions, and if so, why?


Thank you,

Mikodo

---

### Post by MegaJim on 2009-05-17
A bug was introduced in Jaunty which causes kernel panicks with the x3100 and related intel video chipsets.

If you need 3d acceleration use Intrepid, if you don't use Jaunty and wait for the bug to be fixed.

---

### Post by jimmy the saint on 2009-05-17
Perhaps if you detailed some of the issues you are having, the community could help you resolve them.

---

### Post by mikodo on 2009-05-17
> **jimmy the saint said:**
> Perhaps if you detailed some of the issues you are having, the community could help you resolve them.

Sorry, I did not mean to imply I had specific issues. I was just reading some threads while I was waiting for an unrelated question to be answered in another thread I had started. This particular thread that I had quoted got me musing. I was curious why the author was making the statements he did.

Thanks,

Mikodo

---

### Post by Paqman on 2009-05-17
> **mikodo said:**
> Is Intel really this problematic with Ubuntu versions, and if so, why?


Generally no. Intel graphics chipsets normally work well with Linux, and don't even need any proprietary drivers to do so. The reversion we've seen in Jaunty is a bit unusual. Hopefully they'll sort it out quickly. I have a laptop that's still stuck on Intrepid for this reason myself.

---

### Post by ugm6hr on 2009-05-17
1. Whether a version is "buggy" or not is dependent on your hardware.  I would personally recommend 8.04LTS for overall stability and duration of bug finding and resolution.

2. See details here: [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

3. Read relevant Release Notes, or ask here.  Newer hardware requires newer versions, but some older hardware may be sacrificed.

4. If you are happy with 8.04, stick with it til 10.04 (next LTS).  If you are itching to upgrade, I would recommend trying a 9.04 LiveCD.  If it doesn't behave, then wait until the Intel issues are resolved.  8.10 will lose support just as 10.04 comes out, so is not ideal unless you upgrade again before then.

Conflicts of interest:
I run 8.04 on my laptop and 9.04 on my netbook; I am leaning towards upgrading the laptop if Jaunty proves stable on my netbook.

---

### Post by gn2 on 2009-05-17
Both my desktop and laptop have Intel X3100 graphics adapters and I have had no problems whatsoever with 8.04, in fact it's running so good and stable I have decided not to switch to 8.10 or 9.04.

---

### Post by 3rdalbum on 2009-05-17
I wouldn't necessarily recommend 8.04 over 8.10. The software is newer in 8.10 and a number of important bugs were fixed. There is support for more recent hardware too.

8.04 was a good release but for new users they should be running the latest version that they can. There are problems with Intel drivers on 9.04, which may or may not affect you (for instance, video occasionally stutters on my netbook but I've never had a kernel panic). If they affect you, you should be looking at 8.10 not 8.04.

8.04 is for people who do not want their software to change for the next two years.

---

