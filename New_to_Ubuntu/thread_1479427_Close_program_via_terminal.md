---
title: "Close program via terminal?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-05-10
So, I was playing around with the terminal the other day and conky. I recently installed conky via the terminal and started it up via the terminal. It came up and looked nice. But I noticed that there wasn't any window edge to it (minimize, maximize, close, boarders, etc). So I couldn't move it around on my desktop nor could I close it at all. I wanted to close/end conky but couldn't figure out for the life of me how to do it in the terminal.

It isn't that big of a deal, nothing urgent. More curiosity than necesity.

So how do I do it? What command, option, argument do I use to end a program via the terminal?

Thanks in advance.

-Spydey :guitar:

---

### Post by utnubuuser on 2010-05-10
sudo killall conky

---

### Post by spydeyrch on 2010-05-10
> **utnubuuser said:**
> sudo killall conky


So it is not necesary to have elevated privileges (sudo) to start a program yet it is to end a program? Interesting........

What kind of arguments and/or options could I add to the killall command? Could I use the killall command, or perhaps there is just a 'kill' command (???), and maybe a process ID number of some sorts to designate a specific process which I want to end? Just me thinking/questioning outloud. :)

Thanks for your quick response.

Do you know of any other way to end a program via the terminal? I ask because I have found that when dealing with linux (as with most anything), there are usually several different ways, some more complex than others, to get the same thing accomplished.

-Spydey :guitar:

---

### Post by gzarkadas on 2010-05-10
First do a ```
ps -A | grep <app-name>
``` to get the process id (pid) of the program in question; then use ```
kill <pid>
``` to send a SIGTERM to the program.

This will most of the time make the program to terminate. If not, then use ```
kill -s KILL <pid>
``` to send a SIGKILL to the program and end it forcibly.

For very misbehaved GUI apps that don't let you even launch a terminal, type CTRL+ALT+F1 to go to a console login, login as usual and issue the commands above. Then, logout and type CTRL+ALT+F7 to return to the graphical environment.

---

### Post by wojox on 2010-05-10
If you started it from the terminal then Ctrl+c will work.

---

### Post by spydeyrch on 2010-05-10
Wonderful responses. Thank you very much everyone.

I will have to try those new commands.

I will also try the ctrl + c  and see if it works.

Thanks again to everyone.

-Spydey :guitar:

---

### Post by HarrisonNapper on 2010-05-10
> **spydeyrch said:**
> Wonderful responses. Thank you very much everyone.

I will have to try those new commands.

I will also try the ctrl + c  and see if it works.

Thanks again to everyone.

-Spydey :guitar:


Use Ctrl-C only if you started the app using the terminal. Not that there's much harm in doing it otherwise, it just won't help the situation.

---

### Post by m_duck on 2010-05-10
Also, for GUI apps, you can run ***xkill*** from the terminal or run dialog, your mouse pointer will turn into a skull and cross bones, and then you can simply click the app you wish to end. In case you needed *another* alternative...

---

### Post by spydeyrch on 2010-05-10
> **m_duck said:**
> Also, for GUI apps, you can run ***xkill*** from the terminal or run dialog, your mouse pointer will turn into a skull and cross bones, and then you can simply click the app you wish to end. In case you needed *another* alternative...

That actually sounds pretty sweet!!! I will have to try it. I would love to scare my friends that run linux with this and tell them that it is a virus!! What a laugh that would be. Obviously I would tell them that it wasn't really a virus but it sure would be funny for the first few moments.

They are really new to linux, as in 5 days new.  :P

Thanks again.

-Spydey :guitar:

---

### Post by HarrisonNapper on 2010-05-12
@spydey: In that case you should boot to the root shell (recovery mode) and tell them that is what linux actually is and you were showing them Mac OSX before

---

### Post by renegade9x on 2013-02-01
> **m_duck said:**
> Also, for GUI apps, you can run ***xkill*** from the terminal or run dialog, your mouse pointer will turn into a skull and cross bones, and then you can simply click the app you wish to end. In case you needed *another* alternative...

Best response...... Thanks

---

### Post by codemaniac on 2013-02-01
The thread is closed now.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

Thanks!

---

