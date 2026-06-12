---
title: "UnRar select files"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Matuku on 2009-08-15
Is there a way to unrar only select files? I know how to do all files in a folder fairly easily but is there a way to easily select a large number of them? In WinRAR you can go up a level in the gui to the folder the archive is located in and from there select multiple archives and just extract them all; file roller doesn't seem to have a similar functionality.

---

### Post by wojox on 2009-08-15
Don't have unrar, but you can open a terminal:

```
man unrar
```

Should give you some options.

---

### Post by howefield on 2009-08-15
> **Matuku said:**
> In WinRAR you can go up a level in the gui to the folder the archive is located in and from there select multiple archives and just extract them all; file roller doesn't seem to have a similar functionality.

Works the same way in file-roller, have you installed rar and unrar ?

---

### Post by colau on 2009-08-15
> **Matuku said:**
> Is there a way to unrar only select files? I know how to do all files in a folder fairly easily but is there a way to easily select a large number of them? In WinRAR you can go up a level in the gui to the folder the archive is located in and from there select multiple archives and just extract them all; file roller doesn't seem to have a similar functionality.
```

sudo aptitude install unrar
unrar e <filename.rar>

```

---

### Post by Matuku on 2009-08-15
> **howefield said:**
> Works the same way in file-roller, have you installed rar and unrar ?

Yep, both installed but the "Go Up a Level" button is greyed out. I thought it might be because they're on an NTFS partition but the problem persists when I copy them to the Desktop.

Another thing I've noticed is that they're all read only; perhaps because they're "parts"? Could this be affecting it?

---

### Post by colau on 2009-08-15
> **Matuku said:**
> Is there a way to unrar only select files?
```

sudo aptitude install unrar
unrar e <filename.rar>

```

---

### Post by Matuku on 2009-08-15
> **colau said:**
> ```

sudo aptitude install unrar
unrar e <filename.rar>

```

Haha, very good. But it is file***s***, plural. I'm sure you can just list the names after the unrar command if you really want to but is there no GUI way to do this so I don't have to manually enter the name of each rar file I want extracted?

---

### Post by howefield on 2009-08-16
> **Matuku said:**
> perhaps because they're "parts"? Could this be affecting it?

I am a little confused now, are you saying that you have an archive which spans several parts, and that you want to extract specific files from more than one part simultaneously ?

---

### Post by Matuku on 2009-08-16
No no, the archives contain only one file each but are split into multiple parts (part1.rar, part2.rar, etc); I have lots of different archives but only want to extract certain ones (say 10 out of 100). In WinRar you could open one of these archives then "Go up a level" in Winrar so you could see all of the archives in that folder. You could then Ctrl+Click to select the 10 you wanted and hit extract and it would extract only those. But file-roller doesn't seem to have this functionality; the "Go up a level" is greyed out.

---

### Post by Matuku on 2009-08-18
*bump bump bump*

---

### Post by Matuku on 2009-08-18
Is the "Go up a level" button not greyed out for anyone else then? I'm using Linux Mint, btw.

---

