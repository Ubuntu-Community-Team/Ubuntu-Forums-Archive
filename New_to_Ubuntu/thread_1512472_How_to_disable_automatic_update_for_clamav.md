---
title: "How to disable automatic update for clamav"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-18
I would like to update the virus definitions manually,so can anyone tell me the way to disable the automatic update for clamav..?I am using ubuntu 10.04..Thanks in advance....!

---

### Post by jtarin on 2010-06-18
You will need to run ClamAV Anti-Virus Manager in order to fine-tune the configuration of Auto-Updates and Auto-Scan.

---

### Post by karthick87 on 2010-06-18
> **jtarin said:**
> You will need to run ClamAV Anti-Virus Manager in order to fine-tune the configuration of Auto-Updates and Auto-Scan.

I have installed only CLAMAV,do you want me to install any other thing..?

---

### Post by wojox on 2010-06-18
Here's how you set it up. Try reversing it [Setting up auto-updating]("http://www.clamav.net/doc/latest/html/node24.html")

---

### Post by karthick87 on 2010-06-20
I couldn't find the way,someone there to help....?

---

### Post by jtarin on 2010-06-20
I do not have an anti-virus program on my machine as its not needed or desired with Linux and especially if you have a router connection, but I understand that some people need the security of such software, even in Linux, so I would suggest in this situation you open a terminal and type "man freshclam" and this will give you all the options available, as documented.If you have a GUI you might try going to the the update tab, click cancel and uncheck the boxes.

---

### Post by karthick87 on 2010-06-22
Any one has answer..?

---

### Post by jtarin on 2010-06-22
I as I said...the largest percentage of Linux users do not use anti-virus software, waiting for answer on this forum might be awhile. Your best bet would be the source itself.
[http://www.clamav.net/lang/en/support/](http://www.clamav.net/lang/en/support/)

---

### Post by karthick87 on 2010-06-24
I have done :)

Goto terminal and type the following,

```
sudo gedit /etc/clamav/freshclam.conf
```

Go through the file,and find the following line

> # Check for new database 24 times a day
Checks [COLOR=Red]24[/COLOR]

Change 24 to 0 like this

> # Check for new database 24 times a day
Checks [COLOR=Red]0[/COLOR]


Now the automatic update will be disabled to update manually goto terminal and type

```
sudo freshclam
```

Thats it :) and thanks for all the users who replied..

---

### Post by jtarin on 2010-06-24
Good Work! I knew it could be done if you looked long enough. It's not so much about waiting for answers as it is looking in the right places for answers.

---

### Post by itsols on 2010-07-30
First, your question, then your answer... It's a good discovery. But WHY would you want to turn off the update?

In MY CASE, I have a special reason... I just discovered (through observation) that my OS (10.4) crashes on the GUI and goes into low graphics mode every time the ClamAV updates starts... At least I presume this.

What's YOUR reason?

Thanks for sharing the tip anyway!

---

### Post by itsols on 2010-07-31
I stand corrected...

Despite disabling the automatic update, my GUI crashed today. So this is to inform anyone out there who things the issues are connected that my presumption was wrong.

Anyway, thanks for the tip on disabling the updates.

---

