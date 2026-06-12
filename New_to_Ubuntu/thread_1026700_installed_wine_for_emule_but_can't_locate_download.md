---
title: "installed wine for emule but can't locate downloads"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by shalamabobbi on 2008-12-31
I did not create a psuedo c drive but ran emule directly. Emule has been downloading material for days but I can't seem to locate the location of the emule program or its folders with the search function under places.
This should be trivial I think.

---

### Post by mhh91 on 2008-12-31
why don't you just install aMule,i think it does the same job on ubuntu,and runs nicely as well

you'll find it in synaptic

---

### Post by davec64 on 2008-12-31
have a look at the find command:

[http://www.ss64.com/bash/find.html]("http://www.ss64.com/bash/find.html")

If you know the name of a file you've downloaded it'll be able to tell you where it is.

All the best:D

---

### Post by LowSky on 2008-12-31
wine creates its own drive and it hidden from normal view
use ctrl + H to show hidden folders

Wine folder is hidden within you /home folder

also aMule is the Linux version of eMule and it runes great

---

### Post by shalamabobbi on 2008-12-31
I found it. Wine did create a c drive..
Applications-wine-browse c drive
I didn't look since another internet article mentioned creating the c drive as the responsibility of the user when installing wine.

Thanks

---

### Post by Funnnny on 2008-12-31
~/.wine/c_drive (as I remember)
Does the same job as Browse C Drive

---

### Post by donkyhotay on 2008-12-31
The default wine C: 'drive' is located at:
```
~/.wine/drive_c/
```
You can just CD right to it or if you prefer the gui just use nautilus so long as hidden files are showing.

---

