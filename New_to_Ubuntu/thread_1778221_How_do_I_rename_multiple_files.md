---
title: "How do I rename multiple files?"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Roger Allott on 2011-06-08
I want to do a fairly simple procedure.

I have a number of files in my home folder that begin with the characters "Sixteen" and instead I want them to begin with the characters "16".

Having read [http://www.cyberciti.biz/tips/renaming-multiple-files-at-a-shell-prompt.html](http://www.cyberciti.biz/tips/renaming-multiple-files-at-a-shell-prompt.html) I got the impression that the code I'd need would be:
```
laptop:~$ rename Sixteen 16 Sixteen*
```

but I'm getting the error message:
```
Bareword "Sixteen" not allowed while "strict subs" in use at (eval 1) line 1.
```

What am I doing wrong? What should my command be?

---

### Post by sisco311 on 2011-06-08
Ubuntu uses the Perl based rename command by default.

So either try something like: 
```
rename **--no-act** 's/^Sixteen/16/' Sixteen*
```
*NOTE: Invoked with **--no-act** the command will only show what files would have been renamed.*

or if you want to use the rename command explained at cyberciti.biz, then replace **rename** with **rename.ul**.

---

### Post by kouhinn on 2011-06-08
try :
find /dir -type f -name "sixteen*" -exec mv {} "${echo {} | sed 's/sixteen/16/'}" ;

---

### Post by Roger Allott on 2011-06-08
Brilliant!

Thank you very much, sisco311.

---

### Post by sisco311 on 2011-06-08
> **Roger Allott said:**
> Brilliant!

Thank you very much, sisco311.

You're welcome!

---

### Post by larmet on 2012-05-13
I have a similar problem; I have to rename some files that are currently named as:

2012_-05-0019?001.dd  
2012_-05-0019?027.dd  
2012_-05-0019?053.dd  
2012_-05-0019?079.dd  
2012_-05-0019?105.dd

and I need to rename them to:

2012-05-0019.001
2012-05-0019.027
2012-05-0019.079
2012-05-0019.105

and so on. How can I do this via command line?

---

### Post by Vaphell on 2012-05-13
```
rename --no-act  's/([0-9]+)_-([0-9]+)-([0-9]+)[?]([0-9]+).dd/$1-$2-$3.$4/' *.dd
```

---

### Post by sisco311 on 2012-05-13
> **larmet said:**
> I have a similar problem; I have to rename some files that are currently named as:

2012_-05-0019?001.dd  
2012_-05-0019?027.dd  
2012_-05-0019?053.dd  
2012_-05-0019?079.dd  
2012_-05-0019?105.dd

and I need to rename them to:

2012-05-0019.001
2012-05-0019.027
2012-05-0019.079
2012-05-0019.105

and so on. How can I do this via command line?

```

rename --no-act 's/2012_-05-0019\?(.*).dd/2012-05-0019.$1/' 2012_-05-0019*

```

---

