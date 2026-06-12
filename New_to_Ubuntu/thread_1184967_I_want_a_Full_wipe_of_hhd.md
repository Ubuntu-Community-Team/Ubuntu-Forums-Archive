---
title: "I want a Full wipe of hhd"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ChemShock on 2009-06-11
My friend sold his Apple laptop on ebay, but I made the suggestion that he needs to wipe his data before he sends it. I thought I'd see slick and use a LiveCd because he's interested in Ubuntu.

Any suggestions to keep his data safe?

---

### Post by John.Michael.Kane on 2009-06-11
> **ChemShock said:**
> My friend sold his Apple laptop on ebay, but I made the suggestion that he needs to wipe his data before he sends it. I thought I'd see slick and use a LiveCd because he's interested in Ubuntu.

Any suggestions to keep his data safe?

[HDDerase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml")
[dban]("http://www.dban.org/")

The shred command from a live cd may work.
```
shred -vfz -n 100 /dev/hda
```

100 times may be a bit excessive, but you can adjust the number for your needs.

or

```
dd if=/dev/urandom of=/dev/hda
```

---

### Post by jmszr on 2009-06-11
ChemShock,

Just came across this today: [http://www.pcworld.com/article/165771/remove_sensitive_data_before_you_sell_an_old_pc.html](http://www.pcworld.com/article/165771/remove_sensitive_data_before_you_sell_an_old_pc.html). 
Looks like it pretty much covers it.

---

### Post by synapsys on 2009-06-11
Darik's boot and nuke works great, but like the article says.... Once you wipe a hard drive, there is absolutely nothing on it. No big deal if your friend has the Mac OSX install disc, or sold it on ebay specifying that it has no OS.

---

### Post by bodhi.zazen on 2009-06-11
One write with zeros is sufficient.

The "theory" that one needed to do more is now defunct.

[16 Systems The Great Zero Challenge]("http://16systems.com/zero.php") 

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/")

Edit: The "16 systems" challenge has ended. It was a challenge to recover data, not sure how it ended.

---

