---
title: "grepping text and writing it in one line"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-12-01
Hello,
I have two txt files on my computer that each contain one value. I want to take these two values and write them separated by a tab in the same line of a third file.
It is like that.
Content of file A.txt: A
Content of file B.txt: B
Content of the resulting file: A     B

How can I do that?

---

### Post by Hippytaff on 2010-12-01
```

cat file-A | grep A >> file-A-B
cat file-B | grep B >> file-A-B

```
but they won't be formatted in file A-B as you want...I'm not sure grep has this finctionality, for this your better off looking into awk :-)

---

### Post by SeijiSensei on 2010-12-01
```

echo -n $(grep A file-A) > file-A-B
echo -n -e "\t" >> file-A-B
echo $(grep B file-B) >> file-A-B

```

should do what you want.  I made a couple of modifications to Hippytaff's suggestion.  

First, I used echo to enable me to write it all in one line. The '-n' switch suppresses the newline it would write by default in the first two commands.  To make this work with echo I have to use the $() operator that returns the result of the grep command as a string.  The second echo uses the '-e' switch to enable extended characters like the tab (\t).  You may not need the double-quotes around the tab character, but make sure you don't use single quotes.  That will insert a literal '\t' in the result.  The last echo doesn't include a '-n' so the result will end with a newline.

BTW, you can avoid using "cat" most of the time in the shell.  Either the command takes a filename as a parameter, like grep does, or you can use the "<" character to read the file like this:

grep A < file-A

which is equivalent to

grep A file-A 

and also to 

cat file-A | grep A

---

### Post by jal on 2010-12-01
cat a.txt b.txt | tr '\n' '\t'

---

### Post by jal on 2010-12-01
or, grepping through a multi-line file, maybe

```
sed -n -e '/searchterm1/p' -e '/searchterm2/p' a b | tr '\n' '\t'
```

---

### Post by sisco311 on 2010-12-01
> **SeijiSensei said:**
> ```

echo -n $(grep A file-A) > file-A-B
echo -n -e "\t" >> file-A-B
echo $(grep B file-B) >> file-A-B

```

should do what you want.  I made a couple of modifications to Hippytaff's suggestion.  

First, I used echo to enable me to write it all in one line. The '-n' switch suppresses the newline it would write by default in the first two commands.  To make this work with echo I have to use the $() operator that returns the result of the grep command as a string.  The second echo uses the '-e' switch to enable extended characters like the tab (\t).  You may not need the double-quotes around the tab character, but make sure you don't use single quotes.  That will insert a literal '\t' in the result.  The last echo doesn't include a '-n' so the result will end with a newline.


Instead of echo, I would use tr to replace the newline with a tab:
```
grep -m1 -e a file.a | tr '\n' '\t' > output
grep -m1 -e b file.b >> output
```

> **SeijiSensei said:**
> 
BTW, you can avoid using "cat" most of the time in the shell.  Either the command takes a filename as a parameter, like grep does, or you can use the "<" character to read the file like this:

grep A < file-A

which is equivalent to

grep A file-A 

and also to 

cat file-A | grep A

+1

@OP

In general, if you have to redirect multiple commands to a file, you can do something like:

```

#!/bin/bash


exec 6>&1            # Link file descriptor #6 with stdout.
                     # Saves stdout.

exec > ./output      # stdout replaced with file "./output".

# All output from commands in this block sent to file "./output"

grep -m1 -e a file.a | tr '\n' '\t'
grep -m1 -e b file.b

exec 1>&6 6>&-       # Restore stdout and close file descriptor #6.

```

---

### Post by Hippytaff on 2010-12-01
> **Hippytaff said:**
> ```

cat file-A | grep A >> file-A-B
cat file-B | grep B >> file-A-B

```but they won't be formatted in file A-B as you want...I'm not sure grep has this finctionality, for this your better off looking into awk :-)

lol, I'm such an amature :-)

---

