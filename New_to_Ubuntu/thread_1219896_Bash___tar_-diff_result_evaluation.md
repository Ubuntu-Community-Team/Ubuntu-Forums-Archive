---
title: "Bash :  tar -diff result evaluation"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Martin H. on 2009-07-22
Hi all,
 
 
i want to do the following within a bash - script :
 
Compare existing .tar archive with source of the archive for any changes since 
archive generation.
 
The command works as expected. 
 
But how can i analyze the results of this command? Let's say i want to know whether 
a file has been modified. I could do the following 
 
'tar -df archive.tar OriginalFolder | grep "some message" '
 
but this seems not to be 'elegant' and i don't know if it will work all of the time.
 
Is there a better way to do this ? 
 
Any help is greatly appreciated,
thx in advance
Martin

---

### Post by Mornedhel on 2009-07-22
I just did a quick test, apparently tar -d also returns differently depending on the results of the diff.

```
if tar -df sandbox.tar sandbox/ > /dev/null
then echo "not diff !"
else echo "diff !"
fi
```

```
$ tar -cf sandbox.tar sandbox/
$ ./tardiff.sh
not diff !
$ emacs sandbox/perl/templates.pl [edit something in the file]
$ ./tardiff.sh
diff !

```

---

### Post by Martin H. on 2009-07-22
> **Mornedhel said:**
> I just did a quick test, apparently tar -d also returns differently depending on the results of the diff.
 
```

if tar -df sandbox.tar sandbox/ > /dev/null

```
 
Thx for your answer !
 
What does 
 
```
> /dev/null   
``` 
 
do exactly ? I suppose you distinguish between 
return code 0 and <> 0 ? If so that won't be enough because
any failure in 'tar' will return <> 0 and i can't tell what exactly happened...
(e.g. 'file not found', 'file xy.tar has been changed' )
 
Thank you,
M.

---

### Post by Mornedhel on 2009-07-22
> **Martin H. said:**
> Thx for your answer !
 
What does 
 
```
> /dev/null   
``` 
 
do exactly ?

It means "redirect the standard output to /dev/null". /dev/null is a special file that discards any input and immediately returns end of file when it's used as input. Redirecting to /dev/null is often used when you don't need the output, neither on your terminal nor in a file.


> **Martin H. said:**
> I suppose you distinguish between 
return code 0 and <> 0 ? If so that won't be enough because
any failure in 'tar' will return <> 0 and i can't tell what exactly happened...
(e.g. 'file not found', 'file xy.tar has been changed' )

Yes, my script (it's not really a script though, it was meant to be used to test whether the return value of tar -d could be used) assumes that the file exists. You could test for the existence of the file first, but since I didn't redirect standard error, only standard output, it's possible error messages will still appear. Your original tar -d line has the same behavior except only "some message" is output.

If you want a detailed listing, just remove "> /dev/null".

---

