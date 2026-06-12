---
title: "Open multiple terminal applications"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by slimteufel on 2009-04-02
Okay, I want to create one file to double-click and it does all three options here in the terminal:

```

telnet 192.168.1.125

export TERM=linux

/share/bin/mc

```

I can get this to open telnet, just not the second two options.  All I am trying to do is save myself a few CTRL+C & CTRL-V strokes.  

NOTICE:  I searched for quite some time, maybe I am just not familiar enough with the lingo associated to search effectively. :D

---

### Post by Hospadar on 2009-04-02
I assume you are trying to run some command on a remote machine?

A couple things:
Is this a task that gets run (or should be run) on a regular schedule? if so you could use "cron" a program for scheduling regular tasks, if it's something that needs to be running, you can run it every minute, I have some tasks that run every 5 minutes to shuttle files around and change permissions.

If it's a task that only needs to be run at your own discression, I know ssh can run a single command remotely, I assume telnet can do the same.  
You can install public and private keys on your machines to allow passwordless ssh so you don't have to type in anything when you click.  (Also ssh is way more secure and a much better idea in general)

If I wanted to run a command on my home server, i might run something like```
ssh myname@myserver.org ls
```If i needed multiple commands, maybe something like ```
ssh myname@myserver.org "export TERM=linux;/share/bin/mc"
```

If you want to set up ssh for passwordless login, just google "ssh without password" and you'll find a bunch of article on the topic.  Obviously you'll need ssh installed on the server/remote machine - "sudo apt-get install ssh" (ubuntu comes with an ssh client by default, this installs the server)

---

### Post by slimteufel on 2009-04-02
Thanks for the quick reply.  This is a task that runs only occasionally.  What I am trying to create will open a telnet session in the terminal then tell it two commands: "export TERM=linux" which will allow my midnight commander session to run correctly and then "/share/bin/mc" to open midnight commander. This is on a local machine without ssh setup/installed so I need to stick with telnet....so..... i typed ```
telnet 192.168.1.125 "export TERM=linux;/share/bin/mc"
``` directly into the terminal and got this back ```
telnet: could not resolve 192.168.1.125/export TERM=linux;/share/bin/mc: Servname not supported for ai_socktype
``` so that explains why terminal disappears when I run my .sh.  I swear my brain is gonna implode. :D

---

