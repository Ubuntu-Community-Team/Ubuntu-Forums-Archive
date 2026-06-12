---
title: "Script file"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by spirited on 2011-05-12
I am trying to write a script file for job queuing for a program called FEKO, from what I gather ubunutu has a pbs batch manager that could be do the job, would anyone shed some light on how to go about doing it coz I am totally green at it .
 
Thanks:P

---

### Post by seawolf167 on 2011-05-13
If you mean bash scripting, start by [reading here ]("http://mywiki.wooledge.org/BashGuide")for a good how-to.

Once you have your script written and tested, you can add an entry in *crontab* to automatically run your script when you want it too.

---

