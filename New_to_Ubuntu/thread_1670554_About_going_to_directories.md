---
title: "About going to directories"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by baba88 on 2011-01-19
arda@ressam88:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
arda@ressam88:~$ cd downloads
bash: cd: downloads: No such file or directory
arda@ressam88:~$ 

I want to go to downloads. Where is my mistake?

---

### Post by Paqman on 2011-01-19
The command line is case sensitive. "Downloads" is not the same thing as "downloads".

Btw, you can use tab to help with directory names, so in your case:
```
cd Do<TAB>
```

...would get you to the right folder. That also works with a lot of commands.

---

### Post by m_duck on 2011-01-19
```
cd Dow<TAB>
```would be needed in this case due to the Documents folder. If you double-tapped <TAB> after typing **Do** it would suggest both Documents and Downloads as they are both possible matches for what has been typed so far.

---

### Post by baba88 on 2011-01-19
thx.
I can not use the tab. I double tap it and nothing happens. Could you clarify it?

---

### Post by t0p on 2011-01-19
1.  Linux is *case sensitive*.  Your Downloads directory is called "Downloads" not "downloads".  So the commandf

```

cd Downloads

```

will take you to the directory you want.

2.  The autocompletion feature works so, assuming you don't have any other directories that begin "Dow...", typing in

```

cd Dow

```

then hitting the tab button will finish the command for you, to

```

cd Downloads

```

If this isn't working there are a couple of possible reasons.  Maybe you *do* have other directories with names beginning with  "Dow...", in which case you'll need to provide more of the directory's name, for it to autocomplete for you.  Or maybe you've got autocompletion disabled - this setting is probably somewhere under Preferences, but you'll need to look through all the menus to be sure.

---

### Post by Paqman on 2011-01-19
> **m_duck said:**
> ```
cd Dow<TAB>
```would be needed in this case due to the Documents folder. If you double-tapped <TAB> after typing **Do** it would suggest both Documents and Downloads as they are both possible matches for what has been typed so far.

Lol @ the irony of a typo in a post about efficient command line typing :oops:

---

