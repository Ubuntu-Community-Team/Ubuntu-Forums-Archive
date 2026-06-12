---
title: "multiple x window sessions over diff. ssh connections"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by redcomet22 on 2008-02-25
This is my first time posting here, so i apologize ahead of time if this is not posted in the right place.

I'm using the latest version of ubuntu 7.10 server with the ubuntu-desktop metapackage installed on top of it. I'm trying to set up a SSH server with octave so that other people as well as myself can run matlab-esque coded simulations, this of course requires an X-window server and client. 

I have already forwarded my DISPLAY variables and I am able to open an X window on the remote machine over SSH, and I do have some vague understanding of how this is happening. At current i'm placing a remote port forward pointing to port 6000 on the server back to my remote machine through putty (on windows). This does work.

My question is this:

When I have more than one user on the server obviously port 6000 on the server machine is either forwarded or in use. Is there any way an additional user could open up a forwarded connection to the x-window client on the server on a higher port e.g. 6001, 6002, etc.? If so, how would I do that, as well as make that a per-user setting, i.e. user A uses display on serverbox:6001, user B on serverbox:6002 etc. Would I need to install and run multiple copies of the xwindow xclient? Oh yeah, and how would I forward the display variable if the x-client (server side) talking to the x-server on the  default port 6000?

If anyone could help with this I'd appreciate it!

---

### Post by kevmitch on 2008-07-05
Wow, I'm sorry no one has replied to this for so long. Hopefully you're still checking. It might be that there aren't many people familar with putty (including myself).

I can however tell you that forwarding X11 windows should not be this painful a process. You should be able to tell your ssh clients to "ForwardX11" and "ForwardX11Trusted" (though these are openssh config directives) and it should take care of all this port stuff for you. That is, you should not have to explicitly specify ports to forward and you should have to worry about multiple sessions conflicting if you have the correct configuration. This should all just be taken care of automatically.

For example, if one of the client machines were also running Linux, you should be able to add the following to your ~/.ssh/config file

```

     ForwardX11     yes
     ForwardX11Trusted   yes    

```

Seeing as how you're running windows, I would recommend giving cygwin a try: [https://turing.phas.ubc.ca/mediawiki/index.php/Windows_-_blecgh#Cygwin](https://turing.phas.ubc.ca/mediawiki/index.php/Windows_-_blecgh#Cygwin). Since cygwin uses openssh, you will be able to use the above configuration tip exactly as you would on a Linux client.

Maybe someone else with more experience with putty could chime in here with the equivalent configuration.

---

