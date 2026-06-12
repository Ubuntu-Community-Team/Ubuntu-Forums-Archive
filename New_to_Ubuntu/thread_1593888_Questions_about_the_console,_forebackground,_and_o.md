---
title: "Questions about the console, fore/background, and other stuff"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by Amablue on 2010-10-11
I think I'm misunderstanding how this all works. When I start a program from a console, the program is linked to that console, so that if I close the window the program dies with it. If I use $ someprogram & it starts in the background, so I can continue doing other things while it runs, but it will still die when I close the window right? And I can't pull it back into the foreground from another terminal right? Is there a way to just get it to run and stay running independently from the console?

The reason I ask is because I was trying to start a torrent from my phone earlier. I have an android phone with connectbot, so I ssh'd into my home computer, started up ctorrent, but I think when I disconnected ctorrent died. What I want to do is kick off a program (not necessarily ctorrent) and just have it run so I can pick it up when I get home. I can't find any way stop a process in one console and start it up in another.

---

### Post by WRDN on 2010-10-11
Take a look at "screen", an invaluable command line tool. It is a screen manager, as the name suggests, and performs "terminal emulation".
You can detatch from a screen, come back later (even after logging off and on again), and reattach to the screen.

If you run a program in the background, using &, it will not close when the console window closes. In the console, you can bring a background window to the foreground using the "fg" command.
Despite this, I have always found screen more useful - this is especially true if you want to run a time consuming task on a server. 

You could SSH into the server, start the task in screen, detatch, quit SSH, then SSH back in later, reattach and check the status of the task!


screen is installed by default on Ubuntu installations. To use it in the Terminal:

Type:
```
screen
```

Start the task, it doesn't matter if its a background or foreground task. Typically though, screen it used for foreground tasks. e.g. torrent client.

```
gedit
```

Now detatch the screen, by pressing Ctrl + A then Ctrl + D.

You can now close the window, and the task will continue running.

To get back to the screen, type:

```
screen -r
```

If you have more than 1 screen running, you will be provided with a list of available screens. If there is only 1 running, it will automatically reattach to that.
If there is more than 1 screen, the screen ID will be listed, along with the date it was created and the status of it ("Detached").
An example is:

> 3029.pts-0.ubuntu (10/12/2010 01:26:09 AM) (Detached)

To reattach to a particular screen, just type:

```
screen -r 3029
```

Hope this helped.

WRDN.

---

### Post by Amablue on 2010-10-11
Thanks for the tip about screen, it looks like exactly what I need

> If you run a program in the background, using &, it will not close when the console window closes. In the console, you can bring a background window to the foreground using the "fg" command.
Despite this, I have always found screen more useful - this is especially true if you want to run a time consuming task on a server. 

Are you talking about with or without screen here? When I run "gedit &" and then close the console window, gedit closes too.

Something else odd I noticed while looking for information is that neither fg or bg have man pages on my computer. Is this normal?

---

### Post by WRDN on 2010-10-11
> **Amablue said:**
> Thanks for the tip about screen, it looks like exactly what I need



Are you talking about with or without screen here? When I run "gedit &" and then close the console window, gedit closes too.

Something else odd I noticed while looking for information is that neither fg or bg have man pages on my computer. Is this normal?

Sorry, that was a mistake on my part.
Running any command in the base console (without screen), then closing the console will close the program.
With screen, providing you detatch the screen before closing the console, the program will continue running.

Regarding the man pages, that is rather odd, most man pages are available online though. See '[man fg]("http://linux.die.net/man/1/fg")' and '[man bg]("http://linux.die.net/man/1/bg")'.

---

### Post by wkhasintha on 2010-10-11
I was looking for something like this.. Thanx WRDN.

---

### Post by llamakc on 2010-10-11
> **Amablue said:**
> Thanks for the tip about screen, it looks like exactly what I need



Are you talking about with or without screen here? When I run "gedit &" and then close the console window, gedit closes too.

Something else odd I noticed while looking for information is that neither fg or bg have man pages on my computer. Is this normal?

```

man builtins

```

It is one of BASH's built-in commands.

---

