---
title: "search indside compressed files zip, rar, jar"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by 007casper on 2009-07-25
Is there a way to search for files inside zip, rar, jar compression without opening them?

---

### Post by llamabr on 2009-07-25
Yes.  People here lose their entire mind when I say so, but read the man page.

Which sort of file do you want, in particular?

---

### Post by 007casper on 2009-07-25
jar file

---

### Post by wojox on 2009-07-25
You can look inside and see the class files but you can't open them.

---

### Post by 007casper on 2009-07-25
> **wojox said:**
> You can look inside and see the class files but you can't open them.

I am not clear... what do you mean?  

I just wanted to search for a particular text and file in jar files.  Instead of opening one at a time over 600 jar, and zip files... I just wanted to search in batch process to locate particular file and set of words.

---

### Post by QIII on 2009-07-25
Sun's documentation might be a good place to start.

But you can't really look at much besides the manifest by just viewing the JAR file.  But that would at least give you the file names.

You might have to devise some way to iteratively unpack each JAR file in turn, examine the contents of the extracted files, delete the extracted files, unpack the next...

I'd have to fiddle around with it a bit.  I could probably develop a tool, but I'm sure it's been done already.  You might want to see if you can find an application that does that.


[http://java.sun.com/developer/Books/javaprogramming/JAR/basics/](http://java.sun.com/developer/Books/javaprogramming/JAR/basics/)

---

### Post by 007casper on 2009-07-25
thanks for the direction... I am trying to see if there is an app regarding this...

---

### Post by 007casper on 2009-07-26
I came across jarexplorer and jarbrowser.  I like jarbrowser.  However, it doesnt seem to search inside the source file.  It only locates the file names.

Oh, by the way... the man doesnt have anything regarding this... unless, I am looking at it in a funny way.

does anyone have any suggestions to search inside the files in jar?  Thank you.

---

### Post by lkraemer on 2009-07-26
007casper,
This script may be of help.

[http://ubuntuforums.org/showthread.php?t=1053989](http://ubuntuforums.org/showthread.php?t=1053989)

In Windows there was Supersonic Search Tool that worked good,
and even allowed you to search zips etc on a server for a filename by
using Wildcards.  I used it lots.  Linux is a bit harder.

If you know the exact filename you might modify the script.

lkraemer

---

### Post by 007casper on 2009-07-27
Thank you lkraemer!.

I got this code down below.  I need to search for "Hello!World" which the script does a fine job similar to jarbrowser.  However, I need to search inside the file, and replace it to "Hi!Planet".

does anyone have any idea how I can create search and replace tool that goes inside the file that is in jar and replaces the string?  

Thank you.
 
```

#!/bin/sh

LOOK_FOR="Hello!World"

for i in `find . -name "*jar"`
do
  echo "Looking in $i ..."
  jar tvf $i | grep $LOOK_FOR > /dev/null
  if [ $? == 0 ]
  then
    echo "==> Found \"$LOOK_FOR\" in $i"
  fi
done

```

---

### Post by 007casper on 2009-07-27
I found this link
[http://www.unix.com/unix-dummies-questions-answers/39683-find-string-jar-file.html](http://www.unix.com/unix-dummies-questions-answers/39683-find-string-jar-file.html)

I guess I can use grep.  However, I dont know where to go from there. Even though I found more grep samples.  

does anyone know how I can search for some text in all the jar files without extracting it and then replacing that text/string?

---

### Post by 007casper on 2009-08-06
is there a better way to search and replace text in jar, zip files?

---

