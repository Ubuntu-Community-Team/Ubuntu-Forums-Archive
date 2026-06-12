---
title: "Creating a New User from the Terminal"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by rabidcentipede on 2009-08-08
Hello! I recently built a new computer and installed Ubuntu (desktop) on it, and have been quite happy. I eventually added the packages necessary for it to run as a LAMP server, and it has run quite successfully.

Being a bit of a novice user, I've never really used the command line for more than installing programs, moving files, or starting/restarting apache. 

So far, I have done all of my work on the primary account that I first set up when I installed Ubuntu. However, I decided it would be useful to create another user account. Seeing this as an excellent opportunity to learn how to use the command line, I researched the commands to create a new user.

This is what I did:

*$* sudo useradd newusername
*$ *sudo passwd newusername
*Enter new UNIX password: *newpassword
*Retype new UNIX password: *newpassword

and it said that the password had been updated successfully.

Wanting to try this account out, I hit ctrl+alt+F1, and logged in with newusername/newpassword.

First of all, It told me that I didn't have a home directory. So, I went back to my primary account, and created /home/newusername. 

When I logged back in as newusername, I was in the new home directory, but I didn't have any permissions! I couldn't make a file, even in my own home directory! I tried copying a file from somewhere else, and it wouldn't let me do that either!

At this point I gave up, and went back into my primary account in graphical mode, and created a new user from the administration tools. which worked fine. :/

Any tips on where I went wrong, or what I can do to fix this?

---

### Post by Liolikas on 2009-08-08
[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

---

### Post by wojox on 2009-08-08
I've never used useradd but the man page says:
```
sudo useradd -m username
sudo passwd username
```
The -m creates a home dir for user.
I use:
```
sudo adduser newuser
sudo passwd newuser
```
Which is what useradd man page recommends. In the terminal type man <command> to find out more.
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Hope that helps.

---

### Post by rabidcentipede on 2009-08-08
Ohhhh okay thanks so much! So now I understand why I had to make a home directory... still not sure about the lack of permissions.

I just tried it with adduser, and it worked this time. 

Ok, upon checking the man page for useradd, it says "useradd is a low level utility for adding users. On Debian, administrators should usually use adduser(8) instead."

Thanks again!

---

