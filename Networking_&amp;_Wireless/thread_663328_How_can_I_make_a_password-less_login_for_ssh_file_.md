---
title: "How can I make a password-less login for ssh file syncronization with Unison?"
date: 2008-01-10
forum: Networking &amp; Wireless
---

### Post by Mysticle31 on 2008-01-10
I've already make it so I can bypass the password.  However, I have to run it like this.

> ssh -i  /home/$USER/.ssh/backup $USER@IPADDRESS

I make it have a password-less logon by folling the first couple of directions here.
[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

The problem is that in order to use Unison I have to have Unison start the connection with a command like this in the NAMEOFPROFILE.prf file.

> root = /home/$USER/
root = ssh://$USER@IPADDRESS//home/$USER/

As you can see.  I can't put -i or any of the location (-i /home/$USER/.ssh/backup) in the command.

How do I do this?:confused:

All I want is some file syncronised automatically from my laptop to my desktop every night.

And interesting question is.  When I do sync files, what would happen of I edited examplefile.txt to say "Hello Bob" on the desktop PC and the same file (examplefile.txt) to say "Hello Samantha" on the laptop on the same day, and they synchronized?

---

