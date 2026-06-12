---
title: "Started gparted but can't see what's going on - unprompted login"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-08-02
[LIST]
[*]I booted off a Live CD (Ubuntu Jaunty 9.04).
[*]I started a process with gparted - which, obviously, I mustn't interrupt.
[*]This was running fine, so I left it.
[/LIST]
Later, I came back to the computer. The screen was blanked, with a message complaining about a display monitor. It said that display 0 was busy, should it try another number?

I had no idea what it meant, so I said yes.

Ubuntu told me that it chose number 1, and took me to a new login screen.

Now...

[LIST]
[*]When I log in, I briefly (just a flash) see my screen with gparted still running, but then it logs me into a new session.
[*]When I log out, again I briefly (just a flash) see my screen with gparted still running, but then I get the prompt to log in again.
[/LIST]
In other words, it's as if an entirely new session is running on top of my old existing session. I have no clue what made this happen!

How can I end this current session and get back to my old session (which, judging by the busy light on my hard drive, is still running)?

Naturally, I'm concerned about accidentally stopping it from running!

---

### Post by SuaSwe on 2009-08-02
I'm a little bit of a novice but if you do

Ctrl+Alt+F1

you will enter into a command line interface, wherein you can toggle between different sessions via Alt+F1 (that'll be the one you start in), Alt+F2 etc. Not sure if that'll be applicable in this case considering it seems you have somehow set it up to attempt to use a second monitor - maybe the screen saver came on somewhere in the middle? :D - but you might be able to see whether the installer is still running and what stage it's in, and perhaps even fix the problem if you're familiar enough with Terminal (I'm not in this case, I'm afraid!).

You can exit each session of command line mode by typing 'exit' (no quotes, of course).

---

### Post by Paddy Landau on 2009-08-02
You're most likely right that the screensaver came on somewhere in-between, as I was away from the computer for longer than the default 10 minutes. I've disabled the screensaver.

Hmm, I'd thought of Ctrl-Alt-F1 (but Alt-F1 and Alt-F2 are new to me).

I'm worried, though... Doesn't Ctrl-Alt-F1 kill the GUI, which in turn would kill the running gparted process? How can I tell whether I have two GUI's running, so that Ctrl-Alt-F1 would kill only this one and not the other?

Although I do have a full backup, I'd hate to have to go through the entire process of reinstalling and restoring!

For safety sake, I think I'll keep logging off every half-hour or so until that brief flash shows me that gparted has finished; then I'll do what you suggest and see if it would have worked!

Thanks for the advice.

---

### Post by 73ckn797 on 2009-08-02
Have you tried to log out? Don't know if that will help but maybe you could get back in on the prior gparted operation session.

---

### Post by Paddy Landau on 2009-08-02
> **73ckn797 said:**
> Have you tried to log out?
Refer to the first post...
> **Paddy Landau said:**
> 

[LIST]
[*]When I log out, again I briefly (just a flash) see my screen with gparted still running, but then I get the prompt to log in again.
[/LIST]


---

### Post by SuaSwe on 2009-08-02
Ctrl+Alt+F1 won't end anything, everything will keep running as it was (e.g. if I do it now and do a 'top', it'll show me all the programs running in the GUI, and when I do 'exit', it'll go straight back with the GUI just as I left it - basically like a full-screen Terminal session!) but I couldn't swear that it wouldn't disrupt something in your rather particular situation, so perhaps best not to try!

It's there for consideration if need be though. :)

---

### Post by louieb on 2009-08-02
Your x session is likely on tty7 (ctrl+alt+f7)  

pressing ctrl+alt+f1 should not kill your x session 

Try pressing ctrl+alt+f7 wiggle the mouse or something to see if x come back.

if not the go to tty1 (ctrl+alt+f1) and log on.

to see where you are logged on use the  **finger**  command (x session will be tty7 and higher). 

to see if gparted is running and using cpu doing something use the **top **command. or IF you have installed it the **htop** command

---

### Post by Paddy Landau on 2009-08-02
Well, gparted finally finished (phew!).

I tried the Ctrl-Alt-F1 thing, and Alt-F1 and Alt-F2 did indeed seem to swap between two sessions; but they were both text-only.

In Alt-F2, when I typed 'exit', it went back to the GUI (the one that I didn't want).

In Alt-F1, there were some messages that I didn't understand but no prompt.

All I could do was issue the "reboot" command.

So, sadly, I didn't learn how to solve that particular problem, but fortunately gparted had finished without errors!

Thanks for all the advice, people. I'll document what I've learned today -- and disable the screensaver whenever I use the Live CD!

---

