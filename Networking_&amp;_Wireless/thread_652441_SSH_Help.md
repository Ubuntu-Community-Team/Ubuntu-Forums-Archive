---
title: "SSH Help"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by jamescondron on 2007-12-28
Heres the simple idea I'm trying to implement (always a good start)

I'm trying to create a simple menu to come up when a user SSHs into my box, much like when someone SSHs into, say, a home networking router, but have no idea how to implement this.

I've looked into putting a BBS on top of port 22
I've looked into making MOTD executable and creating writing it as a bash script to run as a simple shell, as it were
I've looked into setting the default SSH shell as a bash script

Whilst any of these may or may not be the answer, I have no real experience in any of them which would mean that the length of time it'd take to implement any would be a ball ache if it didn't work.

Could any body suggest any thing to help in this idea? Whether it is an already written script, or to say whether any of the things I've looked into would work, were I to try it and get it working?

Sorry if this has been asked and answered, but I couldn't find it in the search.

Cheers

EDIT: Spelling

---

### Post by kevdog on 2007-12-28
If you want to make a script system wide, why dont you put something in the system wide .bashrc file, since I believe the .bash_profile sources the user and system wide .bashrc file when the login shell is invoked.   If you wanted to only run this script with ssh logins into the server, but not regular logins, Im not sure how you would do this.  I think the settings in the sshd_config file only sets parameters and does not run executables.

---

### Post by jamescondron on 2007-12-28
I had considered .bashrc as a method, but didn't do it for precisely that reason.

Good idea though

---

