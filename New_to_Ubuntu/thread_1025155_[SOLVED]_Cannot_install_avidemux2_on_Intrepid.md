---
title: "[SOLVED] Cannot install avidemux2 on Intrepid"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by sarc on 2008-12-29
I cannot find avidemux2 in any repo, I downloaded avidemux_2.4.3-1~getdeb1_i386.deb and avidemux-common_2.4.3-1~getdeb1_all.deb from getdeb, and I used package installer to install Common first, then avidemux 2, but I get an Error: Dependency is not satisfiable: liblame0 (which I cannot find in any repo either).  
Can anyone help?  Or should I just stick to the avidemux (sans-2) in the repos?

---

### Post by JohnLM_the_Ghost on 2008-12-29
I don't think there is a different **avidemux2** package. I should be in the same **avidemux** package
Make sure you have enabled universe-backports repository. I think it was there.
I'm not currently at Ubuntu box, but I will take a look later.

---

### Post by mikewhatever on 2008-12-29
Avidemux in Intrepid's repositories is version 2.4.3, see package properties.

---

### Post by sarc on 2008-12-29
Sorry I was thrown off by the name (without the 2)... yes it is in the repos!  Thanks all good now.

---

