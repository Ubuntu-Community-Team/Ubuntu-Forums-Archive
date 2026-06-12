---
title: "running applications"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Souptik on 2010-08-21
I am quite new to linux. Can anyone please tell me how to run applications in linux............
for example if i want to run 7zip from the terminal???:D

---

### Post by alphacrucis2 on 2010-08-21
> **Souptik said:**
> I am quite new to linux. Can anyone please tell me how to run applications in linux............
for example if i want to run 7zip from the terminal???:D

If the 7zip executable is in the path being used by bash then just type 7zip followed by any arguments. If you just want to run a command or program that is in the current directory then precede it with ./

---

### Post by Vrroom on 2010-08-21
You will find launchers in applications menu on top left corner of the screen.
Also press alt+f2 and type 7zip to launch it.
Another way is to right click any archive and select 'open with'. Then select 7zip from the list.

---

### Post by Souptik on 2010-08-21
> **alphacrucis2 said:**
> If the 7zip executable is in the path being used by bash then just type 7zip followed by any arguments. If you just want to run a command or program that is in the current directory then precede it with ./

Thanks for responding so fast.
But I see that there are still some problems with 7zip.... lucid doesn't seem to detect it though it is installed.
Please refer to the attachments.

---

### Post by Souptik on 2010-08-21
> **Vrroom said:**
> You will find launchers in applications menu on top left corner of the screen.
Also press alt+f2 and type 7zip to launch it.
Another way is to right click any archive and select 'open with'. Then select 7zip from the list.
Actually, 7zip is not there in any launcher in applications....
Also..... after I give the command using Alt+F2 the dialog box just disappears without any result... could you help me with it?

Also I couldn't understand what you meant by 'Another way is to right click any archive and select 'open with'. Then select 7zip from the list.'   Would you please explain it?

---

### Post by dagdeniz on 2010-08-21
```
man 7z
man 7za
```

looks like: 
7z x /path/to/file.7z /path/to/whereyou'llextract
7z a /path/to/file.7z /path/to/whatyou'lladd

---

### Post by kroq-gar78 on 2010-08-21
> **Souptik said:**
> Actually, 7zip is not there in any launcher in applications....
Also..... after I give the command using Alt+F2 the dialog box just disappears without any result... could you help me with it?

Also I couldn't understand what you meant by 'Another way is to right click any archive and select 'open with'. Then select 7zip from the list.'   Would you please explain it?
i'm pretty sure that the 7zip for linux is command line only (terminal), that's why it doesn't do anything when you use alt+f2. You need to do

```
7z <arguments> <file>
```

the argument to extract Is "x" (no quotes) 

```
7z --help
```
should tell you all the other arguments

---

### Post by davdo2004 on 2010-08-22
Why are you making it so hard for yourself ?
If you have 7zip and also rar and unrar from repositorys installed, then all you have to do is right click on your rar file and select extract here and the archive manager will do the rest.

---

