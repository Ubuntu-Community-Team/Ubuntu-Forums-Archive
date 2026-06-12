---
title: "What the devil is backend?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Gitanes on 2010-12-15
Something is hogging the cpu on my desktop.  When I use the command "top" I get a list of running programs.  There are two instances of something that is identified under the COMMAND column as "backend".  These a jumping around in %CPU of up to 49% a piece though they only take up 0.4 and 0.5 in %MEM.  Any idea as to what these processes are and how I might tame them?

---

### Post by elvisd on 2010-12-15
hi try to use the command
```
ps -eo pcpu,args|sort -rn|head
```
to find out the command that launched 'backend' to know a bit more

---

### Post by eriktheblu on 2010-12-15
[http://manpages.ubuntu.com/manpages/maverick/man7/backend.7.html]("http://manpages.ubuntu.com/manpages/maverick/man7/backend.7.html")
This one perhaps?

---

### Post by Gitanes on 2010-12-15
I've no idea what it was.  I rebooted and it was gone and nothing I've done since has generated a reappearance.  I'm assuming it probably would have been safe to kill the process.  

Thanks for that terminal command, I'll use that to see if I can track it down should it reappear (and before killing it next time).

Pipe smoker here too, Erik

---

