---
title: "netstat listing options?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by noob_ on 2009-01-12
Hello there!

My actual question is whether there is a netstat option (netstat --something) that gives me the netstat output bit by bit. I have more services running than my screen can display. Netstat's manpage didn't give me a satisfactory answer. Perhaps combining netstat with another command by using "&&" or "|" helps....but how?

I'm looking for a listing of the services similar to what you get when you use "dir /p" in MS-DOS.

____
Why do I want to know this?
*hoping that some Linux-Genius reads this post and is willing to be my tutor*

I really want to know how Linux works for years, but I was too lazy to read and too busy for trial&error-work in the past. But things have changed and now I'm not lazy anymore and not as busy as before.

I've read tons of howtos, tutorials and so on, but I couldn't find a suitable starting-point for me (=I was like "WHAT?!") until I found this one here:
[http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/index.html](http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/index.html)

I'm aware that this howto is sort of outdated, but it really suits to my pre-knowledge or at least I think it does, so I digged up an old machine out of my basement and installed the latest version of Ubuntu Server Edition. Maybe the howto doesn't suit to Ubuntu Server Edition at all, but I guess finding out if it does or not is a good way to learn...

Why Ubuntu Server Edition?

I found out that GUIs are rather hindering/confusing than useful if you try to get deep into Linux.
Also, I'm more or less familar with the Desktop Edition since Feisty Fawn. That's why I want to stick to Ubuntu. I started using it because Vista didn't want my old hardware when I got a new notebook a couple of years ago and half of the web said that Linux works with old hardware and Ubuntu is the beginner's choice.

Soon I noticed that watching videos on youtube and other things require some configuration. I managed to make everything work by reading through different forums and had my first experiences in the terminal/shell/bash (I'm not sure if I know the difference between them).

Long story short: I want to know more about Linux and I think that Ubuntu and (network) security is a good starting point for me.

I use out of convenience Vista for everyday-stuff even if a tuned up Ubuntu is installed as well. But right next to my Vista/Ubuntu Desktop Edition notebook is my little Ubuntu Server machine, waiting to be competently used by me.
I even set myself a goal to make sure I can be proud of myself when I reach it.

So if there is anyone here who wants to guide me and give me quick answers to stupid questions like the one above, please let me know.

Thanks!

---

### Post by cb34 on 2009-01-12
umm.. im no expert but you can use

netstat -atu |more
or
netstat -atu |less (press q to get out of it)

-atu
a=all
t=tcp
u=udp

the | sign (pipe sign)

will pipe netstat's output to the input of the more program(or less).

also netstat -atun

do it with n and without, and you'll see what it does. :) (shows port number or service name)

you can also send the output of netstat to a file for review like this:

netstat -atu >tempfile.txt

it will create tempfile.txt in the current working directory.

just some examples for you. :)
peace.

---

### Post by noob_ on 2009-01-12
i guess you just told me some basic things, but they are incredibly useful!

thank you!

:guitar:

---

### Post by cb34 on 2009-01-12
no problem.. the first thing i do on a new install is run netstat and hunt down and shut down any services i dont want running. :)

---

