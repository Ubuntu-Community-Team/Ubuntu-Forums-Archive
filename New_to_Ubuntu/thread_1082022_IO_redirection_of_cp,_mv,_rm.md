---
title: "I/O redirection of cp, mv, rm"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by munishvit on 2009-02-27
i encountered only few commands which can accept standard inputs. is there any way to redirect the inputs (or arguments) of commands like cp, mv, rm to stardard input.

---

### Post by orethrius on 2009-02-27
I'm curious, what exactly do you mean by "standard" inputs?  Are you referring to STDIN or common usage flags, or something else?

---

### Post by Bölvaður on 2009-02-27
> **munishvit said:**
> standard inputs.

are you talking about regular expressions?


or pipes?

---

### Post by orethrius on 2009-02-27
I know!  It's bugging the crap outta me, I can hardly wait for an answer! :D
I wanted to talk to him over IM, but either he's not online, or he's set his YIM status to Invisible.

---

### Post by munishvit on 2009-02-27
> **orethrius said:**
> I'm curious, what exactly do you mean by "standard" inputs?  Are you referring to STDIN or common usage flags, or something else?

i mean to say...
cmd < file      (Take input for cmd from file)
like we do in 'cat'.

suppose we need to do:
mv -R /home/username/dir1 /home/username/dir2/dir3
i want to take the argument '/home/username/dir1 /home/username/dir2/dir3' as an input from a file.
Is there any way...plz

---

### Post by sisco311 on 2009-02-27
```
cmd $(cat file)
```
or
```
cmd `cat file`
```

---

### Post by munishvit on 2009-02-27
> **sisco311 said:**
> ```
cmd $(cat file)
```
or
```
cmd `cat file`
```

you r right, but this way some of the metacharacters (contained within input file) don't work (such as quotes and backslash)

---

### Post by unutbu on 2009-02-27
Can you give an example of the contents of file?
Do the file names have spaces in their names?
How are the arguments separated?

---

### Post by orethrius on 2009-02-28
> **munishvit said:**
> you r right, but this way some of the metacharacters (contained within input file) don't work (such as quotes and backslash)

I forget how to do it from a file, but I do remember that metacharacters need to be escaped before they're passed to the command (that is, \" or \\, where the first backslash escapes the second character).

---

