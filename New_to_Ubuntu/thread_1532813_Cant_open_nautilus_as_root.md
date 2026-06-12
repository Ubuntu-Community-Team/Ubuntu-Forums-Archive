---
title: "Cant open nautilus as root"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-07-17
I am trying to copy some folders into my root folders but I cant start nautilus in root, I get the message shown in the screenshot:

What should I do

---

### Post by bodhi.zazen on 2010-07-17
> **MattDobson said:**
> I am trying to copy some folders into my root folders but I cant start nautilus in root, I get the message shown in the screenshot:

What should I do

Saw a similar thread on this earlier today, I suggest you report it as a bug on launchpad.

Yo can try```
sudo mkdir /root/.config
```

and run gksu nautilus again

---

### Post by k3lt01 on 2010-07-17
Just try
```
sudo nautilus
```and see if that works

---

### Post by Dobbie03 on 2010-07-17
Nope, neither of those worked.  The dialog box didn't pop up but then again neither did nautilus.

---

### Post by k3lt01 on 2010-07-17
Even though this is not a direct answer to your question you could install nautilus-gksu and that will allow you to open folders within nautilus as root.

---

### Post by Dobbie03 on 2010-07-17
Funny thing is I have done that and still it wont work.

---

### Post by k3lt01 on 2010-07-17
Methinks your system has a problem. I have a mastery of stating the obvious I know.

---

### Post by linux18 on 2010-07-17
does PolicyKit Authentication start on startup? if not there's your problem.

---

### Post by Elfy on 2010-07-17
Does it work if you create

```
sudo mkdir /root/.config/nautilus
```

---

### Post by Dobbie03 on 2010-07-17
I'll try those all in the morning, I have given up for the night.  Thanks everyone for the help so far.

---

### Post by bodhi.zazen on 2010-07-17
See this thread :

[http://ubuntuforums.org/showthread.php?t=1530801](http://ubuntuforums.org/showthread.php?t=1530801)

---

### Post by jayanramesh on 2010-07-17
Dear forestpiskie,
my output was

"jayan@jayan-r:~$ sudo mkdir /root/.config/nautilus
[sudo] password for jayan: 
mkdir: cannot create directory `/root/.config/nautilus': No such file or directory
jayan@jayan-r:~$ 

Thank you

---

### Post by jayanramesh on 2010-07-17
Dear MattDobson,

Finally and gladly I found the remedy 

> sudo su (input your password)
mkdir -p /root/.config/nautilus 

and restart.

---

### Post by Windows Nerd on 2010-07-17
> **k3lt01 said:**
> Methinks your system has a problem. I have a mastery of stating the obvious I know.
Now, where is that picture of the ORLY owl...
Wait, here is an improved one!

56k warning: [http://www.southhillshighschool.com/webpages/teachers/teacher_pics/orly.gif](http://www.southhillshighschool.com/webpages/teachers/teacher_pics/orly.gif)

---

### Post by Dobbie03 on 2010-07-17
> **jayanramesh said:**
> Dear MattDobson,

Finally and gladly I found the remedy 

 

and restart.

Awesome, I will try it out asap.
Well done.

---

### Post by Jheric on 2010-08-02
> **jayanramesh said:**
> Dear MattDobson,

Finally and gladly I found the remedy 

 

and restart.

omg I love you. It works!

---

