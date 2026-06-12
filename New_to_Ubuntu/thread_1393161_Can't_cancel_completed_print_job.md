---
title: "Can't cancel completed print job"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by japhyr on 2010-01-29
Hello,

I printed a one-page document this morning, and the document printed successfully.  But the printer icon has stayed on my top panel all day, and it says the job is still processing.  I have tried Job>>Cancel, but nothing changes.  The printer is attached to a different computer than this one.  I am running 9.04 on this computer.

Is there anything I can do to make this job disappear?

---

### Post by tom4everitt on 2010-01-29
There are two terminal commands you can try (you will find the terminal under applications->accessories->terminal):

cancel

should cancel all jobs being processed at the moment (even one sent to another computers printer). If that doesn't work you can try:

sudo killall lpr

which should kill all printing processes by force :)

---

### Post by japhyr on 2010-01-29
Cancel does not seem to have any effect, and "sudo killall lpr" says "lpr: no process killed".  Any other ideas?

---

### Post by japhyr on 2010-01-30
The only way I could figure out how to get rid of the print job was to restart the computer.

---

### Post by tom4everitt on 2010-02-01
Hmm, too bad. Chances are good the problem will be solved when you upgrade to the latest ubuntu...

---

