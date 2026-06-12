---
title: "Problems installing screenlet themes"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Ulysses on 2010-11-23
Hello,

It's late and I'm tired and that is no excuse. But I'm stupid and I can't fix it ; my stupid that is.

:-k:-?:shock:

I cannot install new themes for the clock screenlet.
I went to gnomelook, downloaded the theme in question (plain black ; that's how I roll).
I left it as a .zip file.
I downloaded it to my download folder.
I opened the screenlets application (Applications>Accessories>Screenlets)
Then I went to install the theme and it asks me if gksudo is installed and if it can proceed and then it tells me there is an error.

Oh, guys and girls. If someone out there can please help me by giving my head a good shake, it would be immensely appreciated.

RAR

---

### Post by garylinux on 2010-11-24
In your home dir look for a dir called .screenlets
unzip the theme into that dir in my case I have one called
DigitalClock   restart the screenlet server  and the new theme will show up  (for that user only but most machines are single user anyways)

---

### Post by Ulysses on 2010-11-24
Hey

Tried that
Still won't let me
Tells me I don't have permissions
Why don't I have permissions? Why do I have to do this as root?
This is not making sense to me

RAR

---

### Post by garylinux on 2010-11-27
make sure it is 
/home/your_login_name/.screenlets
where your_login_name  is the name you login as
also make sure  that if.screenlets  exists there  that it is not owned by root

sorry if you already tried this

---

### Post by davebos on 2011-04-22
In Natty the themes go in /usr/share/screenlets/Clock/themes

---

