---
title: "Google earth"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by johntrublu on 2009-09-14
I have downloaded google earth for Linux.  It has downloaded onto my desktop as a BIN file.  i have no idea how to instal a bin file and would appreciate some guidance.

---

### Post by Cresho on 2009-09-14
very easy!

open terminal up and cd /home/yourusernamehere/Desktop

then ls "its a small L" and make sure you can see googleearth file.

then you

sh GoogleEarthLinux.bin


and follow the installer

---

### Post by k33bz on 2009-09-14
I thought googleearth was in the synaptic manager, or was it take out after hardy?

---

### Post by oldos2er on 2009-09-14
> **johntrublu said:**
> I have downloaded google earth for Linux.  It has downloaded onto my desktop as a BIN file.  i have no idea how to instal a bin file and would appreciate some guidance.

 Open a terminal, and run these commands one at a time:

```
cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin
```

---

### Post by philinux on 2009-09-14
Why this nonsense advice.

Click the medibuntu link below, follow the instructions and then you can install from add/remove or System>admin>synaptic and install the ubuntu way.

---

### Post by barnaclebill18 on 2009-09-14
> **philinux said:**
> Why this nonsense advice.

Click the medibuntu link below, follow the instructions and then you can install from add/remove or System>admin>synaptic and install the ubuntu way.

What great advice, especially for us absolute beginners.

What Cresho wrote was completely not understandable to this newbie.

---

### Post by Cresho on 2009-09-14
:lolflag:  Well, I tried to be gentle on you but this is how I do it on my pc!

```
cd ~
ls
sh GoogleEarthLinux.bin
```
This is because my bin file has user permission and I install the stuff into an "installed_programs" folder in my username directory.  I think I had a brainfart when I typed that info above.  the guy who used this code is better suited for newcommers.

```
cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin
```

and your question reffers to the bin file and not synaptic.  I think both of us were a bit confused....... 8)

---

