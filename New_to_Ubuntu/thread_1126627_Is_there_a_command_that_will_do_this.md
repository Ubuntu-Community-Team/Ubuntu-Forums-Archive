---
title: "Is there a command that will do this?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Warpnow on 2009-04-15
Is there a command that will take all the things in quote in a file and output them all somewhere?

---

### Post by mlentink on 2009-04-15
Uh..
What do you mean by that?
You want everything between quote-marks in a file output to a second file? Will the source file allways be text only, or could it be a binary?

---

### Post by llamabr on 2009-04-15
> **Warpnow said:**
> Is there a command that will take all the things in quote in a file and output them all somewhere?

Ya, it's not clear what you want to do:

```
brock@hops:~$ echo "all the stuff in quotes" > quote.txt
brock@hops:~$ cat quote.txt 
all the stuff in quotes
brock@hops:~$ 

```

---

### Post by amauk on 2009-04-15
```
cat your_file | grep -o '"[^"]*"'
```

---

### Post by hovzio on 2009-04-15
Are you trying to filter out everything between a let of quotes in a file?

```
grep -o '".*"' file 
```

This will get the *first* occurence of anything that is quoted in a file. The quotes must be seperatly be filtered..

EDIT! I started my post before Amauk posted.Amauk's command works way better than the one I just mentioned, if you have 2 occurances of quotes on the same line it will seperate them two. ;)

---

