---
title: "streaming problem.."
date: 2009-05-11
forum: New to Ubuntu
---

### Post by n0c2urnal on 2009-05-11
aite so im just trying to watch some shows and this pops up..i recently upgraded to 9.04 and streams dont work.
can anyone help me out?

---

### Post by nhasian on 2009-05-11
make sure you've got flash 10 installed.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by n0c2urnal on 2009-05-11
my flash is updated. any other ideas? :(

---

### Post by avix on 2009-05-11
thats the exact same one I've been getting!

flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libgalago1.0-cil libchm1 python-ldb-samba4 libgalago3 python-tdb libwv-1.2-3
  libtaglib2.0-cil beagle samba-ldb-tools calendar-timezones python-samba
  libavahi1.0-cil libgsf0.0-cil mono-gmcs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by qjmoss on 2009-05-11
Here guys.



Go to synaptic and click search, not quick search, type flash.

The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal!

---

### Post by qjmoss on 2009-05-11
> **qjmoss said:**
> Here guys.



Go to synaptic and click search, not quick search, type flash.

The only packages you should see installed are ubuntu-restricted-extras and adobe-flashplugin. Any swfdec* or gnash packages should be marked for complete removal!

That is what i did to solve my flash problems.

Hope it helps

---

### Post by n0c2urnal on 2009-05-11
thank you so much qjmoss! followed your instructions and now everything is back to normal!

---

### Post by qjmoss on 2009-05-11
No problem, I'm very happy that i've helped you!



Have a nice day!:guitar:

---

