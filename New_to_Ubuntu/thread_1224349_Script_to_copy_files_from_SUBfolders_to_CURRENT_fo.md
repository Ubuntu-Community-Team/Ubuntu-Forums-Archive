---
title: "Script to copy files from SUBfolders to CURRENT folder"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by drkameleon on 2009-07-27
Hello everybody!

I've got a folder containing numerous subfolders, which in turn containing PDF and CHM files...

```
/Current
/---------> SubFolder 1
/---------------------> A.pdf
/---------------------> B.pdf
/---------> SubFolder 2
/---------------------> C.pdf
/---------------------> D.chm
/ .. .. .. ..
```

Could you suggest a script which I could use in order to copy ALL the PDF & CHM files from the subfolders to the current folder?

Thanks in advance!

---

### Post by drkameleon on 2009-07-27
Anyone ??? :confused:

---

### Post by VCoolio on 2009-07-27
If there are only subfolders and no sub-subfolders you can do
cp */*.chm ./ & cp */*.pdf ./
right?

---

### Post by cosine352 on 2009-07-27
> **drkameleon said:**
> Hello everybody!

I've got a folder containing numerous subfolders, which in turn containing PDF and CHM files...

```
/Current
/---------> SubFolder 1
/---------------------> A.pdf
/---------------------> B.pdf
/---------> SubFolder 2
/---------------------> C.pdf
/---------------------> D.chm
/ .. .. .. ..
```

Could you suggest a script which I could use in order to copy ALL the PDF & CHM files from the subfolders to the current folder?

Thanks in advance!

this should work

> find current/ -name '*.pdf' | xargs mv -t current

---

### Post by kaibob on 2009-07-27
The following find command will search recursively on multiple filename extensions in the current directory and copy matching files to the current directory:

```
find . \( -iname '*.pdf' -o -iname '*.chm' \) -type f -exec cp '{}' . \;
```

---

