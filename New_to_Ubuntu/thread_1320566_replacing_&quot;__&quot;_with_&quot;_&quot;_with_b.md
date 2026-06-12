---
title: "replacing &quot;  &quot; with &quot; &quot; with bash"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by shortridge11 on 2009-11-09
I have a large assortment of files, and some of them have 2 spaces in a row.  I want to replace those with a single space.  Does anyone know of a simple script to rename said files?  Even if you could start me on the path i might be able to get it.  I have 10k files, so it might have to be looped with something like 

ls | while read filename; do rename something; done

I'm not looking to do this in krename

---

### Post by DaithiF on 2009-11-09
hello again shortridge11 :)
this should do it:
```
ls | while read filename; do rename 's/  / /g' "$filename"; done
```

---

### Post by scottch.eezem on 2009-11-09
```
ls | while read filename ; do mv "$filename" "${filename//  / }" ; done
```


cheers

---

### Post by kaibob on 2009-11-09
> **scottch.eezem said:**
> ls | while read filename ; do mv "$filename" "${filename//  / }" ; done

I believe there's a typo in scottch's suggestion--there needs to be two spaces after "//".

```
ls | while read filename ; do mv "$filename" "${filename//  / }" ; done
```

---

### Post by Paddy Landau on 2009-11-09
If you prefer a GUI, try [pyrenamer]("http://www.infinicode.org/code/pyrenamer/"). It will allow you to 'test' by showing what will happen if you go ahead. Saves you from making mistakes.

---

### Post by ghostdog74 on 2009-11-09
> **scottch.eezem said:**
> ```
ls | while read filename ; do mv "$filename" "${filename//  / }" ; done
```


cheers

don't have to use ls and while loop. just a for loop will do
```

for file in *
do
 mv ...........
done

```

---

### Post by ghostdog74 on 2009-11-09
> **shortridge11 said:**
> I have a large assortment of files, and some of them have 2 spaces in a row.  I want to replace those with a single space.  Does anyone know of a simple script to rename said files?  Even if you could start me on the path i might be able to get it.  I have 10k files, so it might have to be looped with something like 

ls | while read filename; do rename something; done

I'm not looking to do this in krename

if you have Python 2.4+ , you can use the script (see my sig called File Renamer).

usage (2 files with 2 or more spaces): 
```

$ ls -1
a  b.txt
c       d.txt

$ filerenamer.py -p "\s{2,}"  -e " " -l "*"
==>>>>  [ /home/c       d.txt ]==>[ /home/c d.txt ]
==>>>>  [ /home/a  b.txt ]==>[ /home/a b.txt ]


```

remove -l to commit changes. If you make a mistake, you can revert immediately, use -r option

---

