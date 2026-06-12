---
title: "Sharp Driver Setup Program Requires Root login.  How do I log in as Root?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by pastorbobbyp on 2010-05-04
I have downloaded a package of drivers from Sharp support.  They were in a tar, which I extracted.  There is a Setup program.  When I try to run the setup program it gives me a message telling me that I need to be logged in as Root to be able to run this program.  I have my user privileges set at administrator.  How do I log in as Root in order to run this program?  Thanx.  Bob

---

### Post by jrothwell97 on 2010-05-04
You can't log in as root in Ubuntu, it's disabled (with good reason.)

On the other hand, you can tell the system to run that particular program as root. If it's a command-line application, run
```
sudo *commandname*
```

(Note that when you type in your password, nothing will be displayed on the screen. Don't worry: this is normal, your password is still being entered.)

If it's a graphical application, run
```
gksudo *commandname*
```

You should not use *sudo* for graphical applications as it's known to cause permissions problems down the line.

---

### Post by louieb on 2010-05-04
> **pastorbobbyp said:**
> ...  How do I log in as Root ...

With Ubuntu you don't. You use sudo or gksudo to get root privileges. 

to get a privileged terminal session  

```
sudo -i
```

enter you password and your good to go.

more here [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

also the [forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

