---
title: "Shell Interpretor takes up ALL processor power. How can I stop this process?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Bendihossan on 2009-02-23
Hey all, I have the command "sh -c" that starts when I log in and it takes up all my processor power and nearly all RAM for my system to cope. This process never used to be there and has only started occuring within the last few days. I've used pstree to identify the process and it seems to be started by "gnome-session --> Python --> sh".

Also when I look at processes in htop or top at terminal sh -c appears to take arguments(I think) from lsb_release and apt-cache. Any ideas as to how this process can be stopped? Occasionally (after a few hours) the process stops. Also I've tried doing a "killall python" and "killall sh" which removes the process for around a minute before it returns to consume all of my CPU power! 

Please, please help me find a way of either preventing this process from executing or from using all my CPU power :)

---

### Post by llamabr on 2009-02-23
post the output of ps aux, more more helpfully, you can locate the offending pid using top.  Copy the first couple lines of top

---

### Post by Bendihossan on 2009-02-23
Ok, I will do. The process ended itself within a few minutes of logging in this session though usually it returns. If it doesn't then I'll reboot and post the output...

---

### Post by Bendihossan on 2009-02-25
> **llamabr said:**
> post the output of ps aux, more more helpfully, you can locate the offending pid using top.  Copy the first couple lines of top

Output of ps aux (not all of it obviously - output was huge but the offending items are shown):
```
steffy   24585  0.0  0.0   1772   484 ?        S    07:39   0:00 sh -c { lsb_release -is; } 2>&1
steffy   24586  0.0  0.1   4872  3180 ?        S    07:39   0:00 /usr/bin/python /usr/bin/lsb_release -is
steffy   24587  0.0  0.0   1772   488 ?        S    07:39   0:00 sh -c { apt-cache policy 2>/dev/null; } 2>&1
steffy   24588  0.0  1.2  29628 26328 ?        R    07:39   0:00 apt-cache policy

```

I took a screen shot of the htop output shown below. You can see that the first three lines show the offending processes, PIDs and CPU usage. Hope that helps!

---

