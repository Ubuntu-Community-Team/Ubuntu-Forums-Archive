---
title: "how can I ssh in and leave process running after log out"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2014-11-27
how can I ssh in and leave process running after log out?

I want to close terminal window, but leave the process to complete.

---

### Post by CharlesA on 2014-11-27
Look into screen or tmux
[http://www.howtogeek.com/114582/2-alternatives-to-gnu-screen-for-linux-terminal-multitasking/](http://www.howtogeek.com/114582/2-alternatives-to-gnu-screen-for-linux-terminal-multitasking/)

I prefer screen, myself.

---

### Post by Bashing-om on 2014-11-27
wlraider70; Hi !

Check out 'screen':
```

apt-cache show screen

```

Be one way to do it .

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many ways to 1 end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-11-27
Two options:

1) You can use a terminal multiplexor like screen or tmux to let the job run as the user logged in, even when that user isn't logged in.

2) You can run the job as a daemon, cron job, root job, socket-triggered-job, or other type of job that runs independently of the user logged in.

---

### Post by CharlesA on 2014-11-27
> **ian-weisser said:**
> Two options:

1) You can use a terminal multiplexor like screen or tmux to let the job run as the user logged in, even when that user isn't logged in.

2) You can run the job as a daemon, cron job, root job, socket-triggered-job, or other type of job that runs independently of the user logged in.

Good point on #2. IT all depends on what you want to do.

I run backups via cron but game servers or whatever via a screen session.

---

### Post by QuaxEros on 2014-11-28
There are some good threads all over internet so a quick search gives this one (answer 3 from the included link) 
As he says: no need to install screen or tmux. Linux has commands like: ^Z, bg, fg, disown, nohup etc. included in shell to manage running tasks/jobs.


I found multiple sites with command examples combining multiple options (I'll look around for some worthy edits later).
[http://unix.stackexchange.com/questions/479/keep-ssh-sessions-running-after-disconnection]("http://unix.stackexchange.com/questions/479/keep-ssh-sessions-running-after-disconnection")

And here is the man page from Gnu with the commands for job-control:
[http://www.gnu.org/software/bash/manual/html_node/Job-Control-Builtins.html#Job-Control-Builtins]("http://www.gnu.org/software/bash/manual/html_node/Job-Control-Builtins.html#Job-Control-Builtins")


If you want to start a program directly in background you can just add "&" to the end of the command line like "processName -option1 -option2 &"
(which saves you two step 1 & 2)
Then disown(3) it.

1) If your process is running in the foreground: use "Ctrl-Z" to suspend foreground process (it will stop! send to background(2) to make it continue). 
 This will report the job # of the suspended process, for example:
    [1]+  Stopped                 processName

2) Send processName to the background with "bg %1" (using whatever the job # is following the %).
 This will resume processName in the background.

3) Disown processName with "disown %1" or disown PID.
 Use the -h flag if you want to maintain ownership until you terminate your current shell, like: "disown -h %1".


If you want to check out how "processName" is doing you can bring it back to foreground using "fg %1".
I would wait disowning it till just before logout if you wanna keep an eye on the process.

---

