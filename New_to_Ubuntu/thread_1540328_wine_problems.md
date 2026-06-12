---
title: "wine problems"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by bripa on 2010-07-27
Hi,

I've installed WINE but I have bad response when I try to launch any .exe application. 

Message I get is:
"The file '/home/bripa/Downloads/<program name>/SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

In reading the "executable bit" note, it seems to me it is more linked to some Ubuntu policy than tech problem. How can be solved?

Thanks in advance
Bripa

---

### Post by DarthScape on 2010-07-27
You need to right-click the .exe, click properties, then go to permissions, then check the executable checkbox.

---

### Post by akoskm on 2010-07-27
> **bripa said:**
> Hi,

I've installed WINE but I have bad response when I try to launch any .exe application. 

Message I get is:
"The file '/home/bripa/Downloads/<program name>/SETUP.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

In reading the "executable bit" note, it seems to me it is more linked to some Ubuntu policy than tech problem. How can be solved?

Thanks in advance
Bripa

Hi!
Try to start it with:
```

wine /home/bripa/Downloads/<program name>/SETUP.EXE

``` if you get the same error message then it means that the file called SETUP.EXE is not an executable file.
It has nothing to do with permissions and policies.
I Hope thit helps.

---

### Post by themusicalduck on 2010-07-27
> **akoskm said:**
> Hi!
Try to start it with:
```

wine /home/bripa/Downloads/<program name>/SETUP.EXE

``` if you get the same error message then it means that the file called SETUP.EXE is not an executable file.
It has nothing to do with permissions and policies.
I Hope thit helps.

Actually it is to do with permissions and DarthScape is right.

---

### Post by akoskm on 2010-07-27
> **themusicalduck said:**
> Actually it is to do with permissions and DarthScape is right.

If wine executes the script (like opening a text file with text editor) why do I need to mark it as executable - it don't want to execute it with shell interpreter I just want to add it as input for wine.

Example:

[http://imagebin.org/107035](http://imagebin.org/107035)

Ventrilo.exe -x

---

### Post by Bachstelze on 2010-07-27
> **akoskm said:**
> If wine executes the script (like opening a text file with text editor) why do I need to mark it as executable - it don't want to execute it with shell interpreter I just want to add it as input for wine.

An EXE file is not a text file.

---

### Post by akoskm on 2010-07-27
> **Bachstelze said:**
> An EXE file is not a text file.

No, it isn't. xd
I just tried to give an example. :(
So, I can still start *.exe files with wine without +x.

---

### Post by Bachstelze on 2010-07-27
> **akoskm said:**
> No, it isn't. xd
I just tried to give an example. :(
So, I can still start *.exe files with wine without +x.

Yes, but it's not the same as opening a text file in a text editor. ;) If you run [font=monospace]ps[/font] while you have a program running in Wine, it will just give the name of the program, not wine.

---

