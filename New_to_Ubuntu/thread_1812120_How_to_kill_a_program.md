---
title: "How to kill a program?"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-25
Hello there,

I pressed the log-off button and I realized I still had programs running. I quickly selected "Lock Screen" and logged back in. I have "Docky" appearing on my screen and not going away. I tried to "Quit" it, remove it from launcher, but it isn't working. Is there a way of killing this unresponsive program through the terminal?

---

### Post by silex89 on 2011-07-25
Hi, yes, just type "xkill" and then click on the app thats frozen. That's all.


Best Luck :D

---

### Post by WubiAR on 2011-07-25
> **silex89 said:**
> Hi, yes, just type "xkill" and then click on the app thats frozen. That's all.


Best Luck :D

Thank you very much. Does Ubuntu have a program similar to that of the Windows Task manager?

---

### Post by LemursDontExist on 2011-07-25
> **WubiAR said:**
> Thank you very much. Does Ubuntu have a program similar to that of the Windows Task manager?

The "System Monitor" program mimics the Task manager pretty well.  From the command line it should be gnome-system-monitor, in Gnome Classic it should be under the system menu, and in Unity you can find it by under Applications->System.

---

### Post by Wim Sturkenboom on 2011-07-25
> **WubiAR said:**
> Thank you very much. Does Ubuntu have a program similar to that of the Windows Task manager?

'*ps -ef*' will give you a list of all running processes and, amongst others, the PID. You can kill a process nicely with '*kill pid#*' and if it does not get killed, '*kill -9 pid#*' will get rid of it.

There might be a GUI based alternative to *ps*, but I never looked at it.

---

### Post by HermanAB on 2011-07-26
I love Xkill.  Very satisfying use of the skull and cross bones.  Just don't click on your desktop by accident...  Yeah, OK, go ahead and do it, if you have nothing important running!

---

### Post by b1gag3 on 2011-07-26
You can also use ```
top
``` to show all running tasks. To kill them you can use the already  mentioned ```
kill #pid
```

---

### Post by amjjawad on 2011-07-26
If you are not a friend of CLI ;)

By the way, don't freak out, I'm using Mint 11 but it has exactly the same app (System Monitor).

---

### Post by LemursDontExist on 2011-07-26
> **Wim Sturkenboom said:**
> '*ps -ef*' will give you a list of all running processes and, amongst others, the PID. You can kill a process nicely with '*kill pid#*' and if it does not get killed, '*kill -9 pid#*' will get rid of it.

There might be a GUI based alternative to *ps*, but I never looked at it.

If you're looking for a specific process, *pgrep* and *pkill* are nice shortcuts. So for instance '*pkill firefox*' would kill all firefox proceses nicely, and '*pkill -9 firefox*' would kill them dead no matter what.

---

### Post by Swagman on 2011-07-26
or 

```
pidof <program name> (eg:banshee) 
```

7719

paul@Main-Computer:~$

```
 Kill 7719 
```

---

### Post by Simian Man on 2011-07-26
If you use KDE, you can just hit Crtl-Alt-Esc and click on the program you want to kill.

---

