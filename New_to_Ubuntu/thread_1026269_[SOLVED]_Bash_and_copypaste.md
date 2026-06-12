---
title: "[SOLVED] Bash and copy/paste"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Cl0cKw0rK on 2008-12-30
is there any way to add copy paste ability to bash on ubuntu server?

---

### Post by eBoxNet on 2008-12-30
are you talking about pasting text inside the terminal window?
if yes then right click and click paste.
of course u can do that only if you have gui installed.

---

### Post by MyR on 2008-12-30
> **Cl0cKw0rK said:**
> is there any way to add copy paste ability to bash on ubuntu server?

I have not used ubuntu server, however I might ask if ctrl+shift+c and ctrl+shift+v will work for copy and paste.

peace

---

### Post by Cl0cKw0rK on 2008-12-30
no that doesn't work. i have no GUI (Ubuntu server doesn't come with one, and i have no need to install it). thus i have no mouse. also, i can't highlight, so the normal ctrl+shift method is out as well. any other suggestions.

---

### Post by MyR on 2008-12-31
There has to be *some* way. I switched to a shell and noticed that ctrl + various keys does some interesting things not unlike from within vi, which I am not very familiar with.

Edit: I see that ctrl+u is cut for the current line and ctrl+y pastes it

---

### Post by eBoxNet on 2008-12-31
are you connecting from another machine?you can connect by sftp

places -> connect to server -> ssh 
give your usr name and pass and connect.

that way you have a "gui" for your ssh connection

---

### Post by Cl0cKw0rK on 2008-12-31
I realize that bit, im ssh'd into it right now. I'm just curious if I can enable it in the shell, so that i can do it directly.

---

### Post by eBoxNet on 2008-12-31
enable what?
:confused:

---

### Post by DGortze380 on 2008-12-31
I'm sure there's a way to do it in your favorite editor, as for in a bash shell...

ctrl+shift+c     -    copy
ctrl+shift+v     -    paste

Only problem is getting text to highlight. Not sure how to do that.

You can however press the up arrow to review previous commands, that's typically sufficient for me anyways.

---

### Post by Cl0cKw0rK on 2008-12-31
Yeah, it usually deos for me too. I was just hoping it was possible. Who knows about highlighting. thanks anyway.

Are you sure about the ctrl+shift thing, it seems to do something like skip the command on the shell

---

### Post by eBoxNet on 2008-12-31
can you pls tell us exactly what you wanna do?
what and where you need to copy and paste?
tnx

---

### Post by ushimitsudoki on 2008-12-31
I have mouse in terminal using [gpm]("http://en.wikipedia.org/wiki/GPM_(software)").

I just tested cut-n-paste from one terminal to another.

I highlighted the text (a couple of lines from cat output) in tty0. No action is required to "copy" - it's automagic.

I opened up nano in tty1 and right-clicked to paste it.

This is right at boot with no GUI being loaded. (It's in Gentoo, not Ubuntu, but I don't see how that would matter.)

---

### Post by cariboo on 2008-12-31
I'm not exactly sure what it is that you are trying to do, but I copy and paste all time in a terminal when I ssh in to my server. See screenshot.

Jim

---

### Post by handydan918 on 2008-12-31
> **cariboo907 said:**
> I'm not exactly sure what it is that you are trying to do, but I copy and paste all time in a terminal when I ssh in to my server. See screenshot.

Jim
Yeah we get that. You are, however, running X on the local host.

---

### Post by Cl0cKw0rK on 2008-12-31
i just want to be able to copy paste text in the bash shell. thanks for the gpm tip. now i have a mouse and i can highlight. Also i can cut and paste. thanks for the help.

---

### Post by decoherence on 2008-12-31
glad you found your solution! :D

you can thank ushimitsudoki by clicking the little medal icon in the lower right of his helpful post. i'm sure it'd be appreciated.

see you around the forum! :o

---

