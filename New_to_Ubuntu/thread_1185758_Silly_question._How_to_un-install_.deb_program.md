---
title: "Silly question. How to un-install .deb program?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by Tholley on 2009-06-12
I installed Frostwire from the Frostwire website yesterday, (did not see an apt in Add/Remove or Synaptic), it will not work, something corrupted. I downloaded it again and re-installed per the error instructions. Still showing something corrupt, so I just want it to be gone and I'll stick to Limewire which downloaded and installed perfectly.
 
So how to I un-install it? There is nothing showing in the repo to de-select.
 
And I thought I was getting the hang of this.:eek:

---

### Post by gradinaruvasile on 2009-06-12
if u have broken dependencies 
in a terminal type (it will not break anything if not needed):
sudo apt-get install -f
If u had installed frostwire, this would uninstall it(terminal again):
sudo apt-get remove --purge frostwire

---

### Post by mharrison on 2009-06-12
You should be able to search for it in Synaptic as well and remove it from there.  I have done that with Frostwire in the past.

---

### Post by Tholley on 2009-06-12
> **mharrison said:**
> You should be able to search for it in Synaptic as well and remove it from there. I have done that with Frostwire in the past.
 
That was what I was thinking I could do, but it is not listed in Synaptic. :confused:
 
I guess I'll try using sudo like gradinaruvasile suggested.

---

### Post by zika on 2009-06-12
Did You look in Status->Installed(local or obsolete) ... ?
Did You look by Origin?
(I mean in Synaptic)

---

### Post by Tholley on 2009-06-12
> **zika said:**
> Did You look in Status->Installed(local or obsolete) ... ?
Did You look by Origin?
(I mean in Synaptic)
 
Status >Installed I do not remember seeing that options anywere. Is that is Admin?
 
I did search for it in Synaptic, and after typing frost it comes up blank.

---

### Post by michy99 on 2009-06-12
```
sudo dpkg --remove frostwire
```

---

### Post by markharding557 on 2009-06-12
if it was a .deb it should show up in synaptic in the local and obsolete tab

---

### Post by xavierp94 on 2009-06-12
sudo dpkg -r debpackage.deb

---

### Post by zika on 2009-06-13
> **Tholley said:**
> Status >Installed I do not remember seeing that options anywere. Is that is Admin?
 
I did search for it in Synaptic, and after typing frost it comes up blank.
"Status->Installed(local or obsolete)" is in Synaptic.

---

### Post by Tholley on 2009-06-13
> **zika said:**
> "Status->Installed(local or obsolete)" is in Synaptic.

Found it, removed it completely.

Thanks!

---

