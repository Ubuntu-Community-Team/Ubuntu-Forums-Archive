---
title: "Problem with WINE"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Alucard_Jh on 2009-03-17
Whenever I try to do ANYTHING involving WINE, it just dumps me back to the login screen. I need a way to fix this. If anyone knows how to fix this, please respond in this topic or PM. Thank you.

---

### Post by LowSky on 2009-03-17
What are you doing?

Have you tried purging you WINE install and then reinstalling?

---

### Post by Alucard_Jh on 2009-03-17
What do you mean by "Purging" my WINE install? And Yes, I have tried reinstalling multiple times.

---

### Post by bobmatino17 on 2009-03-17
have you run ```
winecfg
```?

---

### Post by BDNiner on 2009-03-17
by purging he means completely uninstalling the application and all configuration files. Config files are normally in a .wine directory in you home folder and most applications will leave these behind when you uninstall them.

---

### Post by Alucard_Jh on 2009-03-17
> **bobmatino17 said:**
> have you run ```
winecfg
```?
WineCFG also boots to login screen.

---

### Post by stchman on 2009-03-17
> **Alucard_Jh said:**
> Whenever I try to do ANYTHING involving WINE, it just dumps me back to the login screen. I need a way to fix this. If anyone knows how to fix this, please respond in this topic or PM. Thank you.

Are you running WINE from the repos, use WINE repos, or did you build it from source?

---

### Post by Alucard_Jh on 2009-03-17
I got it from add/remove programs.

---

### Post by Dougie187 on 2009-03-17
Have you checked your system logs? Located in /var/log probably syslog, possibly messages. Also you can type dmesg to get some information. Look for the time stamp around when you last tried it?

---

### Post by Alucard_Jh on 2009-03-17
Bring
Up
My
Post

---

### Post by Vince4Amy on 2009-03-17
Have you install any graphics card drivers?

---

