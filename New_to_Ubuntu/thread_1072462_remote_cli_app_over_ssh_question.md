---
title: "remote cli app over ssh question"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by mishkin on 2009-02-17
When you run a program like irssi in terminal over ssh on a server

when you close the terminal does the program remain running on the server?

if it does how do you connect to the program to see it's cli output again??

especially if say your running 2 or 3 cli programs in this manor??

Since I don't know, I run my cli programs in xfce4 over vnc (visual terminal boxes I can minimmize)

(my server is debian but my home comps are ubuntu)

---

### Post by DGortze380 on 2009-02-17
> **mishkin said:**
> When you run a program like irssi in terminal over ssh on a server

when you close the terminal does the program remain running on the server?

if it does how do you connect to the program to see it's cli output again??

especially if say your running 2 or 3 cli programs in this manor??

Since I don't know, I run my cli programs in xfce4 over vnc (visual terminal boxes I can minimmize)

(my server is debian but my home comps are ubuntu)

Best answer is maybe...

it depends on the program, but most of the time I would bet it keeps running.

---

### Post by skintythe1andonly on 2009-02-17
Im by no means an expert but have jsut started using screen to run multiple cli apps and it lets me log out of the session. Have a look at 
[http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/")

---

### Post by mikewu on 2009-02-17
Closing the connection does infact close the processes associated with the shell. Screen would be my choice. When you want to close the session, you detach screen with ^a^d. Programs will continue to run. When you connect again, you can reattach the screen screen with a screen -r.

---

### Post by DGortze380 on 2009-02-17
> **mikewu said:**
> Closing the connection does infact close the processes associated with the shell. Screen would be my choice. When you want to close the session, you detach screen with ^a^d. Programs will continue to run. When you connect again, you can reattach the screen screen with a screen -r.

not always. I regularly use wget over ssh and close the connection, the process continues. It depends on the process.

---

### Post by uberg on 2009-02-17
Yes, but screen will definitely keep the process running as this is part of the design of screen.

---

### Post by mishkin on 2009-02-17
how exactly does screen command work

do you have to do it when you first start the program? or can you do it after?

maybe an example of how that would go with irssi

because I hear people say they run torrentservers over ssh and have no gui and I didn't get how they were getting back to their torrent client screen when they log back on.

---

### Post by uberg on 2009-02-17
You have to run screen first.  From a terminal command line.  You may have to install it.  I have to admit that I don't use this program before I go on any further.  I have used it before but found that I don't really need it in my day to day activities.  I did find it to be really cool though and know some of the things it was designed for.

The home page is:
[http://www.gnu.org/software/screen/](http://www.gnu.org/software/screen/)

To quote the first line from the introduction: "Screen is a full-screen window manager that multiplexes a physical terminal between several processes, typically interactive shells."  What this means is from gnome-terminal you can run screen which presents you with a terminal from which you can now open many instances of a terminal session.  As i said i don't use this program much but i hope that gives you and idea.  It actually does a lot more but i am being simplistic.  One of the neat things, as mikewu pointed out, is that screen lets you "detach" (^a^d) this session.  It's like you log out of this session but you are not really logging out of this session.  Which means your program continues to run as if you were still connected to that session.  At a later time you can invoke screen again and reconnect to that session.

Most programs you run from a terminal session terminate when you logout of that terminal session.  Screen lets you "detach" that session without logging out.

I am afraid i made a hash out of this explination.  I am sorry.  But please give it a try.  I really think that this is what you are looking for.  I am also inspired to relook at this piece of software again because it is capable of so many other things too.

---

### Post by skintythe1andonly on 2009-02-18
I am using screen for exactly this purpose. I am running rtorrent at home on a old desktop with no monitor. It is just connected to my router. When I want to start rtorrent, I ssh into this desktop and i start rtorrent with the screen command first

```
screen rtorrent
```

when i want to detach this from my cureent session i use ^a^d and I get detached. I can logout then from this ssh session.

When i log back in and want to check how rtorrent is doing I simply go

```
screen -r
```

That is as far as im using it at the moment but it can be used to run a lot more. I dont use irssi but found this

[http://quadpoint.org/articles/irssi]("http://quadpoint.org/articles/irssi")

---

### Post by uberg on 2009-02-18
Just found this great article from IBM developer works:
**[COLOR=#999999]Speaking UNIX: [/COLOR]Stayin' alive with Screen**

[http://www.ibm.com/developerworks/aix/library/au-gnu_screen/index.html](http://www.ibm.com/developerworks/aix/library/au-gnu_screen/index.html)

---

