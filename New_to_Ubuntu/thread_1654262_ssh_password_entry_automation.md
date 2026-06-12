---
title: "ssh password entry automation?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Unewbeginner on 2010-12-28
How could I do it automatically with bash script? I just input "enter x.x.x.x" and it will help me input my password? Thanks!

---

### Post by xifer on 2010-12-28
> **Unewbeginner said:**
> How could I do it automatically with bash script? I just input "enter x.x.x.x" and it will help me input my password? Thanks!

you could store the text in a script file - but that's not very secure.  Would it be better to generate PGP key on the intended client, forward it to the server so it can trust your connection?

---

### Post by freak42 on 2010-12-28
[http://www.google.ch/search?q=ssh+passwordless+login](http://www.google.ch/search?q=ssh+passwordless+login)

---

### Post by Wtower on 2010-12-28
Hi, take a look at: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Unewbeginner on 2011-01-01
I saw someone recommended a command called "expect". Anyone knows how to use it?

---

### Post by perspectoff on 2011-01-01
You can, but you don't want to.

SSH passwords are transmitted unencrypted and can be intercepted by a man in the middle. It is not a particularly secure way of doing things.

You should use keys instead.

Here are some instructions:

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH](http://ubuntuguide.org/wiki/Ubuntu:Maverick#SSH)

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#SSH](http://kubuntuguide.org/Maverick#SSH)

If you are really intent on doing it, though, you need a little utility called expect. Then you can automate the process:

    * Install the expect utility: 

sudo apt-get install expect

    * If for example your SSH client ID is clientuserID, yourpassword is not#1sostrong, and the remote SSH server is remoteserver.computer.xyz using the default SSH port of 22, then use this command to start the SSH tunnel: 

expect -c 'spawn ssh -l clientuserID -L 5900:127.0.0.1:5900 remoteserver.computer.xyz -p 22; expect assword ; send "not#1sostrong\n" ; interact'

There are other parameters in this example. 5900 are the ports to be used on either side of the tunnel (port 5900 is used for VNC, for example).

You can use the entire command as a menu item (must be "Run in terminal" in the Advanced menu options).

---

