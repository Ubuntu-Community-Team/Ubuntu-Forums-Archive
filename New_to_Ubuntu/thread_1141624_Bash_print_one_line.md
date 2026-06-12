---
title: "Bash print one line"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-04-28
this is probably a simple thing that i dont know how to do.
i have multi line output, and i am writing a script that uses the lines as arguments.
how do i cut out only line from the output? 
thanks in advance for any and all help.

---

### Post by Tibuda on 2009-04-28
I can't understand very well what you want. If you want only the first line of the output, you can pipe the command to head, like this:
```
cat longfilename | head -n 1
```

---

### Post by mjheagle8 on 2009-04-28
i want to print any one specific line from an output.

---

### Post by Tibuda on 2009-04-28
Hmm... What about piping head to tail? Like this, for the 20th line:
```
**your command** | head -n **20** | tail -n 1
```

---

### Post by kaibob on 2009-04-28
> **mjheagle8 said:**
> i want to print any one specific line from an output.
How do you want to identify the line to print? If by line number, I believe awk will do what you want. For example, the following prints line 3 of a file:

```
awk 'NR==3' file
```

The following prints lines 1 to 3:

```
awk 'NR==1,NR==3' file
```

You can also pipe output through awk:

```
cat file | awk 'NR==1,NR==3'
```

---

### Post by llamabr on 2009-04-28
If none of that helps, maybe you could give an example of what you want.  I've read your question a few times, and can't figure out what you want to do.

---

