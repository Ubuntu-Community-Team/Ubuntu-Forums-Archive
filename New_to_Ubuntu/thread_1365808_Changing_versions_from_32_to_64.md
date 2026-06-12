---
title: "Changing versions from 32 to 64 ?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-12-27
I have a couple of version related questions...  

My system is AMD Athlon 64 3200+  1Meg of memory. 

Q1.  Is there an easy way to tell if I have Ubuntu 64 or 32 installed? 

When I enter **uname -a** the system returns the following:  Linux john-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Q2.  Is there an easy way to tell if my firefox is 32 or 64 version. 

Q3.  If I am running the 32 bit version, does it make sense to upgrade to the 64 bit version? 

Would appreciate some opinions and instructions...

---

### Post by sandyd on 2009-12-27
> **Desert Sailor said:**
> I have a couple of version related questions...  

My system is AMD Athlon 64 3200+  1Meg of memory. 

Q1.  Is there an easy way to tell if I have Ubuntu 64 or 32 installed? 

When I enter **uname -a** the system returns the following:  Linux john-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Q2.  Is there an easy way to tell if my firefox is 32 or 64 version. 

Q3.  If I am running the 32 bit version, does it make sense to upgrade to the 64 bit version? 

Would appreciate some opinions and instructions...

1. ```

uname -a

``````

x86_64

```means 64-bit

edit: just saw the output
yours is 32 bit.
2.  64 bit ubuntu = 64 bit firefox. 32 bit ubuntu = 32 bit firefox

that is, unless you installed firefox somewhere else other than the repos

3. Only if you do heavy multimedia number-crunching stuff and have 3.6+ Gigs of ram
edit: must be blind, just saw that you have one gig of ram. (assuming you meant GB there, not Meg, or terabyte, or petabyte, or kilobyte, or byte)

and you cant simply "upgrade" from 32 to 64 bit, you gotta start from scratch.

---

### Post by NESFreak on 2009-12-27
A1. i686 means you're running a 32bit version of ubuntu.
A2. Since you can't run 64bit programs on a 32bit linux version, your firefox is also 32bit.
A3. No, you do not need 64bit support right now. Unless you're really sure you're missing the 64 bit functionality you'll be just fine.

So you might choose to install the 64bit version of 10.4 instead (when it comes out, next april), however if your system is running fine now. Why reinstall. Be sure to download the 64bit cdrom instead of the regular one when upgrading.

---

