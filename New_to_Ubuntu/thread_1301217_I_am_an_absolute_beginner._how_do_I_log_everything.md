---
title: "I am an absolute beginner. how do I log everything?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by petrockthief on 2009-10-25
After an hour or so of Bashing and getting all kinds of errors and the like. How do I view the record of all that was typed, spat out at me, called to run, what time the power went out, etceterea

---

### Post by martrn on 2009-10-25
If you are talking about typeing bash command at a terminal and want the history of commands you typed, type :

```
history
```

---

### Post by petrockthief on 2009-10-25
Oh why thankyou m. But I suspect you understood what it was I meant when I refered to the Bashing- it is so full of errors I need this too does history do that? You did not say. What about this:

```
activity
```

---

### Post by Sef on 2009-10-25
1. What are you trying to do that gives you all those errors? 

2. Could you please post some of those errors.

---

### Post by petrockthief on 2009-10-25
Bashing.

```

bash
bash
bash
2b
mic
b4
bash
bash
bash
7-zip
bash

```

Pardon me if you think I'm being rude, it is on another thing and it has no knowledge of the sweet bit stream that is the internet. What to do about that?

```

Adept
~Adpet

```

---

### Post by martrn on 2009-10-25
Hi pt,
> But I suspect you understood what it was I meant when I refer-ed to the Bashing - it is so full of errors I need this too, does history do that? You did not say. What about this: activity 

Need to watch - Need eyes for activity.  Need sensors.

> 
Pardon me if you think I'm being rude, it is on another thing and it has no knowledge of the sweet bit stream that is the internet. What to do about that?


Learn.

> 
Adept
~Adpet


Try apt-get instead.
```
apt-get irc
apt-get xchat
```

> Bashing.Pardon me if you think I'm being rude, it is on another thing and it has no knowledge of the sweet bit stream that is the internet. What to do about that?


[http://en.wikipedia.org/wiki/Internet]("http://en.wikipedia.org/wiki/Internet")
[http://en.wikipedia.org/wiki/Bash]("http://en.wikipedia.org/wiki/Bash")
[http://en.wikipedia.org/wiki/Irc]("http://en.wikipedia.org/wiki/Irc")

---

### Post by petrockthief on 2009-10-26
Curiously enough I cannot get the internet on anything other than this windows computer. Could you take a look at my question here at [http://ubuntuforums.org/archive/index.php/t-1079344.html](http://ubuntuforums.org/archive/index.php/t-1079344.html)?

Basically I need to tell a config file where to point to in terms of a usb thing. /dev/ttyUSB0 is posted but that does not work on Kubuntu 6.06. I tried some other routes but to no avail.

---

### Post by rockstarrem on 2009-10-26
Can I ask why your using Kubuntu 6.06?

---

### Post by martrn on 2009-10-26
> **petrockthief said:**
> Curiously enough I cannot get the internet on anything other than this windows computer. Could you take a look at my question here at url:http:u/url? Basically I need to tell a config file where to point to in terms of a usb thing. /dev/ttyUSB0 is posted but that does not work on Kubuntu 6.06. I tried some other routes but to no avail.

T-Mobile Work fine on ubuntu, not sure of your model, but should work straight off in a new ubuntu installation.

The kernel on 6.06LTS is not just not going to work.  You need a newer kernel, aka you need to upgrade your os to the latest for it to work.

T-Mobile-equipment all work fine, on the latest kernels.

---

### Post by ikisham on 2009-10-26
From what I researched, the output of the terminal don't get logged unless you ask it to. Look in [this]("http://ubuntuforums.org/showthread.php?t=396244") thread, the guy seems to have done it with the script command.

Under /var/log (or System>Administration>Log File Viewer) you have a variety of log files (none specific from the terminal) that record the system's activities.

---

### Post by philinux on 2009-10-26
<snip>

misread post.

---

### Post by alphaniner on 2009-10-26
ikisham said 'the output of the terminal does not get logged'.  */home/username/.bash_history* contains input.  I think what the OP wants to log is STDOUT & STDERR.

---

### Post by petrockthief on 2009-10-26
> **rockstarrem said:**
> Can I ask why your using Kubuntu 6.06?

Because I live in a black hole. I just might switch to Ubunto Studio ([http://www.ubuntustudio.org]("http://www.ubuntustudio.org")'s the word if you haven't heard). This looks promising and needs more support.

---

### Post by Barriehie on 2009-10-31
To log STDOUT from the CLI:
```

*command* 1>somefilename

```

To log STDERR from the CLI:
```

*command* 2>somefilename

```

To log both STDOUT and STDERR concurrently:
```

*command* 1>somefilename 2>somefilename

```

Barrie

---

