---
title: "Batch Change ^M to New Line"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by scambro on 2010-05-17
Hello,

This feels like a very basic question but I can't seem to get it to work at all...  I have a directory full of files from DOS, *NIX, MAC, whatever else.  I want to go through each file, look for the ^M (control-m) character and replace it with a suitable line feed.  I wrote the following batch file, but keep getting errors:

```
#/bin/ksh
for fileName in $(ls *.txt): do
cat $fileName | sed s/^M//g >tmp && mv tmp $fileName
done

```

```
./rename.sh: line 3: syntax error near unexpected token `cat'
```

Seems simple enough... What am I missing?  Thanks!

---

### Post by jbrown96 on 2010-05-17
^ is a special character. It means "lock to beginning of line." Try this instead ```
sed s/\^M//g $filename > $filename
```
Edit: That will destructively overwrite the original file. You may want to try outputting to another file to make sure it works properly first.

---

### Post by iponeverything on 2010-05-17
```

sudo apt-get install tofrodos
dos2unix *

```

---

### Post by scambro on 2010-05-17
> **jbrown96 said:**
> ^ is a special character. It means "lock to beginning of line." Try this instead ```
sed s/\^M//g $filename > $filename
```
Edit: That will destructively overwrite the original file. You may want to try outputting to another file to make sure it works properly first.

Now I get the following error:

```
./rename.sh: line 3: syntax error near unexpected token `sed'
./rename.sh: line 3: `sed s/\^M//g $fileName > $fileName'

```

File looks like this:

```
#/bin/ksh
for fileName in $(ls *.txt): do
  sed s/\^M//g $fileName > $fileName
done

```
I'm testing this in a subdirectory figuring a few attempts will destroy my files :)

Thanks!

---

### Post by jbrown96 on 2010-05-17
> **scambro said:**
> Now I get the following error:

```
./rename.sh: line 3: syntax error near unexpected token `sed'
./rename.sh: line 3: `sed s/\^M//g $fileName > $fileName'

```

File looks like this:

```
#/bin/ksh
for fileName in $(ls *.txt): do
  sed s/\^M//g $fileName > $fileName
done

```
I'm testing this in a subdirectory figuring a few attempts will destroy my files :)

Thanks!

I just created a sample file, and I'm not getting any syntax errors; however I did have to put single quotes around the regex ```
sed 's/\^M//g' $fileName > $fileName
``` This won't work if ^M is actually a single character instead of ^ and M. That still wouldn't cause syntax errors though; you just wouldn't get any matches.
Here are my two lame files > ^M lkdsfjlkj lkjdlfsj ^lkjlkj lkjalsdjf
kljaldsjfl lsdkjflj lkjljfm^ ljsladjf ^M
lkasdlfkj ^M and the output >  lkdsfjlkj lkjdlfsj ^lkjlkj lkjalsdjf
kljaldsjfl lsdkjflj lkjljfm^ ljsladjf 
lkasdlfkj 

You may want to check out an ascii table to see if ^M is two characters or one special one.

---

### Post by scambro on 2010-05-17
I think I got it with the following (you were right though, ^M is not two characters, so I used the octal number to get it):

```
#/bin/ksh
for fileName in $(ls *.txt)
do
  cat $fileName | sed 's/\o015/\n/g' > tmp && mv tmp $fileName
done

```

This appears to work.  The dos2unix wasn't working at all for me, I tried that a few times before figuring I'd just have to deal with all of these files with my own script.  

Thanks for the help!

---

