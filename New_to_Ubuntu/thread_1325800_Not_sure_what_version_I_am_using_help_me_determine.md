---
title: "Not sure what version I am using? help me determine this."
date: 2009-11-13
forum: New to Ubuntu
---

### Post by flywelder on 2009-11-13
I know it says I am using Ubuntu Christian version.....maybe a 7.4 version?????
 A friend installed this a year ago and I am still learning how to use Ubuntu.
 The friend has now moved away and I am lost when some thing goes hey wire! 
 I am wondering if I should update to a newer  version, but how would I do that?
 Help please.
 Desperate D.

---

### Post by wojox on 2009-11-13
Open a terminal and type:

```
uname -r
```

Get the kernel version. Yes you should but you'll need to do a clean install I believe. You should ask over here: [Ubuntu Christian Forums]("http://ubuntuforums.org/forumdisplay.php?f=168")

---

### Post by sisco311 on 2009-11-13
Applications -> Accessories -> Terminal 
and type:
```
lsb_release -a
```

---

### Post by kansasnoob on 2009-11-13
> **flywelder said:**
> I know it says I am using Ubuntu Christian version.....maybe a 7.4 version?????
 A friend installed this a year ago and I am still learning how to use Ubuntu.
 The friend has now moved away and I am lost when some thing goes hey wire! 
 I am wondering if I should update to a newer  version, but how would I do that?
 Help please.
 Desperate D.

If you go to System > Administration > Terminal and run the following command it will tell you the "version" as far as how old it is:

```
cat /etc/issue
```

If you just go to System > About Ubuntu it might tell you more about the Christian Edition. I've never used it.

---

