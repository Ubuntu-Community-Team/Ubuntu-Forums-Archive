---
title: "Ghost aMule process??"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by PepeLapiu on 2010-07-16
Okay, I have aMule installed and I added it to the Start up apps list.
But it's rather sporadic as sometimes aMule doesn't start at all when loging on. And when I try to start aMule in terminal I get the following:
```

pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/pepelapiu/.aMule/muleLock)Raising current running instance.
pepelapiu@pepelapiu-laptop:~$
```

But the strange thing is that the terminal tells me aMule is already running but I can't find anything resembling aMule in System Monitor.
So I deleted aMule from the Start Up Apps list but the results are the exact same. aMule won't start at start up (expected) but it still won't start with terminal, same results as above. Terminal tells me it's already running yet I can't find it in SysMon ..... what the hell?!?

Soo I tried to kill aMule in terminal and here are the results:
```

pepelapiu@pepelapiu-laptop:~$ kill -a amule
bash: kill: a: invalid signal specification
pepelapiu@pepelapiu-laptop:~$ kill
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
pepelapiu@pepelapiu-laptop:~$ sudo killall amule
[sudo] password for pepelapiu: 
amule: no process found
pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/pepelapiu/.aMule/muleLock)Raising current running instance.
pepelapiu@pepelapiu-laptop:~$ 
```

I can't start aMule because it's already running and I can't kill it either because terminal tells me there is no process found.

What am I doing wrong here?

Thanx for your help!

Cheers,
PepeLapiu :)

---

### Post by jtarin on 2010-07-16
> **PepeLapiu said:**
> Okay, I have aMule installed and I added it to the Start up apps list.
But it's rather sporadic as sometimes aMule doesn't start at all when loging on. And when I try to start aMule in terminal I get the following:
```

pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/pepelapiu/.aMule/muleLock)Raising current running instance.
pepelapiu@pepelapiu-laptop:~$
```

But the strange thing is that the terminal tells me aMule is already running but I can't find anything resembling aMule in System Monitor.
So I deleted aMule from the Start Up Apps list but the results are the exact same. aMule won't start at start up (expected) but it still won't start with terminal, same results as above. Terminal tells me it's already running yet I can't find it in SysMon ..... what the hell?!?

Soo I tried to kill aMule in terminal and here are the results:
```

pepelapiu@pepelapiu-laptop:~$ kill -a amule
bash: kill: a: invalid signal specification
pepelapiu@pepelapiu-laptop:~$ kill
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
pepelapiu@pepelapiu-laptop:~$ sudo killall amule
[sudo] password for pepelapiu: 
amule: no process found
pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/pepelapiu/.aMule/muleLock)Raising current running instance.
pepelapiu@pepelapiu-laptop:~$ 
```

I can't start aMule because it's already running and I can't kill it either because terminal tells me there is no process found.

What am I doing wrong here?

Thanx for your help!

Cheers,
PepeLapiu :)

Try ```
sudo amule
```

[other possible reasons]("https://answers.launchpad.net/ubuntu/+source/amule/+question/89324")

---

### Post by gandaran on 2010-07-16
> sudo amule
don't ever run root amule!
you can fix the issue by just deleting the existing amule user profile (/home/'user'/.amule) reboot and restart amule again

---

### Post by Zeike on 2010-07-16
> **PepeLapiu said:**
> ```

pepelapiu@pepelapiu-laptop:~$ amule
Initialising aMule 2.2.6 using wxGTK2 v2.8.10
Checking if there is an instance already running...
There is an instance of aMule already running
(lock file: /home/pepelapiu/.aMule/muleLock)Raising current running instance.
pepelapiu@pepelapiu-laptop:~$
```


Sounds like the amule lockfile failed to get removed one time.

Try manually removing it with

"rm -v ~/.aMule/muleLock"

and try starting aMule again.

---

### Post by PepeLapiu on 2010-07-16
It worked! I ran sudo amule and that worked. Then I deleted the content of ~/user/.amule (except for the incoming and temp folders). Then I re-added aMule to the Start Up list and if works great again.

Thanx peep-holes!

Cheers,
PepeLapiu :)

---

### Post by jtarin on 2010-07-16
> **gandaran said:**
> don't ever run root amule!
you can fix the issue by just deleting the existing amule user profile (/home/'user'/.amule) reboot and restart amule again
I agree. You should not run amule as root during normal operation, but at times you will need to do so as to resolve some conflicts with the application and/or process.My suggestion was meant as a step in a repair process as to what works or is broken.

---

