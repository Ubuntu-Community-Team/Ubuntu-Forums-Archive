---
title: "Terminal message &quot;could not open lock file&quot;"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by tmos22 on 2009-05-05
I was just trying to install Beagle for ubuntu, i went to terminal and typed 

apt-get install beagle

and got this message 

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Malalo on 2009-05-05
Try this :

```
sudo apt-get install beagle
```

then type your password when requested.

---

### Post by michy99 on 2009-05-05
Use sudo
```
sudo apt-get install beagle
```

You need root privileges to install.

Well, what he said.

---

### Post by tmos22 on 2009-05-05
Thanks, i did that but got this message

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by michy99 on 2009-05-05
If you have Synaptic package manager or Add/Remove open, you have to close it.

---

### Post by Malalo on 2009-05-05
> **michy99 said:**
> If you have Synaptic package manager or Add/Remove open, you have to close it.

I let you answer first this time :P

---

### Post by michy99 on 2009-05-05
> **Malalo said:**
> I let you answer first this time :P

I guess I owe you one.:P

---

### Post by tmos22 on 2009-05-05
Thanks guys , got it working

---

