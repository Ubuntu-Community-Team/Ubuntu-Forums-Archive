---
title: "install problem &quot;who are you?&quot; screen"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by opentarget on 2011-04-11
Im new to ubuntu and having some issues...
Im installing xubuntu on an old windows machine.
I want to just write over the harddrive so clicked the "erase and use the entire disk" option.

passed the language and keyboard/ time options and on to "who are you?" options and filled them all in. but at this point it wont let me click forward to install.

any idea?

---

### Post by Quintilian on 2011-04-11
Does it not let you go forward past the "Who are you?" screen? 
I thought it usually starts installing when you get to the screen that asks you "Where are you?"...

Does it leave you at a screen thats kinda like a slide show? Or it locks up right before that?

---

### Post by ~Plue on 2011-04-11
> **opentarget said:**
> 
passed the language and keyboard/ time options and on to "who are you?" options and filled them all in. but at this point it wont let me click forward to install.

make sure you don't have any spaces/uppercase/special characters in the username field

try with all lowercase letters and/or numbers only

---

### Post by opentarget on 2011-04-11
thanks for the quick reply s people :)

@ plue, thats it, i had all caps in the username.
god so simple, but i always have it in caps, time to change my ways.

---

### Post by opentarget on 2011-04-11
so im working on getting a server running on this old pc.
im following:
[http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)
this guide.

but when i get to changing the samba code, then to i try to reboot samba in the terminal by (  /etc/init.d/samba restart    )
i get: bash:  /etc/init.d/samba: No such file or directory

im sure im doing somthing wrong, but im not sure what.

---

### Post by Quintilian on 2011-04-12
i think you should have marked this thread as [solved] and opened a new one...

but since we're here...you need to make sure you have samba installed.
try:
sudo apt-get install samba
and it should install if it isn't already. i looked on my system and i do have the smb.conf file, but samba is not installed by default apparently.

---

