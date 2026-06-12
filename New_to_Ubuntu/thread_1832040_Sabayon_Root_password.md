---
title: "Sabayon Root password"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by stewartie4 on 2011-08-24
Hi I'm customizing my default user profile for ubuntu with sabayon which I got here:
[http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)

It is utterly fantastic, so simple to use but my onl problem is this: I need to run a script as root to install my theme but my root password doesn't work as I am in a virtual account.
does anyone know the root password in sabayon?

---

### Post by haqking on 2011-08-24
> **stewartie4 said:**
> Hi I'm customizing my default user profile for ubuntu with sabayon which I got here:
[http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)

It is utterly fantastic, so simple to use but my onl problem is this: I need to run a script as root to install my theme but my root password doesn't work as I am in a virtual account.
does anyone know the root password in sabayon?

a virtual account ?

when asked to run as root it requires you to use your own password using sudo.

run the script using sudo and enter your own login password

---

### Post by stewartie4 on 2011-08-24
yes I know that but sabayon isn't the script it is a program that lets you set the default theme for new user accounts. The way it does this is by opening a sort of virtual machine, you customize the theme then save it, but as it is a virtual account the root password is different.

---

### Post by haqking on 2011-08-24
> **stewartie4 said:**
> yes I know that but sabayon isn't the script it is a program that lets you set the default theme for new user accounts. The way it does this is by opening a sort of virtual machine, you customize the theme then save it, but as it is a virtual account the root password is different.


oh gotcha.

see here [http://wiki.sabayon.org/index.php?title=En:Sabayon_Linux](http://wiki.sabayon.org/index.php?title=En:Sabayon_Linux)

scroll down a little

could be no password, root or sabyonuser

---

### Post by stewartie4 on 2011-08-24
> **haqking said:**
> oh gotcha.

see here [http://wiki.sabayon.org/index.php?title=En:Sabayon_Linux](http://wiki.sabayon.org/index.php?title=En:Sabayon_Linux)

scroll down a little

could be no password, root or sabyonuser

sorry again :(
you're talking about the operating system , I'm talking about the program, its called user profile editor on the software center.
so those passwords don't work.
thanks anyway

---

### Post by haqking on 2011-08-24
> **stewartie4 said:**
> sorry again :(
you're talking about the operating system , I'm talking about the program, its called user profile editor on the software center.
so those passwords don't work.
thanks anyway


ok so see here [http://www.linux.com/archive/feature/114319](http://www.linux.com/archive/feature/114319)

it says you need to know root password.

so as i said in first post.  Run it as sudo from terminal

gksudo sabayon

and supply your login password

---

### Post by stewartie4 on 2011-08-24
> **haqking said:**
> ok so see here [http://www.linux.com/archive/feature/114319](http://www.linux.com/archive/feature/114319)

it says you need to know root password.

so as i said in first post.  Run it as sudo from terminal

sudo sabayon

and supply your login password

uugh "a fatal error has occurred"
maybe I should just give up lol
thanks for your help anyway :)

actually I can run it fine but when in the virtual account for customization it says I need a root password but mine wont work as its not on my account, its on the account sabayon-admin so my password won't work.

---

### Post by haqking on 2011-08-24
> **stewartie4 said:**
> uugh "a fatal error has occurred"
maybe I should just give up lol
thanks for your help anyway :)

actually I can run it fine but when in the virtual account for customization it says I need a root password but mine wont work as its not on my account, its on the account sabayon-admin so my password won't work.


ooh yeah my bad

i meant:

gksudo sabayon 

as it is graphical, try that

---

### Post by stewartie4 on 2011-08-24
> **haqking said:**
> ooh yeah my bad

i meant:

gksudo sabayon 

as it is graphical, try that
thanks very much for all your help but my passowrd still won't work when trying to run a script inside the virtual window.

---

### Post by snowpine on 2011-08-24
/etc/skel is where defaults for new user accounts are stored. The contents of /etc/skel are automatically copied to a new user's /home when the account is created.

---

### Post by stewartie4 on 2011-08-24
> **snowpine said:**
> /etc/skel is where defaults for new user accounts are stored. The contents of /etc/skel are automatically copied to a new user's /home when the account is created.
so I could just customize my account then copy the contents of my home folder (inc hidden files) to there?
would that work?

---

### Post by snowpine on 2011-08-24
> **stewartie4 said:**
> so I could just customize my account then copy the contents of my home folder (inc hidden files) to there?
would that work?

Exactly, correct. :)

---

