---
title: "Custom App Panel Issue"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by wgwwm34 on 2011-02-21
So I was created buttons to put on my panel to start and stop my apache server. Unfortunately unlike my other buttons they never prompt me to enter my password to run as root or really seem to do much of anything. I'm positive I have the commands right but just in case here's what I have:

```
sudo /etc/init.d/apache2 start
```
&
```
sudo /etc/init.d/apache2 stop
```

Any ideas?

---

### Post by ajgreeny on 2011-02-21
You will need to turn the command into scripts and point your launcher to those scripts, I think, as you are not simply running an application with a command which is to an executable in one of the $PATH folders, (see output from "**echo $PATH**" for those folders) but are trying to execute a command as if in terminal.

Try ```
bash -c "sudo /etc/init.d/apache2 start"
```as the command and it might work, as that more complex command can have the same action as a script file and may just do the job as well.

---

### Post by wgwwm34 on 2011-02-21
Yeah I just turned them into scripts. Thanks!

---

### Post by ajgreeny on 2011-02-21
> **wgwwm34 said:**
> Yeah I just turned them into scripts. Thanks!
Just for future reference, did you just use the command as I suggested, or turn the commands into full shell scripts?

---

