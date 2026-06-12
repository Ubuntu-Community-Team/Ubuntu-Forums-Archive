---
title: "Screen Command Detatches But Process Still Fails"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by age99 on 2009-11-23
Hi, 
I'm running some big processes remotely through ssh (putty).  The processes will take longer than 1 day to run, but the problem is that the connection times out every now and then and the process stops.  

I've been using the "screen" command and then detaching once the process is started however the process still stops once the connection is lost or the window is closed.

```
screen *command*
Ctrl-a d

```

The detach seems to have worked fine, but once I close the putty session, or the connection is lost, the process still stops.

Any idea why this is happening?

Thanks

---

### Post by lorsen on 2010-01-13
Have you tried to reattach right after detaching. Just to see if it works in that case.

---

### Post by fromthehill on 2010-01-13
I've experienced this on several windows ssh-clients
the screen got killed after I closed putty

I can't reproduce this error
for some reason the now does screen keeps running after I exit putty
it could be because I have the same user logged in locally so it is never completely logged out

---

