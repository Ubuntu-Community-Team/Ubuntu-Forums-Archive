---
title: "[SOLVED] .dmrc file is being ignored"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by expatCM on 2008-12-07
I have just started getting a message 

User's $HOME/.dmrc file is being ignored.  ...............  644 permissions required by user.

Some other information was there but that was the main part.  Click OK and it goes away.

So I started Ubuntu in Boot Recovery Mode and entered the following command

chmod 644 /home/username/.dmrc

The problem is that the error message still appears.  No idea why.  I took a look at the permissions of the .dmrc file using nautilus and they show the username and usergroup to be what I was expecting ....

Everything appears to be working as it should.  Any idea what this message may mean or how to get rid of it?

---

### Post by shifty_powers on 2008-12-07
[https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296)

will give you some more information

---

### Post by drs305 on 2008-12-07
I wrote a HowTo on this subject - and how to fix it. There may be several steps necessary to resolve the issue. If you don't get it resolved after reading through the following post back. If you do, please mark it Solved:

[Forum thread on .dmrc errors]("http://ubuntuforums.org/showthread.php?t=976610") (Go to Section 5 for the quick fix)
 
[Community wiki on dmrcErrors]("https://help.ubuntu.com/community/dmrcErrors")

---

### Post by Rocket2DMn on 2008-12-07
drs305 has a nice detailed tutorial here, which includes some background
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)
EDIT: Speak of the devil.

---

### Post by expatCM on 2008-12-07
Thank you to everyone for responding here .... appreciate it :)

I have solved the problem ....  what I did was read up on the links and then to chmod 700 ~ and then rebooted ....  easy ... and it worked.

---

