---
title: "Reconnect to SSH where I left off?"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by P-J on 2007-07-09
Hi there!

I run ubuntu-server on an old machine at home, and SSH to it using 'putty' on my Windows machine at work. I don't claim to know too much about SSH so forgive me :)

But I wondered, is it possible to close putty and then reconnect to the session at a later time (and carry on where I left off)?

Or do I need a different client or some configuration on the server? Any help much appreciated :)

---

### Post by EndPerform on 2007-07-09
What you can do is use screen.  Basically, after you SSH into your machine, run screen.  It'll present you with a prompt just like before, but the difference is that you can disconnect from it.  So say you're working on something and need to log out.  When in screen, you'd type CTRL-A then press D to disconnect.  When you SSH back into the machine, you'd type screen -r to reconnect.  So, in review:

SSH into your machine and type:
```
screen
```
to start your screen session.

When you're ready to disconnect from your session:
```
CTRL-A D
```
to disconnect from the screen session, then log out of your SSH session

When you're ready to reconnect, login via SSH and type:
```
screen -r
```
to reconnect.  Hope this helps.

---

### Post by kevdog on 2007-07-09
What if you just type "exit" while within screen.  This seems to exit the program for me, but does it save the commands?

---

### Post by netztier on 2007-07-09
> **P-J said:**
> Hi there!

I run ubuntu-server on an old machine at home, and SSH to it using 'putty' on my Windows machine at work. I don't claim to know too much about SSH so forgive me :)

But I wondered, is it possible to close putty and then reconnect to the session at a later time (and carry on where I left off)?

Or do I need a different client or some configuration on the server? Any help much appreciated :)

The answer is Yes and no. 

The No-Part: Once an SSH tunnel goes down, it is down. Period - the shell you had opened when logging in will be closed.

The Yes-Part: You might want to look at the tool **screen** (package has the same name) which offers a wealth of functionality, amongst which:

[LIST]
[*]create **multiple** virtual terminals (Ctrl+a c) to switch between with **Ctrl+a 0** to **Ctrl-a 9** (or more), just like you can have multiple consoles when using screen and keyboard at the machine and switch between them with Alt+F1 to Alt+F6.
[*]disconnect from screen with **Ctrl+a d** and log off. The programs you had running in the virtual terminal(s) continue to work as if you were still logged in.
[*]reconnect to screen with **screen -r** once you have your SSH tunnel back or you're sitting at the machine's console or established some other form of interactive login (telnet, rsh..) with the machine.
[/LIST]
... to list only a few - the ones I juse mostly. Screen comes in very handy when running an IRC client from home for instance, or multi-hour update jobs or other command-line applications that for some reason can't be run as daemons or can't be cron-jobbed. When I still ran gentoo on my machines, I would start the emerge processes in one screen terminal, top in a second one, then disconnect from the session, go to work, SSH into the machine and then re-attach to screen to see how it ran. 

The **man screen** command  - although the manpage is around 3400 lines - is probably your best friend once you have screen it installed ;-)

best regards

Marc

---

### Post by netztier on 2007-07-09
> **kevdog said:**
> What if you just type "exit" while within screen.  This seems to exit the program for me, but does it save the commands?

This will close whatever virtual terminal you were working on within screen - if it's the only one, it will exit screen and drop you back to the terminal you had logged in from. You should be able to spot that from the "[screen is terminating]" message:

```
marc@torch:~$
marc@torch:~$screen
[COLOR="Gray"]      marc@torch:~$
      marc@torch:~$
      marc@torch:~$ exit
[/COLOR]**[screen is terminating]**
marc@torch~$

```

If you had opened multiple virtual terminals within screenl, you just get dropped back to another one (I'm not sure if it is the lowest numbered one, the one you were in before or the next lower numbered).

best regards

Marc

---

### Post by P-J on 2007-07-09
Blimey! Loads of answers all at one :)

Thanks for all the suggestions :) Netzier : Running an application that can't be run as a daemon/cron job is exactly what I need to do. It's an X-serverless box so I need it to keep running while I'm not connected.

Thanks all, I'll check it out!

//edit : EndPerform & NetZier - Thanks for the advice. Have installed screen and it does exactly what I'm after. Thanks a million!

---

