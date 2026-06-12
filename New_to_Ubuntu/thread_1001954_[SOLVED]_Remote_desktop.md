---
title: "[SOLVED] Remote desktop"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Malalo on 2008-12-04
Hello all !

I'm actually connecting to specific applications on another server through SSH, with this command line, for example the account manager (the server is running Tru64) :

**ssh -X -Y root@theserver /usr/bin/X11/dxaccounts**

This, although a little slow, works fine.

However, I would like to know if the complete desktop (not just an application) could be sent through SSH (or by any other means) ?

Thanks for your help.
Ubuntu 8.10

---

### Post by jbrown96 on 2008-12-04
You will need to setup a VNC server. TightVNC is open source and uses the same encryption as SSH by default. Ubuntu has a VNC client that will be able to connect. 
Or, you can tunnel VNC through SSH. I'm not sure how to do it, but there are lots of guides, just search for it.

---

### Post by Malalo on 2008-12-04
I probably should've mentionned :
The goal is to find a solution that will not need to install anything on the server, as it contains specific financial software and we are not allowed to change its configuration...
Let me explain my needs more clearly :
I'm accessing different apps through SSH (as stated above), I would like to have the complete desktop in one command, so I wont have to create a new SSH command for each app I need to access...

The last option I was thinking of, was to create a script which would ask which app I'm connecting to, then it would change the command line appropriately...

But still, I would prefer to have the desktop, again without the need for VNC...

---

### Post by scorp123 on 2008-12-04
> **Malalo said:**
> However, I would like to know if the complete desktop (not just an application) could be sent through SSH  Yes ... but it's risky. If for any reason the SSH connection drops your entire GUI session will die and so will the programs that you were running. The result would be an unclean shutdown and crash of these programs ... which might be a very bad thing.

Imagine you're running the desktop remotely and you're inside one really critical application .... and for some stupid reason the SSH connection dies. Then what? Are you 100% sure your UNIX admins are not going to kill you in very unpleasant ways if they find out it was you who caused this hickup?

Also ... I'd assume if your admins would have wanted you to execute the desktop remotely they would have given you the information already? Are you even sure that the desktop programs are installed? Because it is a server and probably professional equipment ("Tru64" isn't exactly something you'd see home users working with ...) chances are the GUI environment isn't even installed ...

If you want to be on the safe side I'd suggest you talk to your admins. Tell them that you'd like to have a GUI and if they are OK if you tunnel that through your SSH connection ... they might even help you to set it up properly from your box ...

---

### Post by bodhi.zazen on 2008-12-04
> **scorp123 said:**
> Yes ... but it's risky. If for any reason the SSH connection drops your entire GUI session will die and so will the programs that you were running. The result would be an unclean shutdown and crash of these programs ... which might be a very bad thing.

Imagine you're running the desktop remotely and you're inside one really critical application .... and for some stupid reason the SSH connection dies. Then what? Are you 100% sure your UNIX admins are not going to kill you in very unpleasant ways if they find out it was you who caused this hickup?

Also ... I'd assume if your admins would have wanted you to execute the desktop remotely they would have given you the information already? Are you even sure that the desktop programs are installed? Because it is a server and probably professional equipment ("Tru64" isn't exactly something you'd see home users working with ...) chances are the GUI environment isn't even installed ...

If you want to be on the safe side I'd suggest you talk to your admins. Tell them that you'd like to have a GUI and if they are OK if you tunnel that through your SSH connection ... they might even help you to set it up properly from your box ...

You can forward an entire desktop over SSH.

If you are running apps over ssh, use screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

	[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)

:lolflag:

---

### Post by scorp123 on 2008-12-05
> **bodhi.zazen said:**
> If you are running apps over ssh, use screen Chances are "screen" isn't installed on **Tru64 UNIX** ;)  And OP already said he can't install any additional programs. ):P

---

### Post by Malalo on 2008-12-05
> **scorp123 said:**
> ... chances are the GUI environment isn't even installed ...


Yes it is, since I'm already able to get GUI apps as "dxaccounts" through SSH. I've been on the console, and there is a GUI desktop. Other admins here (might not look like it, but I am an admin, in Windows... slowly transitioning to Linux) have access to the Tru64 console using the Hummingbird eXceed program. I'd simply like to have the same as they do but in my Ubuntu environment...
If "screen" needs some type of installation on the server, then I can't...

I think I'll just stick to creating a script asking which app I want to access, thus changing the ssh command.

Thank you ever so much for your input !

---

### Post by scorp123 on 2008-12-05
> **Malalo said:**
> Yes it is, since I'm already able to get GUI apps as "dxaccounts" through SSH. I've been on the console, and there is a GUI desktop. You might try this then:  Get a connection via: ```
ssh -X youruser@yourserver
``` Once you're in you can try to launch the CDE (is it CDE? I haven't used Tru64 in ages!) via this: ```
xstart
``` (Linux uses "startx" .... but I doubt that this would work?)

---

### Post by scorp123 on 2008-12-05
Hmmm ... you could also try one of these: ```
dtlogin
dtsession
``` At least on Solaris this seems to work; as Tru64 has CDE too this might also work there.

---

