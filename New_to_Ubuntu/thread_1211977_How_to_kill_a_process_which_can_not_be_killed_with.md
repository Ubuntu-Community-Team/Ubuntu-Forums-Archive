---
title: "How to kill a process which can not be killed with &quot;kill P_ID&quot; or &quot;Kill -s ABRT P_ID&quot;"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by legolas_w on 2009-07-13
Hi
I have a process which is in uninterrupted state (based on system monitor) and I have not been able to kill it using

```

kill 4898

OR

Kill -s ABRT 4898

```

Is there anyway to just kill it forcefully?

Thanks.

---

### Post by halitech on 2009-07-13
did you try it with sudo?

---

### Post by Mornedhel on 2009-07-13
kill -9 <pid> sends SIGKILL to the process. If that doesn't kill it, your only other simple option should be killing its parents and hoping they mop their children up.

---

### Post by legolas_w on 2009-07-13
Hi,
I tried with sudo and it is still there, I sent signal 9 to it (several times) and it is still alive. even I sent the signal 9 to it using
```

 sudo kill -s 9  PID


```

and no effect.

---

### Post by sanemanmad on 2009-07-13
Have you tried ```
killall process_name
```

---

### Post by Wim Sturkenboom on 2009-07-13
> **legolas_w said:**
> Hi,
I tried with sudo and it is still there, I sent signal 9 to it (several times) and it is still alive. even I sent the signal 9 to it using
```

 sudo kill -s 9  PID


```

and no effect.It's ***kill -9***, not *kill -s 9*.

---

