---
title: "very new/ help understanding ' &gt;&gt; '"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-03-29
I noticed that ```
echo 'test' >> file.txt
``` will append to a file and not replace it.


1) Is there a convient (ie: shortscript) way of just replacing the file?

2) I need a reference for `>>` but I don't know where to look. thanks.

---

### Post by jimmy the saint on 2010-03-29
```
echo "text" > file.txt
```

will replace the contents.

---

### Post by uxinn on 2010-03-29
"echo 'test' > file.txt"
replaces your file.

[http://tldp.org/LDP/abs/html/io-redirection.html]("http://tldp.org/LDP/abs/html/io-redirection.html")

---

### Post by jduggan95 on 2010-03-29
```
$man bash
``` 

then in the man page type '/>>' then 'enter'. this will search for all the patterns that have '>>'. Press 'n' to search for the next pattern.

---

### Post by nemilar on 2010-03-29
Without getting too in-depth:

both the > and the >> operators redirect what is called the "standard output", or "stdout" (s-t-d out).  This is, generally speaking, the output of a program on the command line, except for its errors (which are sent to what is called "standard error", or "stderr").

When you do something like:

```
echo "hello, world!" > file1
```

You are telling the shell to take the command ```
echo "hello, world!"
``` and *redirect* its standard output to a file named file1, overwriting anything that is currently there.

Similarly, when you do

```
echo "hello, world!" >> file1
```

You are telling the shell to do the same thing, except instead of replacing the file known as "file1", you are telling the shell to append to it.


The same principle of stdout redirection is in use with command pipes.  You have probably seen something like this before:

```
cat somefile | grep "someword"
```

Which is just saying to the shell, "run the command 'cat somefile' and redirect its standard output to the command 'grep "someword"'.  (As a side note, some linux users hate when people "cat to grep", and would prefer you use the command 'grep "someword" somefile').

Hope that gives you a little more insight into what exactly is going on under the hood.

---

### Post by quista345 on 2010-03-29
What command is used to get the relative path using Ubuntu?

---

### Post by nemilar on 2010-03-29
quista, you can use

```
pwd
```

to get the present working directory.  All paths are relative to this directory (unless you use a leading slash ("/") in which case it is an absolute path).

---

### Post by EssexEagle on 2010-03-29
> **quista345 said:**
> What command is used to get the relative path using Ubuntu?

You already have a thread going [here]("http://ubuntuforums.org/showthread.php?t=1439581").  Your question is a bit off-topic in this thread anyway.

---

