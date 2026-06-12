---
title: "SSH Connection Refused"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by josesanders on 2006-12-29
I have installed SSH server on two edgy machines, and both seem to be listening to port 22.  For some reason, though, only one machine is accepting incoming connections - I can SSH from machine one to machine two, but not from machine two to machine one.  I did the same thing on both machines, just ran the command:
$ sudo apt-get install openssh-server

Does anyone have any ideas about why this might be?  I'm new to linux networking, so it might be something very obvious.  I don't have any firewalls installed.

---

### Post by c.dric on 2006-12-29
did you start the ssh server on both machines ?

sudo /etc/init.d/ssh start

[it's very very obvious, but i had to ask :) ]

---

### Post by josesanders on 2006-12-30
I tried running that command, and it said that it failed, but gave no reason, so I decided to just remove openssh-server, and reinstall, and it worked.  I don't know what was wrong, but it's working now.  Thanks for the suggestion.

---

### Post by c.dric on 2006-12-30
i had something similar a few days ago. 

i did sudo /etc/init.d/ssh start to start ssh and it failed, then i looked at the conf file -without- changing anything ... made another attempt to start it with sudo /etc/init.d/ssh start and then it worked.

don't ask me how :???:

---

### Post by theorem_hunter on 2007-01-03
im getting the same error, but the 
sudo /etc/init.d/ssh start
command is not working for me...
it just said [fail]
so i tried
sudo /etc/init.d/ssh restart
and it said [ok] 
but i still get this:
$ ssh [email]dimitri@dimitri.homelinux.net[/email]
ssh: connect to host dimitri.homelinux.net port 22: Connection refused


any help?

---

### Post by josesanders on 2007-01-03
That sounds a lot like what was happening with me.  I just removed ssh server and reinstalled:

$ sudo apt-get remove openssh-server

After this command, it recommended that I remove some extra stuff with another apt command, so I did that. Then I reinstalled:

$ sudo apt-get install openssh-server

Then everything worked.  I hope this helps.

---

