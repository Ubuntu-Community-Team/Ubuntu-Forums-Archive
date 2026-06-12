---
title: "Mac id"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by aas452 on 2009-02-21
Is there a way to find out what my MAC ID is on my computer???

---

### Post by taurus on 2009-02-21
Applications -> Accessories -> Terminal
```
ifconfig
```
or
```
/sbin/ifconfig
```
if /sbin is not in your path.

---

### Post by HermanAB on 2009-02-21
You can also use ifconfig to change the MAC address.  That is sometimes very useful when replacing a machine that is hooked to a DSL modem.

Cheers,

H.

---

### Post by aas452 on 2009-02-21
Found it:

As Root

```

ifconfig -a

```

Its under **eth0**

Look for **HWaddr **

---

