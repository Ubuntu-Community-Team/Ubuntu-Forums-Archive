---
title: "How to do VAR=right($MYSTRING,1) with SH (not bash)?"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-16
Hello,

I am looking a way to get the last char under SH. It is possibel with bash using [] but not under sh.

What are solutions could be proposed?

---

### Post by john newbuntu on 2010-10-16
awk/bash does a cleaner job.  But if sh is what you want, one possible solution is:
echo $X | cut -c ${#X}
where X is your string. But make sure $X is not blank.  I'm sure there are cleaner solutions.

---

### Post by DaithiF on 2010-10-18
Hi, this works for me under both /bin/sh and /bin/bash:
```
x="hello"
echo ${x: -1:1}

```

---

### Post by honeybear on 2010-10-21
> **DaithiF said:**
> Hi, this works for me under both /bin/sh and /bin/bash:
```
x="hello"
echo ${x: -1:1}

```

Thanks !

---

### Post by honeybear on 2010-11-21
> **DaithiF said:**
> Hi, this works for me under both /bin/sh and /bin/bash:
```
x="hello"
echo ${x: -1:1}

```

it works too for getting the extension ... cool !
```
echo ${x: -4:4}
```

unfortunately it does [COLOR="Red"]**NOT**[/COLOR] work under SH 
(bash yes)

---

### Post by DaithiF on 2010-11-21
what do you mean by extension ... file extension ?

no guarantee that a file extension will be 3 chars, or even that there will be one.

a better way to get it would be:
$ x="somefile.doc"
$ y=${x##*.}
$ [[ $y == $x ]] && echo "No file extension" || echo "extension is $y"
extension is doc

---

### Post by honeybear on 2010-11-21
> **DaithiF said:**
> what do you mean by extension ... file extension ?

no guarantee that a file extension will be 3 chars, or even that there will be one.

a better way to get it would be:
$ x="somefile.doc"
$ y=${x##*.}
$ [[ $y == $x ]] && echo "No file extension" || echo "extension is $y"
extension is doc

filename.ext 
ext is the extension

well, sometimes, under MAC, they are 4 letters... 
The issue is to make it compatible with SH

---

### Post by DaithiF on 2010-11-21
the ${var##*.} construct will work under sh, (it means, strip from the left of the variable var every character up to and including the last '.' character ... which would leave you with the extension, however many chars it contains (or the entire filename if there is no '.' in the name.

---

### Post by honeybear on 2010-12-12
> **DaithiF said:**
> the ${var##*.} construct will work under sh, (it means, strip from the left of the variable var every character up to and including the last '.' character ... which would leave you with the extension, however many chars it contains (or the entire filename if there is no '.' in the name.

it works flawless, thanks !
```
 var="mama.wav" ; echo ${var##*.}
```

---

