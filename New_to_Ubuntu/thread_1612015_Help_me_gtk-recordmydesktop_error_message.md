---
title: "Help me gtk-recordmydesktop error message"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by X-Tarzan on 2010-11-02
hi all how to fix this error message DeprecationWarning: os.popen3 is deprecated.  Use the subprocess module. cleanup=os.popen3

---

### Post by Hippytaff on 2010-11-02
Might it be a bug - [https://bugs.launchpad.net/ipython/+bug/488061](https://bugs.launchpad.net/ipython/+bug/488061)

when do you get the error?

---

### Post by X-Tarzan on 2010-11-02
got error after i upgrade Ubuntu 10.04 --> 10.10

---

### Post by Hippytaff on 2010-11-02
might be a a bug then - have you checked out the link?

---

### Post by sandyd on 2010-11-02
> **X-Tarzan said:**
> hi all how to fix this error message DeprecationWarning: os.popen3 is deprecated.  Use the subprocess module. cleanup=os.popen3

os.popen3 is a depreciated function in python 2.6
os.popen3 needs to be changed to subprocess (subprocess.Popen)

so if function is 
os.popen3(...)
it needs to be
subprocess.Popen(...)

---

