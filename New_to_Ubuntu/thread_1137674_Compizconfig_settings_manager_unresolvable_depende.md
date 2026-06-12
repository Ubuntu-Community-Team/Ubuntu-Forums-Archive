---
title: "Compizconfig settings manager unresolvable dependencies"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by laffinet on 2009-04-25
Hi !

I recently did a clean install of 9.04. Tried to install compizconfig settings manager and get the following error message:

The following packages have unresolvable dependencies...

"compizconfig-settings-manager:
 Depends: python-compizconfig but it is not going to be installed"

If I try to install python-compizconfig I get another dependency error:

"python-compizconfig:
  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed"

If I check for python I actually have 2.5, 2.6 & 3.0 installed (according to synaptic)

---

### Post by steve101101 on 2009-04-25
that is weird. have you tried to install python?/ not sure if its going to help.

---

### Post by laffinet on 2009-04-25
See edit above.

---

### Post by ibetimpostingforhelp on 2009-09-10
I have the same problem using 8.10.  Currently have Python 2.5 installed.

---

### Post by powel212 on 2009-09-10
Hey Guys

I have experienced this before too and I found that it was caused because the mirror I was using was out of date. Thus causing incompatibility issues with some packages. Please change your Mirror to the Main US mirror then run updates. Then install compiz again. If it comes back with errors please open synaptic and under the edit menu select "fix broken Packages" then hit apply then run updates again and then install compiz again.

Changing to The main US mirror may be slower if you are outside the US but it will be less problematic.

I hope that helps.

Powel

---

