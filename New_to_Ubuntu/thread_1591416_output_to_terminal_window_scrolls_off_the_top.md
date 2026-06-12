---
title: "output to terminal window scrolls off the top"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by T. Jump on 2010-10-09
I'm working on a toolchain build that has errors. When I went to review the output script that displays in the terminal window I only had a portion of the script (the end portion) and all the beginning parts of the script were not accessible (by scrolling to the top of the window).
 
What is happening? And how do I get to the full script?
 
Ubuntu 9.10

---

### Post by CharlesA on 2010-10-09
Can you output it to a file, or pipe it to less?

---

### Post by T. Jump on 2010-10-09
Big Newbie here. I don't know how to do either of these. I was reading about "less" but only with regard to the history and not an active terminal window.

---

### Post by mike2357 on 2010-10-09
Sending output to a file, instead of the screen is quite simple.  It's called redirection, and a good discussion is at this web site:
[http://en.wikipedia.org/wiki/Redirection_(computing)]("http://en.wikipedia.org/wiki/Redirection_(computing)")

So if your command was "mycommand", you could send all of the output to a file called "OUT", and run it in the background with this command:

```
mycommand > OUT 2>&1 &
```

Don't worry too much about the 2>&1 part, but it is discussed in the web site I referenced.

You can still watch the progress of "mycommand" while it's running with this command:

```
tail -f OUT
```

---

### Post by T. Jump on 2010-10-09
Great. Almost there. I have the > working but what is "tail"? If I want to watch the output would it be:  command > -f OUT or does the word "tail" need to be there?

---

### Post by formaldehyde_spoon on 2010-10-09
> **mike2357 said:**
> 
```
mycommand > OUT 2>&1 &
```
or 
mycommand &> OUT &

for the same effect.

---

### Post by mcduck on 2010-10-09
> **T. Jump said:**
> Great. Almost there. I have the > working but what is "tail"? If I want to watch the output would it be:  command > -f OUT or does the word "tail" need to be there?

Tail is  a program used to view the last lines of a text file. The -f option tells tail to keep on reading the file, so when new lines are added tail will print them for you. (one cmmon use for tail is monitoring your system logs, try "tail -f /var/log/syslog", for example). There's also "head" which works in similar way, only reading from the beginning of a file instead of the end.

So no, you can't redirect command output to "-f". It's not a file, and it's not a program.

What you'd do is run whatever command you run, redirecting it's output to a text file. (somecommand > output.txt 2>&1) and then at the same time run (tail -f output.txt) to read the file. You can do the reading in another terminal, or send your original command to work in background (by adding a "&" to the end of the command) and run tail in the same terminal.

---

### Post by T. Jump on 2010-10-09
Great. Then all is done here. I have this all working. Thank you!!

---

