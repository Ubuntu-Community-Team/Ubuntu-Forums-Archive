---
title: "Running a .exe file to setup an app"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by SysEnvir on 2010-01-26
Hi!
I'm from the Windows environment and would like to know how one executes a .exe setup file from within Ubuntu, please. Just clicking on the .exe file doesn't do it.:p

---

### Post by lotharmat on 2010-01-26
If you want to use windows programs in Ubuntu; you need to install WINE

```
sudo apt-get install wine
```

---

### Post by feelshift on 2010-01-26
Ubuntu (Linux) can't run Windows apps (.exe)
What application do you want to install?
You can search for an equivalent app that will work in ubuntu or install Wine (I think it's in the repositories) and run it in Wine.
Wine is an emulator that will let you install Windows apps in Linux. :P

---

### Post by Paqman on 2010-01-26
What app are you trying to install? There might be a good Linux alternative that you can just get through Ubuntu Software Centre.

---

### Post by SysEnvir on 2010-01-26
Hi I've downloaded Strawberry Prolog Linux Version, and want to download and install Gambas.

---

### Post by 3rdalbum on 2010-01-26
The Ubuntu repositories already contain "gprolog" and "gambas".

Get your software from the repositories (Ubuntu Software Centre/Synaptic Package Manager) rather than trawling the web for programs. The repositories make it safer and easier to install, and easier to keep up-to-date.

The free version of that Strawberry Prolog seems awfully limited; you'd probably be happier with gprolog.

gprolog is run in the terminal, I believe.

---

### Post by SysEnvir on 2010-01-26
> **3rdalbum said:**
> The Ubuntu repositories already contain "gprolog" and "gambas".

Get your software from the repositories (Ubuntu Software Centre/Synaptic Package Manager) rather than trawling the web for programs. The repositories make it safer and easier to install, and easier to keep up-to-date.

The free version of that Strawberry Prolog seems awfully limited; you'd probably be happier with gprolog.

gprolog is run in the terminal, I believe.


Many thanks for this and G'day!
Andy.

---

### Post by airtonix on 2010-01-26
> **feelshift said:**
> 
Wine is an emulator that will let you install Windows apps in Linux. :P

Wine is not an emulator because it does not : 

emulate a  : 

+ cpu.
+ motherboard.
+ kernel.
+ system calls.

The correct definition of WINE is that it is a Translation Layer.

Indeed all wine does is intercept system calls made by a piece of win32 software and redirect them to relevant native Linux function calls.

Wine would be horribly slow if it were an emulator.

---

### Post by J V on 2010-01-26
> **airtonix said:**
> Wine is not an emulator because it does not : 

emulate a  : 

+ cpu.
+ motherboard.
+ kernel.
+ system calls.

The correct definition of WINE is that it is a Translation Layer.

Indeed all wine does is intercept system calls made by a piece of win32 software and redirect them to relevant native Linux function calls.

Wine would be horribly slow if it were an emulator.Shortly:

**W**ine
**I**s
**N**ot an
**E**mulator

---

### Post by feelshift on 2010-01-26
> **airtonix said:**
> Wine is not an emulator because it does not : 

emulate a  : 

+ cpu.
+ motherboard.
+ kernel.
+ system calls.

The correct definition of WINE is that it is a Translation Layer.

Indeed all wine does is intercept system calls made by a piece of win32 software and redirect them to relevant native Linux function calls.

Wine would be horribly slow if it were an emulator.
Sorry for the confusion. ;)

---

