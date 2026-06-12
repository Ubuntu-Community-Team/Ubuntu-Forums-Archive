---
title: "Making Firefox 3.5 default web browser"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by servicetech on 2009-07-23
What goes in the custom command line under preferred applications to make 3.5 default?

---

### Post by kukibird1 on 2009-07-23
> **servicetech said:**
> What goes in the custom command line under preferred applications to make 3.5 default?

The path to wherever  firefox is installed. I have firefox in /opt  so it is /opt/firefox/firefox .

---

### Post by llamabr on 2009-07-23
The code name is 'shiretoko', which I believe sets up an alias, so you can run them both at the same time.  I havn't installed it, but try that.  If not, set up the alias yourself.

---

### Post by scrooge_74 on 2009-07-23
That works I tried a couple of weeks ago. Just go check where it got installed so you can tell the system

---

### Post by llamabr on 2009-07-24
> **scrooge_74 said:**
> That works I tried a couple of weeks ago. Just go check where it got installed so you can tell the system

Even I don't understand that advice.  Did this solve your problem?

---

### Post by ftabor on 2009-07-24
> **servicetech said:**
> What goes in the custom command line under preferred applications to make 3.5 default?

firefox-3.5 %s

---

### Post by scrooge_74 on 2009-07-24
> **llamabr said:**
> Even I don't understand that advice.  Did this solve your problem?

lol

you need to find where it got installed, you can look for it in /usr and track if down. You can look in synaptic in the detail for the package it will tell you which files got installed and where. 

Then you just need to change your System>prefer apps and put that path in the detail for your prefer browser

---

### Post by servicetech on 2009-07-24
> **ftabor said:**
> firefox-3.5 %s

Solved, thanks :)

---

### Post by scrooge_74 on 2009-07-24
Click on the solved button ;)

---

### Post by colau on 2009-08-15
> **servicetech said:**
> Solved, thanks :)
Cheers.

---

