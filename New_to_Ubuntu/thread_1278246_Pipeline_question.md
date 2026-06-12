---
title: "Pipeline question"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by ForgivenByJC on 2009-09-29
I have no return on
```
which mythfrontend | cat
```
Have I done this wrong?  Also,
```
cat /usr/bin/mythfrontend
```gives results, so that is not the problem.  Thanks!  -J

---

### Post by undecim on 2009-09-29
does "which mythfrontend": output anything?

Also, the two commands you posted do completely different things. The first one takes the output of "which mythfrontend" (which should be "/usr/bin/mythfrontend") and sends that as the input to cat. cat should then output "/usr/bin/mythfrontend" (the "| cat" at the end of a command does nothing).

The second command will take the contents of the file /usr/bin/mythfrontend and dump them to your terminal.

---

### Post by ForgivenByJC on 2009-09-29
Yes, ```
which mythfrontend
``` does output ```
/usr/bin/mythfrontend
```

undecim said:> the "| cat" at the end of a command does nothingWhat do you mean by this?

Does pipe ("|") not take the output ("/usr/bin/mythfrontend") from 'which' and pass it to 'cat' to effectively create 'cat /usr/bin/mythfrontend'?

---

### Post by Bachstelze on 2009-09-29
> **ForgivenByJC said:**
> 
Does pipe ("|") not take the output ("/usr/bin/mythfrontend") from 'which' and pass it to 'cat'

It does.

> **ForgivenByJC said:**
> to effectively create 'cat /usr/bin/mythfrontend'?

No. The pipe passes the standard output of a command to the standard input of another command. This is not the same as passing it as an argument on the command-line.

---

### Post by undecim on 2009-09-29
No, each command has an input and an output. These act in a way similar to file (from the program's point of view anyways).

When you pipe a command to another command, you make one program's output that same as the next program's input. What you are doing is the same as running "cat" and typing on the keyboard "/usr/bin/mythfronted"

The "cat" program, when run with no arguments just takes stdin (input) and sends it to stdout (output)

What you are looking to do can be accomplished like this:

cat `which mythfrontend`

the ` (the character under the "~" and next to the "1" key around the command means that bash (your terminal) will evaluate that command and place its output in the command you are running. Effectively, this runs the command:

cat /usr/bin/mythfrontend

which will output the contents of the file /usr/bin/mythfrontend, after the program "which mythfrontend" has closed.

---

### Post by ForgivenByJC on 2009-10-29
Awesome!  Thank you!  I am cleaning up my email and realized I did not get back to this topic.  Thank you for your help. -J

---

