---
title: "[SOLVED] Ok, I give up... USER?"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by jp317 on 2009-01-09
I found Wubi installer on the web, and thought it sounded like a good idea, and installed it on a Dell laptop running Windows 2000.  It ground away for nearly 10 hours on my slow DSL, but finally there's Ubuntu, but... the first thing I get is a USER box, and I've not got the least clue who Wubi decided the USER should be, let alone the password of this mysterious user.  I've searched these forums and the net at large, and i'm sure the answer is there somewhere, but I've not found it yet, so... can some kind person tell me how to get this ubuntu usable?  If so, I would be grateful.

Thank you.

---

### Post by overdrank on 2009-01-09
> **jp317 said:**
> I found Wubi installer on the web, and thought it sounded like a good idea, and installed it on a Dell laptop running Windows 2000.  It ground away for nearly 10 hours on my slow DSL, but finally there's Ubuntu, but... the first thing I get is a USER box, and I've not got the least clue who Wubi decided the USER should be, let alone the password of this mysterious user.  I've searched these forums and the net at large, and i'm sure the answer is there somewhere, but I've not found it yet, so... can some kind person tell me how to get this ubuntu usable?  If so, I would be grateful.

Thank you.

Hi and welcome, you should have enter the user name and password before wubi installed.

---

### Post by NfF on 2009-01-09
Hello! Welcome to the Ubuntu.
Like what the admin above said, type in ur username and password (:or reinstall ubuntu if everything fails.

---

### Post by porchrat on 2009-01-09
What they are saying is that the when the installer runs it will prompt you for a username and password.  After you have entered those, and done a few other things, wubi will install.  You then use the username and password you entered during the installation process to access wubi.

> **overdrank said:**
> Hi and welcome, you should have enter the user name and password before wubi installed.

Hey...how come overdrank gets to use an animated avatar and the rest of us don't?

---

### Post by sisco311 on 2009-01-09
you have to choose your username and passwoed during the installation:
[IMG]http://www.psychocats.net/ubuntu/images/wubi02.png[/IMG]
[http://www.psychocats.net/ubuntu/wubi]("http://www.psychocats.net/ubuntu/wubi")

if you have forgot your username and password try this:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by jp317 on 2009-01-09
Ok, I finally found an answer in another thread on this forum.  Here it is, copied for the benefit of anyone reading this in the future.
[I] Re: username and password
You should be able to find out the username from recovery mode, reboot - pick recovery - when you get to the small recovery menu choose root prompt

Code:

grep 1000 /etc/passwd

should give you the username -eg

kevin:x:1000:1000:kevin,,,:/home/kevin:/bin/bash

Then do
Code:

passwd yourname

exit and resume, then you can use your username and new password[/I]

---

### Post by porchrat on 2009-01-09
> **jp317 said:**
> Ok, I finally found an answer in another thread on this forum.  Here it is, copied for the benefit of anyone reading this in the future.
[I] Re: username and password
You should be able to find out the username from recovery mode, reboot - pick recovery - when you get to the small recovery menu choose root prompt

Code:

grep 1000 /etc/passwd

should give you the username -eg

kevin:x:1000:1000:kevin,,,:/home/kevin:/bin/bash

Then do
Code:

passwd yourname

exit and resume, then you can use your username and new password[/I]

Oh now I get it...you wanted to know where to FIND the username.  Next time please be a little clearer with what you want. You never actually asked where the username was stored, we all thought you meant "where did this user and password thing come from?"

---

