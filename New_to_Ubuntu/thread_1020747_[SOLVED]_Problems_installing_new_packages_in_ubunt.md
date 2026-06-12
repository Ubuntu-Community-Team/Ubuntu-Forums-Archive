---
title: "[SOLVED] Problems installing new packages in ubuntu error"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by letters on 2008-12-24
I am trying to add more packages to Ubuntu, but I keep getting this error:
How can I fix this problem. Thank you.

[IMG]http://img19.picoodle.com/img/img19/3/12/24/f_errorwindowm_f889949.png[/IMG]

:(

---

### Post by ibizatunes on 2008-12-24
try these
```
sudo apt-get install -f 
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by kansasnoob on 2008-12-24
I would go to System > Administration > Synaptic and click on the Edit tab, then click on Fix Broken Packages and see what response you get.

---

### Post by letters on 2008-12-24
> **kansasnoob said:**
> I would go to System > Administration > Synaptic and click on the Edit tab, then click on Fix Broken Packages and see what response you get.

When I try to open Synaptic Package Manager. I get this error:

[IMG]http://img26.picoodle.com/img/img26/3/12/24/f_errorm_cb0531f.png[/IMG]

---

### Post by letters on 2008-12-24
???

---

### Post by snova on 2008-12-24
> **letters said:**
> When I try to open Synaptic Package Manager. I get this error:

Open a terminal (Applications -> Accessories -> Terminal) and type this:

```
sudo dpkg --configure -a
```

(Press Enter, obviously)

Type in your password (it won't show), and wait for the prompt to come back.

Hopefully this will fix it.

---

### Post by letters on 2008-12-24
> **snova said:**
> Open a terminal (Applications -> Accessories -> Terminal) and type this:

```
sudo dpkg --configure -a
```

(Press Enter, obviously)

Type in your password (it won't show), and wait for the prompt to come back.

Hopefully this will fix it.

I entered the code. I can now open Synaptic Package Manager, but still cant open Add/Remove Programs to install new packages.

---

### Post by letters on 2008-12-24
Im guessing to stop getting this error. I will have to fix the broken packages, but not sure which packages are broken...

[IMG]http://img34.picoodle.com/img/img34/3/12/24/f_brokenpackm_7de26b7.png[/IMG]

---

### Post by balaknair on 2008-12-24
> **letters said:**
> Im guessing to stop getting this error. I will have to fix the broken packages, but not sure which packages are broken...

[IMG]http://img34.picoodle.com/img/img34/3/12/24/f_brokenpackm_7de26b7.png[/IMG]

In Synaptic

To see the broken packages, in the left hand pane-->select Custom filters-->Broken

To fix the Broken Packages, Edit> Fix Broken packages

---

### Post by letters on 2008-12-24
> **balaknair said:**
> In Synaptic

To see the broken packages, in the left hand pane-->select Custom filters-->Broken

To fix the Broken Packages, Edit> Fix Broken packages

Thank you broken packages are fixed! I can now continue to install new packages. :guitar:

---

### Post by balaknair on 2008-12-24
Glad to help.

Could you please mark the thread as solved(from the thread tools menu on top).
It'll help others with similar issues find it.
Thanks.

---

