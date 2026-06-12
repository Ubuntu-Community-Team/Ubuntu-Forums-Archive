---
title: "in need of urgent help.. wut is this??"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by applewire on 2009-10-02
HI,
i have installed ubuntu 9.04 on my laptop,
i try to install programs like 7-ZIP, recordmydesktop and other programs... and every time i try so, on the description box it says this...
"gtk-recordMyDesktop cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
and it says that with 7-ZIP and other programs i try to get!!:(

Does any one know how to help me !??:confused::?:

---

### Post by oldos2er on 2009-10-02
How exactly are you trying to install these programs? Are you running 64-bit Ubuntu?

---

### Post by fela on 2009-10-02
You're probably trying to run 64 bit software on a 32 bit system.

Try using the 32 bit version.

We can know for sure what architecture (32 or 64 bit) you're running if you enter this command:

```
uname -m
```

EDIT: it could be the other way round. We'll know when you've run that command.

---

### Post by applewire on 2009-10-02
> **fela said:**
> You're probably trying to run 64 bit software on a 32 bit system.

Try using the 32 bit version.

We can know for sure what architecture (32 or 64 bit) you're running if you enter this command:

```
uname -m
```

EDIT: it could be the other way round. We'll know when you've run that command.
its a 32bit (idk how to get the 32bit version)

and "i686" is a 32 bit.. right?

---

### Post by applewire on 2009-10-02
> **oldos2er said:**
> How exactly are you trying to install these programs? Are you running 64-bit Ubuntu?
im using a 32bit, "i686" is 32 bit.. right?? (im sure it is) and how do i get the 32 bit versions of the programs im trying to get??

---

### Post by halitech on 2009-10-02
are you downloading the files from a website and trying to install them or are you using Synaptic to try and install things?

---

### Post by Maheriano on 2009-10-02
THIS IS NOT URGENT. Stop that.

---

### Post by fela on 2009-10-02
> **applewire said:**
> im using a 32bit, "i686" is 32 bit.. right?? (im sure it is) and how do i get the 32 bit versions of the programs im trying to get??

Yes, i686 is a variant of 32 bit.

Are you trying to install the software through synaptic? You should be. If it gives you that error through synaptic something's very wrong.

---

### Post by LewRockwell on 2009-10-02
> **Maheriano said:**
> THIS IS NOT URGENT. Stop that.

the box fell over and naked cheerios are running everywhere

.

---

### Post by applewire on 2009-10-02
yes i am trying to install it from synaptic.

---

### Post by JC Cheloven on 2009-10-02
```
sudo dpkg --configure -a
```
and then try again.

---

