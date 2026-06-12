---
title: "Killing Processes"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by okayneil on 2009-07-08
Hey guys, as an experiment I killed a few processes to see if they reduced CPU load, with the thinking that once i do a reboot they would all auto start again, well they didnt. 

Does ubuntu have restore points or is there a away to get all the "normal" running processes back?

Cheers!

---

### Post by Sub101 on 2009-07-08
Unfortunately there are no "restore points" like with Windows.

Do you know what processes you stopped?

And how did you stop them? I am surprised they have not restarted after a reboot.

---

### Post by okayneil on 2009-07-08
> **Sub101 said:**
> Unfortunately there are no "restore points" like with Windows.

Do you know what processes you stopped?

And how did you stop them? I am surprised they have not restarted after a reboot.

No idea what ones I killed, damm with the restore point. I "killed" the processes. :(

---

### Post by kandieyman on 2009-07-08
If you do not know which ones you killed, then how do you know that they did not run on startup. All processes are killed on shutdown, so you did not do anything permanent. Killing a process is always for that session only.

---

### Post by binbash on 2009-07-09
Yup , it is for that session only.

---

### Post by LookTJ on 2009-07-09
If you killed them using the killall(or etc) command, it is only for that session. Not all processes auto-restart.

---

### Post by indytim on 2009-07-09
Re-boot!

---

### Post by okayneil on 2009-07-09
> **indytim said:**
> Re-boot!

Thas exactly what i did, for example, I cant shut the computer down via the drop down menu in the top right corner, its gone. Tomboy notes are gone, they used to come on startup :(

---

### Post by random turnip on 2009-07-09
0.0
I now know not to do this.

What i would do:
Back everything up on an external disk, re-instal ubuntu...

If not, go System --> Admin (i think) --> Start up programs
Find the list of start up programs in there, post a screen shot or type them in here and hopefully someone will know what you have missing and how to get them back.
If not, sounds like a re-instal case.

---

### Post by niteshifter on 2009-07-09
Hi,

Sounds like he really killed vs. asking a process to end (SIGKILL vs SIGTERM) - although SIGTERM is only slightly "safer". It depends on the process (program).

I just went on about this in [this thread]("http://ubuntuforums.org/showthread.php?t=1208187") (post #6).

Anyways, let's find out what you did and what you did it to. If you were working in a terminal and using the command 'kill' or 'killall', then the below will be helpful. In a terminal:
```
history | grep kill
```
and post the output here. It'll give us some clues. If you did the kill-off via System Monitor or some other GUI tool then there won't be a history to work from.

---

### Post by okayneil on 2009-07-09
> **niteshifter said:**
> Hi,

Sounds like he really killed vs. asking a process to end (SIGKILL vs SIGTERM) - although SIGTERM is only slightly "safer". It depends on the process (program).

I just went on about this in [this thread]("http://ubuntuforums.org/showthread.php?t=1208187") (post #6).

Anyways, let's find out what you did and what you did it to. If you were working in a terminal and using the command 'kill' or 'killall', then the below will be helpful. In a terminal:
```
history | grep kill
```and post the output here. It'll give us some clues. If you did the kill-off via System Monitor or some other GUI tool then there won't be a history to work from.

I did the kill via gui, system monitor to be exact, p.s im no reinstalling, thats crap advice, no offence, reinstalling is not always the solution.

---

### Post by 3rdalbum on 2009-07-09
If you remove applets from the panel, they don't come back automatically, you have to re-add them.

If you removed programs like Tomboy from the Startup Applications, all you have to do is re-check the box in System > Preferences > Startup Applications and they will come back on your next login.

---

### Post by kandieyman on 2009-07-09
I agree. The fact that you have missing applets from the panel is of no concern. Right click and add the applet back. You will very unlikely need to reinstall (but you can if it will make you feel more comfortable).

---

