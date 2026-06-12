---
title: "Update Manager Help"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by kiniyaloca1 on 2011-01-22
Hi, all of the sudden when I attempt to update my system via the update manager i get this error (see attached pic). Im running maverick [cant wait for Natty! :)] 64-bit. This just all of the sudden happened...not really sure why. Please help

--thanks,
  
    Anthony

---

### Post by owlcroft on 2011-01-22
First, check the obvious: is your internet connection still ok?  (It looks like it, as you were able to post the message.)  Have you tried again?  Sometimes repositories can go down for a few minutes.  Is the address indeed still unchanged and correct?

We can then go from there.

---

### Post by rezaervani on 2011-01-22
The screenshot show that your link is wrong.

You will not found [http://ppa.launchpad.net/user/ppa-name/](http://ppa.launchpad.net/user/ppa-name/) . It is a wrong address

Just remove it from your repository address.

Use :

> System --> Administration --> Software Sources

Klik tab Other Software

Choose [http://ppa.launchpad.net/user/ppa-name/user/](http://ppa.launchpad.net/user/ppa-name/user/) bla bla bla from list and click remove

than update your system with
> 
sudo apt-get updateOr you can also edit your /etc/apt/sources.list

and remove deb [http://ppa.launchpad.net/ppa-name/user/](http://ppa.launchpad.net/ppa-name/user/) bla bla from your list

For ppa you can check it directly into [http://ppa.launchpad.net](http://ppa.launchpad.net)

Hope it helps ...

[B]--- 
Yayasan Rumah Ilmu Indonesia
[http://www.rumahilmuindonesia.or.id](http://www.rumahilmuindonesia.or.id)
Official Ubuntu Archive Mirror
[http://cermin.rumahilmu.org](http://cermin.rumahilmu.org)[/B]

--

---

### Post by kiniyaloca1 on 2011-01-22
Ok i removed "http://ppa.launchpad.net/user/ppa-name/ubuntu" & "http://ppa.launchpad.net/user/ppa-name/ubuntu" and now the update manager seems to be working and says everything is up to date. Is there any reason why those were in there? Still kinda a noob to linux...

---

### Post by rezaervani on 2011-01-22
> **kiniyaloca1 said:**
>  Is there any reason why those were in there? Still kinda a noob to linux...

OK, glad it helps, so you can mark this thread as SOLVED.

For your question, why that link be there is simple :

[http://launchpad.net/user/ppa-name](http://launchpad.net/user/ppa-name) is often use as example if you want to add ppa repository.

There is a lot of ppa software. 

User refer to people who develop the software
ppa-name refer to the name of software

Example : ppa for LibreOffice will be looked like :
[http://launchpad.net/libreoffice/ppa](http://launchpad.net/libreoffice/ppa)

Or for software from Sabily Team (like thwab) will be looked like :
[http://launchpad.net/sabily.team/ppa](http://launchpad.net/sabily.team/ppa)

---

