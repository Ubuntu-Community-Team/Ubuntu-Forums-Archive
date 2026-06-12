---
title: "where is newly installed software?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by coresubsystems on 2010-01-22
I have just installed pspp using the synaptic package manager. It says it is installed but it hasn't shown up in my applications. does anyone know where it is? Cheers.

---

### Post by ubudog on 2010-01-22
It might be in System or Administration.  If not, hit ALT F2 and type pspp. Hope that helps!

---

### Post by sisco311 on 2010-01-22
Applications -> Science -> GNU PSPP

EDIT:
> **ubudog said:**
> It might be in System or Administration.  If not, hit ALT F2 and type pspp. Hope that helps!

pspp is the cli interface, psppire is the graphical interface for pspp.

---

### Post by coresubsystems on 2010-01-22
hi. there is no science section in the applications menu. The alt F2 thing didn't work either. I know its installed because in the synaptic package manager the box next to it shows that it is.

---

### Post by coresubsystems on 2010-01-22
do i need to install psppire?

---

### Post by MelDJ on 2010-01-22
> **coresubsystems said:**
> do i need to install psppire?

if you want a graphical user interface of pspp, yes

---

### Post by 1991sudarshan on 2010-01-22
just logout and login again i might work

---

### Post by coresubsystems on 2010-01-22
I have done a search for psppire in the package manager and nothing has come up. how do i get it?

---

### Post by sisco311 on 2010-01-22
> **coresubsystems said:**
> do i need to install psppire?

It's installed by the pspp package. Press Alt+F2 and run psppire.

---

### Post by coresubsystems on 2010-01-22
When i do that it says the location or file could not be found. logging out didn't work either

---

### Post by 1991sudarshan on 2010-01-22
otherwise use the terminal to open!!!!!!!!!!!

---

### Post by 1991sudarshan on 2010-01-22
otherwise use the terminal to run psppire!!!!!!!!!!!

---

### Post by 3rdalbum on 2010-01-22
Look at the screencast in my signature. The program is probably in /usr/bin, just use Synaptic to find out the name of the program, and then you can create a launcher for it.

Usually if you don't get a launcher in your Applications menu, it means that it's just a command-line program; but the package depends on GTK so it probably does contain a GUI.

Maybe file a bug report against that package if it doesn't give you an Applications menu launcher?

---

### Post by sisco311 on 2010-01-22
Are you using Hardy? The pspp package in Hardy is outdated and it doesn't contain the GUI. Use the ppa repo to install version 0.6:

[https://launchpad.net/~bojo42/+archive/ppa](https://launchpad.net/~bojo42/+archive/ppa)

---

