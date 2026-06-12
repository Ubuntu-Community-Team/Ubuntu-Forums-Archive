---
title: "unable to get the stop command to work"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by Talistan on 2009-12-15
Hello, and sorry for reposting, but I accidently put this in another forum I will remove
I am running a program and in the shell I do

alex@alex:~$ jobs -l
[1]+  2590 Running                 brasero &

I can use `kill' with a stop signal to stop it and then start it again, but in the tutorials I am looking at it speak of the stop command which I only find the man pages for. 

alex@alex:~$ stop  2590
stop: Unknown job: 2590

but the man stop pages are the same for initctl
alex@alex:~$ initctl stop 2590
initctl: Unknown job: 2590

So I am confused about how to get these commands to work, if I am able to read the man pages correctly. I would like to learn how to use these commands that are available to do the purpose of kill as well.

All the best and thanks.

---

### Post by ibuclaw on 2009-12-15
The following commands:
```

start
stop
restart
reload
status

```
Are for handling **services**, not applications.

To kill applications via their PID, use the 'kill' command
```
kill -9 **2590**
```
Alternatively, if you don't which to end the process, but instead detach it from the terminal.
```
disown
```
Regards
Iain

---

### Post by Talistan on 2009-12-15
Awesome, answer, was so confused! 
Thanks tons!

---

