---
title: "how to do a hashcheck"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by patchido on 2009-11-13
well, i was told to do this but it aint working,

```
so type

md5sum openS{TAB}

and it will autocomplete to eg:

md5sum openSUSE-11.2-DVD-i586.iso
(or whatever you downloaded) Hit enter and wait

If it's OK. Burn it slowly. Boot the disc and do the media check from the menu to check the burn was OK. 
```


i get this


```
No command 'md5ssum' found, did you mean:
 Command 'md5sum' from package 'coreutils' (main)
md5ssum: command not found

```

---

### Post by Anarci on 2009-11-13
There is a typo in your sample code, you entered md5ssum instead of md5sum, try

```
md5sum <file>
```

---

### Post by Paqman on 2009-11-13
A good way to prevent typos on the command line is to use TAB autocompletion. Just start typing the command and hit TAB, if the system can it will complete the command for you.

---

