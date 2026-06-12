---
title: "SSH into an existing session"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by mhouston100 on 2008-03-11
Hey guys, i'm sure this will be an easy solution that i'm overlooking but here goes:

I SSH into my machines at home from work and sometimes do some video encoding which takes forever, what I would like to do is log into one of the existing console sessions (e.g the ones you normally access by ctr - alt - f1 etc) from work so that when I get home I can just switch to that session and continue working.  I've been reading around and heard mention of a program called "screen" that allows something similar to this.  Any suggestions, perhaps something simpler that i'm missing? 

As we have windows machines at work i'm using putty, and occasionally tunnel VNC sessions through it... is there maybe a putty option that allows me to connect to an existing session?

Thanks!

---

### Post by kevdog on 2008-03-11
screen is the only method I am aware of -- it basically allows you to save sessions -- Im not sure if it allows to exist into a currently running session however.

---

### Post by mhouston100 on 2008-03-11
Ok thans for the reply, I might have a bit more of a read up on screen.  

Basically, the picture i'm getting is that you:

 start a SSH session
 run screen
do what needs to be done
 exit screen saving the session
 end the SSH session

When I get home I then:
Start a terminal session or switch console
start screen
load the saved session
continue working

If this is correct I think that should suffice.  One question though - If i'm, say, converting a video file with tovid (approx 2 hrs) and need to save and close the 'screen' session, how would I put tovid in the background so i can enter the commands to save the session and ext?

---

### Post by gardara on 2008-03-14
> **mhouston100 said:**
> 
If this is correct I think that should suffice.  One question though - If i'm, say, converting a video file with tovid (approx 2 hrs) and need to save and close the 'screen' session, how would I put tovid in the background so i can enter the commands to save the session and ext?

You can just close putty or whatever you use, you don't necessary have to close screen, when you exit your ssh program, screen will continue running :)

---

