---
title: "Synaptic Error"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by b.healed on 2009-10-21
I am brand new to Linux and I am running into an issue as I bring up Synaptic package Manager.

Here are the details of the error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

Who can help me determine what is going on and how to fix this?

thank you so much!

Jason

---

### Post by howefield on 2009-10-21
Open a terminal (Applications > Accessories > Terminal) and type the following

```
sudo dpkg --configure -a
```

press the enter key, type your password when prompted and press the enter key.

---

### Post by dominiquec on 2009-10-21
Somehow you interrupted the APT process.  Just do as the error message says and type:

sudo dpkg --configure -a

on the command line.

---

### Post by b.healed on 2009-10-22
Great.  Thank you so much.  That fixed the issue.

Very quick responses, I am impressed.  haha

---

