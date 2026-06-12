---
title: "I think I need a graphics driver"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by trus-rod on 2009-01-12
I just intalled Ubuntu Studio on a laptop.  Installation seemed to go fine.  I rebooted, and at log in I get a black screen with text.  Put in name and password, then just more text, the no warrenty info, where to go for help, etc. and the command prompt at the end just like terminal, but its the whole screen, like dos.  

Help, I'm stuck.

The laptop is a HP ze4610us

---

### Post by Titan8990 on 2009-01-12
to start graphics from the TTY terminal:


sudo /etc/init.d/gdm start

---

### Post by trus-rod on 2009-01-12
It says command not found

---

### Post by cerealtx on 2009-01-12
try ```
startx
``` to start up the x server

---

### Post by trus-rod on 2009-01-12
Well I tried it, it told me to install it.  So I did that, it ran through the process.  Tried startx again.  Now it says line 139: xauth: command not found  abunch of times with different line numbers.  then no such directory of file.  I rebooted and tried again, same thing.

---

### Post by oldos2er on 2009-01-12
Can you please post the output from this command: 

 uname -a

---

### Post by trus-rod on 2009-01-14
Linux shop 2.6.24-19rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

---

### Post by Michael.Godawski on 2009-01-14
hi,

might be some graphic compatibility issue. 
What is your graphic card?
Have you tried out the Ubuntu Live CD on your laptop to see if Ubuntu works in the first place? There is no live cd version of the studio isn't it... I have not found one.

---

### Post by Titan8990 on 2009-01-14
Can anyone verify this: Linux shop 2.6.24-19rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux as actually being a Ubuntu kernel?

---

### Post by trus-rod on 2009-01-14
Uh, not sure what the specs are.
I had the Emc2 version installed, it worked fine, but couldn't install Ardour.

I started going through the trouble shooting guide on Psychocats page, and seem to making some progress.  Its been installing ubuntu-desktop for about 10 minutes now.

---

### Post by Titan8990 on 2009-01-14
Ubuntu-desktop should have been installed by default. Did you do a minimal install or server version?

---

### Post by trus-rod on 2009-01-14
I don't remember seeing an option, Install did seem awfully fast.

---

### Post by Titan8990 on 2009-01-14
I suggest starting over, with the correct disc found here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by oldos2er on 2009-01-14
> **Titan8990 said:**
> Can anyone verify this: Linux shop 2.6.24-19rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux as actually being a Ubuntu kernel?

 Yes, it's the realtime kernel used by Ubuntu Studio.

---

