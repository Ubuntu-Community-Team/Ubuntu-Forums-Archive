---
title: "How to open a .lnk"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by downloadfreak on 2008-12-18
Hello,

I downloaded and installed several programs with wine and some of them have the extension .lnk When I try to open it it says:
"Could not open thefile.lnk
There is no application installed for this file type."

What can I do about it?

Best regards,
Downloadfreak

---

### Post by lovelyvik293 on 2008-12-18
the .lnk files are Windows Shortcut File.So i think you can't open them in linux.

---

### Post by decoherence on 2008-12-18
I haven't tested this, but try right clicking on the .lnk file and selecting "Open with Other Application."

In the box that comes up, either find wine in the list or click the little triangle at the bottom and type 'wine' in to that (no quotes)

let us know if that works!

---

### Post by downloadfreak on 2008-12-18
I can see it in the list and after trying several times it doesn't work

---

### Post by decoherence on 2008-12-18
That's too bad... I'd think wine would be able to deal with .lnk files fine.

You'll have to find the original file it refers to. I gotta start commuting soon, but the easiest way I can think of off the top of my head is to use the strings program from the terminal
```

strings filename.lnk
```

hopefully it will show you the path of the original file. good luck

---

### Post by downloadfreak on 2008-12-18
I tried it in several ways but always it says "no such file" But it's in the c: drive in wine, is that a problem?

---

### Post by bwang on 2008-12-18
The .lnk files are just shortcuts. Go to Applications>Wine>Programs and you should be able to find the programs you installed.

---

### Post by decoherence on 2008-12-19
> **downloadfreak said:**
> I tried it in several ways but always it says "no such file" But it's in the c: drive in wine, is that a problem?

nope, that should be ok. in the terminal type "strings "

no quotes and follow it with a space. don't press enter yet.

now find this .lnk you want to open and drag it to the terminal window. It should display the path to the file... now press enter and see if it spits out another path which would be the original file.

---

### Post by mc4man on 2008-12-19
.lnk are worthless so you can safely delete them. Usually they're created when installing a program in wine and choosing to create a desktop icon.
In that case you'll get the shortcut (icon) and a .lnk, deleting the .lnk will have no effect on the shortcut.

If your curious you can open them in gvim.

---

### Post by s.fox on 2010-10-27
Necromancy - Thread Closed.

---

