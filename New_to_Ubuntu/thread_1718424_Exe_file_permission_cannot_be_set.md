---
title: "Exe file permission cannot be set?"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by 23494asd on 2011-03-31
Hello, i try to set a windows executable to "executable" from the permission tab. But if i check the checkbox the "checkmakr" instantly flips back ...


Any Ideas? Thanks!

---

### Post by Paqman on 2011-03-31
Where is the file located, on your hard drive, or some removable media?

---

### Post by 23494asd on 2011-03-31
On one of my internal harddrives, which is mounted.

---

### Post by Mark Phelps on 2011-03-31
Windows executables won't run -- at least, not by themselves.

You need to have Wine (or one of its extensions) installed to run those apps.

And even then, you should first go to the WineHQ site to check out their Application Compatibility database to see the performance rating for the specific app and version you want to run.

And finally, even though you didn't ask, just letting you know that you can't use Wine to install Windows drivers.

---

### Post by 23494asd on 2011-03-31
I have wine installed and could set permission 2 days ago on other executables. Just now when i try to set the executable flag from the permission tab, it flips back :/

---

### Post by coffeecat on 2011-03-31
The exe file is on an internal partition, but what filesystem? If NTFS or FAT32 you can't change permissions except through mount options.

---

### Post by ~Plue on 2011-03-31
if you right click the .exe > open with other application > use custom command '*wine*' (instead of the default 'wine application loader.....'), then it'll run even without the 'executable' permission

---

### Post by 23494asd on 2011-03-31
> **coffeecat said:**
> The exe file is on an internal partition, but what filesystem? If NTFS or FAT32 you can't change permissions except through mount options.
I think NTFS, i have Starcraft 2 there which works liek a charm. 
I try to run TERA ONLINE launcher.exe (beta)

---

### Post by 23494asd on 2011-03-31
> **~Plue said:**
> if you right click the .exe > open with other application > use custom command '*wine*' (instead of the default 'wine application loader.....'), then it'll run even without the 'executable' permission
The wine program with an icon does not work, but there are 6 wine core files and those seem to work. But the executable seems to not work :(

---

### Post by coffeecat on 2011-03-31
> **23494asd said:**
> The wine program with an icon does not work, but there are 6 wine core files and those seem to work. But the executable seems to not work :(

Try from a terminal:

```
wine /path/to/executable/launcher.exe
```

... and see if you get any error messages.

---

### Post by 23494asd on 2011-03-31
> **coffeecat said:**
> Try from a terminal:

```
wine /path/to/executable/launcher.exe
```... and see if you get any error messages.
I get this, many lines ...

```
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x131ad0)->(0x32f1cc)
```

---

