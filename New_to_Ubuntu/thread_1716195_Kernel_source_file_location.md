---
title: "Kernel source file location"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by vmsda on 2011-03-28
Where is the kernel source located in Ubuntu, ie. if I want to view/modify/compile the active kernel, where do I look for its source?

Thank you in advance for info.

---

### Post by An Sanct on 2011-03-28
look into
```
/usr/src
```

---

### Post by Ryan20 on 2011-03-28
Do you mean typing that into the terminal?  I tried that and I get:

```
bash: /usr/src: is a directory
acer@acer-AO532h:~$ ^C
acer@acer-AO532h:~$ 

```

---

### Post by vmsda on 2011-03-28
... and is there a script/command listing the kernel parameters chosen/defaulted to?

Thank you again.

---

### Post by vmsda on 2011-03-28
> **Ryan20 said:**
> Do you mean typing that into the terminal?  I tried that and I get:

```
bash: /usr/src: is a directory
acer@acer-AO532h:~$ ^C
acer@acer-AO532h:~$ 

```

No, Ryan20, type:```
cd /usr/src
ls   (to see the contents)
```

---

### Post by vmsda on 2011-03-28
> **vmsda said:**
> ... and is there a script/command listing the kernel parameters chosen/defaulted to?

Thank you again.
Have found the answer to my own question. Configuration of kernel can be found in 

/usr/src/linux-headers .../.config

It is a hidden file which lists all the parameters and respective values.

---

