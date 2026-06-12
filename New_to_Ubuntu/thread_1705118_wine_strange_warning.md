---
title: "wine strange warning"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by pressko on 2011-03-11
Hi,

When i'm starting "regedit" from terminal i get : 

wine: cannot find L"C:\\windows\\system32\\plugplay.exe"

any suggestions ? 


10x in advance

---

### Post by grahammechanical on 2011-03-11
This is not a strange warning.

I have wine installed on my system and when I go to the wine menu and select Browse C: Drive I can find plugplay.exe in the system32 folder in the windows folder. I did nothing special to put it there. The wine install put it there. May be you do not have plugplay.exe in the system32 folder.

Why are you running regedit? That program allows you to edit the windows registry, does it not? You are not running Windows.

Regards.

---

### Post by pressko on 2011-03-12
I need to change some registers , cuz windows games are emulated trough wine , aren't they ? Why plugplay.axe is missing and what it does ? Can u send me the file  on email (presianbg@gmail.com)  ? 

Best Regards :)

EDIT: 

i checked it and i  plugplay.exe is in system32 folder :O ? wtf is going on :P

---

### Post by Mark Phelps on 2011-03-13
> **pressko said:**
> I need to change some registers
Regedit is NOT used to change registers; it is used to change Windows Registry entries -- which is what I think you mean.

>  cuz windows games are emulated trough wine , aren't they ? 
No, they are not.  Wine is not an emulator.  Wine is a set of Windows DLLs that make Linux system calls instead of Windows system calls.

To run a particular Windows game or app, you have to install it through Wine.  You should check the Wine App compatibility data base for app/game ratings at the WineHQ site before you attempt to install anything.

> Why plugplay.axe is missing and what it does ? Can u send me the file  on email (presianbg@gmail.com)  ? 
If you want detailed Wine support, you should be posting in the Wine subforum, not the Absolute Beginners forum.  You will get better support there.

---

