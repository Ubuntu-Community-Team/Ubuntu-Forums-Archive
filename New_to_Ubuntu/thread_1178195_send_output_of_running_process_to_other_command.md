---
title: "send output of running process to other command"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by benfindlay on 2009-06-04
Hi there, I am wondering if it is possible to pipe the output of a command while it is still running through grep to search for certain lines.

Here's the specifics:

I am running autopsy with remote hosts and ports specified using the command line, for example:```
./autopsy -p 9001 192.168.1.100
```When it activates, it ties up terminal until I use CTRL+C to terminate it. I have tried the following:
```
./autopsy -p 9001 192.168.1.100 | grep [search phrase] >> info.txt
```to send the output to a file, but this doesn't do this until after the process is terminated, which is too late.

Any ideas?

Cheers

Ben

---

### Post by kpkeerthi on 2009-06-04
Why not redirect the output of the running process to a file and then grep on the file?

```

./autopsy -p 9001 192.168.1.100 > autospy.log 2>&1 &

```

```

grep [search phrase] autospy.log

```

---

### Post by benfindlay on 2009-06-04
> **kpkeerthi said:**
> Why not redirect the output of the running process to a file and then grep on the file?

```

./autopsy -p 9001 192.168.1.100 > autospy.log 2>&1 &

```

```

grep [search phrase] autospy.log

```

Outstanding, that did the trick! Thanks!

Out of interest, what does the 2>&1 do?

Thanks

Ben

---

### Post by benj1 on 2009-06-04
just run the process in the background,
add an '&' suffix to the command

---

### Post by benfindlay on 2009-06-04
A normal & doesn't work it seems. From what I can tell, the process isnt really meant to be run in background.

Putting an & between the ./autopsy and | grep seems to prevent the pipe from working, and if it is moved to the end of the line, grep won't carry out the instructions until the application is terminated. This is a problem as autopsy generates a unique URL for the remote hosts to connect to each time it is run, meaning that I can't get that URL until after it terminates (and the next time it generates a new one).

---

### Post by kpkeerthi on 2009-06-04
> **benfindlay said:**
> Outstanding, that did the trick! Thanks

Out of interest, what does the 2>&1 do?

Thanks

Ben

2 is the file descriptor for standard error and 1, standard output.
2>&1 sends 2 (the errors) to the same place where 1 (the output) is also sent, in our case to autospy.log file.

---

### Post by benfindlay on 2009-06-04
Excellent, thanks again!

Ben

---

