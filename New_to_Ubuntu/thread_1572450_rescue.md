---
title: "rescue"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Begin_learn on 2010-09-11
i installed ubuntu under windows using wubi....somehow my system crashed...i have rescued my system in rhel5.0 using rescue mode but when i insert my ubuntu cd it shows that no rescue mode is available..help me to recover my system.........

---

### Post by mikewhatever on 2010-09-11
Does RHEL5 has a wubi like installation mode?

---

### Post by Begin_learn on 2010-09-11
no but thats not what i intend to ask.....help me rescuing my system

---

### Post by mikewhatever on 2010-09-11
Well, the problem with 'rescuing' a wubi installation is that you get a virtual file system within another, usually ntfs, file system. Obviously, it's a little tricky to access it, but not impossible.
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

After you are done repairing, I think it would be wise to migrate to the proper installation, as wubi installations are not intended for day to day usage.

---

