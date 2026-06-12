---
title: "specific port monitoring software"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by ja660k on 2010-01-11
hey guys,

Im wondering if there is an app that will sit on my laptop and monitor ports mainly ssh for activity... preferably a terminal based application that i can just run and will show me when that port has made a connection?

i thought i could write one in java or C but it would take some learning and time, so i thought i'd find out if one exist already?

to clarify i dont want to monitor other machines ports, just my own.

thanks in advance :-)

---

### Post by dmillerct on 2010-01-11
> **ja660k said:**
> hey guys,

Im wondering if there is an app that will sit on my laptop and monitor ports mainly ssh for activity... preferably a terminal based application that i can just run and will show me when that port has made a connection?

i thought i could write one in java or C but it would take some learning and time, so i thought i'd find out if one exist already?

to clarify i dont want to monitor other machines ports, just my own.

thanks in advance :-)

You could use conky and have the information on your desktop. :D

---

### Post by ubudog on 2010-01-11
I'm working on one, will be done soon.  Will post back with a link soon.

---

### Post by DamenW on 2010-01-11
if you are handy with bash or are willing to read a little Snort is the best.  It is a desktop IDS/IPS.  It will monitor anything you want to monitor for network wise.

---

### Post by ja660k on 2010-01-12
snort is really overkill for what i need, though it gives handy info. 

all i need is something to say when a connection to a port is made.

---

### Post by Cheesemill on 2010-01-12
You could use a combination of watch and netstat, give me a while and I'll post back with a command.

---

### Post by iponeverything on 2010-01-12
You can have sshd invoked from xinetd, you can have a wrapper around it do whatever else you like..

---

### Post by aeiah on 2010-01-12
```
netstat -ant | grep 192.168.0.1:22
```

or whatever your internal ip and ssh port are

or you could use grep on the command ```
w
``` such as ```
w | grep -v :0
```

which greps for everything but :0, your local display

---

### Post by ja660k on 2010-01-12
> **aeiah said:**
> ```
netstat -ant | grep 192.168.0.1:22
```

so that is what i want... but is there a way i can automate this to run 
```
netstat -ant | grep 192.168.0.1:22
```
every minute or so?

---

### Post by Cheesemill on 2010-01-13
You can use watch:
```
watch -n 60 'netstat -ant | grep 192.168.0.1:22'
```

---

