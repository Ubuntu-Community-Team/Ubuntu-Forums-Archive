---
title: "Re: Root acct."
date: 2010-10-14
forum: New to Ubuntu
---

### Post by patrik k on 2010-10-14
Recently installed Ubuntu 10.04 as a dual boot with my XP machine.
After having to reformat and reinstall xp due to a rootkit/virus that was dug in real deep, I decided to give Linux another try.
The last Linux anything I did was a required semester of some flavor of command line only Linux.
Since then, I have not even looked @ Linux.
I have grown very tired of the security and constant update issues of my XP.
So, as a new Linux user, I am afraid I must start out asking the usual dumb type question.
(I know, the only dumb question is the one not asked right?)
When Ubuntu installed, I was only asked to set up my user acct.
Nothing was asked regarding the p/w for the root account.
Since I am configuring my peripherals and such to operate under this new os, I need access to the root account @ the terminal.
I have tried the user account p/w but authentication fails.
Gawd, did I miss something.
Thanks for any assistance.
patrik

---

### Post by Toz on 2010-10-14
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ctrl-Alt-F1 on 2010-10-14
Ubuntu doesn't like you to use root account as it can create some security problems for those that don't know how to do it properly.

To run a command with root privileges, simply add sudo before the command.  For example "apt-get install amarok" will fail because I need root privileges, but "sudo apt-get install amarok" will work.  It will ask you for the password for YOUR account, then complete the command if your password is correct.

---

### Post by patrik k on 2010-10-14
Thanks to both of you.
That is what I needed and am reading the documentation along with my text book.
patrik

---

### Post by lisati on 2010-10-14
As others have indicated, the preferred way of gaining superuser privileges (a.k.a. "root") in Ubuntu is through the "sudo" command and its variants. Don't forget to use gksudo for graphical commands.

As an aside, "sudo" can mean "**s**uper **u**ser **do**", and can also mean "**S**witch **U**ser and **do**" or "**S**ubstitute **U**ser" - see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) and [http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo) for more information

---

