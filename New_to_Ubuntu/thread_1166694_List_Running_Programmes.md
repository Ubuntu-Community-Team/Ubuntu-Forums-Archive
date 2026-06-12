---
title: "List Running Programmes"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Pioneer5000 on 2009-05-22
I was wondering if there was a command that showed all running programmes. Just like with Windows when you alt+tab+del then go to applications you can see what is running on computer so you can pick up if there's anything running in the background that you are unaware of. So is there a command for this?


Main reason I ask is because when I went to shut down my computer it said there is a programme "unknown" running and it asked me to confirm if I wanted to shut down and stop the programme from running but I have no idea what this "unknown" programme is.

---

### Post by asmoore82 on 2009-05-22
Open "System -> Administration -> System Monitor"

-OR-

Alt+F2 for "Run" and: ```
gnome-system-monitor
```

---

### Post by nandemonai on 2009-05-22
Or in terminal:

```
top
```

or

```
ps -A
```

My personal favorite is htop but you need to install that separately.

```
sudo apt-get install htop
```

```
htop
```

---

### Post by sahabcse on 2009-05-22
try 

top -u username

For more info follow

[http://sahabm.blogspot.com/2009/02/server-load-top-command.html](http://sahabm.blogspot.com/2009/02/server-load-top-command.html)

---

### Post by x33a on 2009-05-22
> **nandemonai said:**
> 
My personal favorite is htop but you need to install that separately.


another htop lover. it's really configurable and light on resources compared to gnome-system-monitor.

---

### Post by balboost on 2009-05-22
thank you for htop, i didn't know it, now it is installed :)

---

### Post by binbash on 2009-05-22
ps aux

---

### Post by scorp123 on 2009-05-22
> **binbash said:**
> ps aux ps -efH

---

### Post by Pioneer5000 on 2009-05-22
Thanks for the replies guys.  :D

---

