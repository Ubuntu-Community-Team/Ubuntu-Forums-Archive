---
title: "How to search through all files in a folder?"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by kramer65 on 2010-11-09
Hello,


I've got a folder in which I have all different types of files (html, js, php etc.) including files in folders within that folder. I now want to search for a specific word within all those files simultaneously.

Does anybody know how this would be possible? Any tip is welcome!

---

### Post by Hippytaff on 2010-11-09
I don't know if I'm misunderstanding what you want to do but maybe
 
```

grep -ir (word)

```

---

### Post by col48 on 2010-11-09
grep text-being-hunted top-folder -r

looks like it would do the job on its own, but you might check the options of grep to refine your search.

eg -r (as above) searches subfolders recursively, which is what you want..
-i makes the search insensitive to case
-l only prints the names of the files where it is found without adding the context of the hit


and you might want to direct the output into a file if there might be many hits.

---

### Post by toekneewood on 2010-11-09
> **Hippytaff said:**
> I don't know if I'm misunderstanding what you want to do but maybe
 
```

ls -a | -i grep (word)

```
 
or look into awk :-)

Congratulation Hippytaff on your 1000's bean :-)

---

### Post by Hippytaff on 2010-11-09
> **toekneewood said:**
> Congratulation Hippytaff on your 1000's bean :-)
 
Thanks - 1000 stupid questions asked and the odd almost useful peice of advice :-)

---

### Post by thomaswei on 2010-11-09
Or try the Magnifier-Symbol in Nautilus, if you don't wanna use the CLI

---

### Post by toekneewood on 2010-11-09
grep -i word * (does all files in that directory case insensitive)
grep -ir word * (does all files in that directory and goes recursively into other directories)

---

### Post by Hippytaff on 2010-11-09
[QUOTE=Hippytaff;10093470]I don't know if I'm misunderstanding what you want to do but maybe
 
```

grep -ir (word)

```
 
Going to edit my original post to save confusion :-)

---

### Post by toekneewood on 2010-11-09
This one might be what you are looking for.  Find text within a specific types of files
```

find . -type f | egrep 'js|php|sh' | sed -e "s@'@\\\'@g" -e "s@ @\\\ @g" | xargs grep "word"

```

---

### Post by kramer65 on 2010-11-09
Hi everybody! Thanks for the overwhelming response!

I hoped there was some kind of handy tool since I am not so good with the terminal. But hey, let's give it a try.

I want to search for the word "kramer65", so I went to the folder using 
```
cd Desktop/thefolderwhichIwanttosearch
```
I then typed
```
grep -ir kramer65
```

The total of files in the folders (and all the subfolders) is about 9MB of which at least 90% are text files. I typed the command above about 10 minutes ago, but nothing seems to happen (although I know the word is in there for sure). :confused:
Could it be that it takes a long time because it are so many files, or is that not true?

Any help welcome!

---

### Post by toekneewood on 2010-11-09
If you click "Places" from the menu and then "search for files" this should also give you what you need

---

### Post by toekneewood on 2010-11-09
You will not see any cursor icons movement unless it finds something and then when it has finished.  If you have Binary files in the search area this might also cause it to take a while, or maybe throw a wobblier

---

### Post by kramer65 on 2010-11-09
Ah great! That works a lot easier.. :-)

Thank you very much!

---

### Post by toekneewood on 2010-11-09
Just in case you do fancy doing it at the CLI, this command will exclude binary files
```

grep -rI --exclude-dir="\.svn" "word" *

```

---

