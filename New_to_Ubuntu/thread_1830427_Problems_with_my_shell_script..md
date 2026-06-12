---
title: "Problems with my shell script."
date: 2011-08-21
forum: New to Ubuntu
---

### Post by eamonn on 2011-08-21
Hello,

I'm trying to write a shell script to make connecting to a wireless network in the terminal a little easier. 

I'm still working out the kinks. I had some questions about using IF/THEN statements.

I've been using O'Reilly's 'Learning the bash' book and was under the impression that I was using the correct syntax. Still, the IF/THEN statements that I wrote aren't doing what I wan't.

I think my problem might have to do with how I'm getting user input but I'm not sure. 

If anyone could look at my script and give me some pointers that would be great.

---

### Post by AlphaLexman on 2011-08-21
The square brackets '[' and ']' are actually a test construct in bash. In other words, it is a separate command and requires whitespace around each bracket, like this...
```
if [ $CONNECTIONINPUT = 'y' ]
```Also notice the whitespace around the 'equal sign'

**EDIT:** The 'fi' and the 'elif' are out of order. The 'fi' should be after the 'elif' and is probably not needed, just use 'else'

---

