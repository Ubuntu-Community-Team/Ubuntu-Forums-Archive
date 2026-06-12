---
title: "Running Python in the background"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by izacboy_123 on 2011-06-13
Hi!

I have managed to get my VPS setup to run my python server! However, if I use this command:

> Python server.py

- The server runs, but it's stuck on PuTTy, and if I close PuTTy, the server closes! How can I run the Python program in the background so I can still use PuTTy to do things while the server is running in the background, and continues to run on my VPS even after closing PuTTy? Also, once the server is running in the background, how can I stop it?

Thanks!

---

### Post by compmodder26 on 2011-06-13
Try:

```
Python server.py &
```

This will put it to the background.  This will however still send all of its output to standard output (aka your terminal window).  

If you wish to capture all of its output do this:
```
Python server.py > /path/to/logfile 2>&1 &
```

Now to stop it when it's in the background, type:
```
ps aux | grep "server.py"
```

This should show a line that contains the PID (Process ID) of the server instance.  

You can then do:
```
kill pid_of_process
```

where "pid_of_process" would be replaced by the pid you found from the command above.

Research the "kill" command to figure out different ways of asking your program to shut down.

---

### Post by izacboy_123 on 2011-06-13
> **compmodder26 said:**
> Try:

```
Python server.py &
```

This will put it to the background.  This will however still send all of its output to standard output (aka your terminal window).  

If you wish to capture all of its output do this:
```
Python server.py > /path/to/logfile 2>&1 &
```

Now to stop it when it's in the background, type:
```
ps aux | grep "server.py"
```

This should show a line that contains the PID (Process ID) of the server instance.  

You can then do:
```
kill pid_of_process
```

where "pid_of_process" would be replaced by the pid you found from the command above.

Research the "kill" command to figure out different ways of asking your program to shut down.

Ah, that does work, thanks!

[s]But I am still having the problem of the server.py closing when I close the connection to PuTTy. How can I keep server.py running in the background forever? Until I use the Kill command to kill it, or the VPS reboots![/s]

I learnt how to use the nohup command! :P

Thanks!

---

