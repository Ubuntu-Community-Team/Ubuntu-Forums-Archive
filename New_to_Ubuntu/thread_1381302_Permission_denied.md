---
title: "Permission denied"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Slasher The Great! on 2010-01-14
[SIZE=3]hi guys,
i'm trying to add a font to '/usr/share/fonts/truetype' but it keeps on saying 'Error moving file: Permission denied'. 
Any solution?


THANKS GUYS
[/SIZE]

---

### Post by audiomick on 2010-01-14
Yep.
/usr belongs to root. You need root privileges to put stuff in there. One way is to start the file manager with root privileges
```
gksu nautilus
```
in a terminal, and do it in there.

---

### Post by garyed on 2010-01-14
use " sudo " in front of the command like this:
```
sudo mv /newfile /oldfile
```

---

### Post by ronniestamps on 2010-01-14
you can also add fonts to your user directory.

for example:

/home/ronnie/.fonts

the font folder has to have the dot in front of it: .fonts

---

### Post by Norm24 on 2010-01-14
Open a terminal and:

```
gksudo nautilus
```

You are now logged in as root and can move files as needed.

---

### Post by halitech on 2010-01-14
> **ronniestamps said:**
> you can also add fonts to your user directory.

for example:

/home/ronnie/.fonts

the font folder has to have the dot in front of it: .fonts

+1
also works great if you have a separate /home folder during a reinstall as you don't loose all your fonts.

---

### Post by iMilkChan on 2010-01-14
i agree on what the first replier said.  are you root?

---

### Post by ajgreeny on 2010-01-14
The only problem with adding fonts to a ~/.fonts folder in home is that in a multiuser system, the fonts will not be available to all.

The best way to proceed is to follow this guide.

All the fonts you will use in Ubuntu are stored in two places.

1.  /usr/share/fonts
2.  ~/.fonts

I recommend you install them in the #1 loaction.  Reason being is that if you install them to your /home directory they will not be accessible form another account on the computer.
First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/customttf
```
Next open a terminal in the folder where you have a bunch of custom fonts and
```
sudo cp ./*.ttf /usr/share/fonts/truetype/customttf
```  This will copy the truetype fonts to that folder.
Now we need to install them in Ubuntu.  That is what the fc-cache command is for.
Open a terminal in your customttf folder and
```
sudo fc-cache -f -v
```
This will install the fonts so that all users applications like OpenOffice and others can use them.

---

### Post by Slasher The Great! on 2010-01-19
WORKED, Thanks guys

---

### Post by PenguinInside on 2010-01-20
For me, it works better to have fonts installed to my home directory because I'm the only user. And I also have various OS installations. So if I install fonts to the OS, it won't be available when I reboot to another OS.

But if fonts are in .fonts, they will be available (because I have a shared home partition).

YMMV

---

