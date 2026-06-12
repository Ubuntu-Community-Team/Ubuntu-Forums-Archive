---
title: "Why is Update Manager asking for 9.04 cd on Ubuntu 8.10?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by resander on 2009-07-14
I have always kept my Ubuntu 8.10 up to date by installing all updates.

Recently I keep getting this message when clicking 'Install Updates' button:

Please insert disk labelled:
Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)
in drive /cdrom/

I don't have this CD and I want to continue using 8.10, which is working fine. I have never clicked the 'Upgrade' to 9.04 button at the top of the Update dialog.

Would I not be inviting problems if I got the CD with 9.04 packages and tried to install updates on 8.10?

Updating the package dpkg-dev (it is in the list of updates available) causes this message to appear.

I have never been asked to insert a CD to do the routine updates before. 
Why now?

---

### Post by vinutux on 2009-07-14
If you ever inserted ubuntu 9.04 cd and add repos to synaptic


Anyway open software sources

System->administration->software sources 

and **untick** ubuntu 9.04 cd  fuunder **Installable from cd-rom/DVD section**

.

---

### Post by resander on 2009-07-14
There is no 'ubuntu 9.04 cd' in the Installable from CD-ROM/DVD section. There is a ubuntu 8.10 though and that is already unticked.

Your first sentence starting 'If you ever...' ends half-way. I guess the tail part should read 'you will end up with trouble'. Right?

---

### Post by vinutux on 2009-07-14
So no way to ask ubuntu 9.04 cd....sounds strange..........////

---

### Post by swoody on 2009-07-14
> **resander said:**
> There is no 'ubuntu 9.04 cd' in the Installable from CD-ROM/DVD section. There is a ubuntu 8.10 though and that is already unticked.

Your first sentence starting 'If you ever...' ends half-way. I guess the tail part should read 'you will end up with trouble'. Right?

Well, if it's not showing up in the GUI version, lets go check the file itself :D

Open a terminal (Applications>Accessories>Terminal) and enter:
```
gksu gedit /etc/apt/sources.list
```

It'll ask you for your password, so enter it, and hit enter. When the gedit window opens, look for a line that begins with "deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope" If that listing is in there, you'll need to put a # in front of it. Then make sure to save the file, and you can exit that program.

After you exit, go back into Update Manager and check if it gives you the same error message now :)

---

### Post by tarps87 on 2009-07-14
Can you try:
```
cat /etc/apt/sources.list | grep jaunty
```
and
```
cat /etc/apt/sources.list | grep Jaunty
```

This should list any references to 9.04 in you sources list

---

### Post by resander on 2009-07-14
Thanks,

Yes, it was in /etc/apt/sources.list. Loud and clear! Problem solved after commenting out the line.

But how did it get there? I don't recall clicking the 'Upgrade to 9.04' button and backing out, which possibly could explain it.

Again many thanks.

---

### Post by swoody on 2009-07-14
Good, good. Glad that worked out for you :)

Not sure what causes it. Maybe some funky upgrade? Maybe a typo by the developer? Maybe a small gang of computer fairies snuck into your room at night to mess with you?? To be honest, I'm really not sure what would have caused this ;)

---

### Post by LewRockwell on 2009-07-14
> **tarps87 said:**
> Can you try:
```
cat /etc/apt/sources.list | grep juanty
```
and
```
cat /etc/apt/sources.list | grep Juanty
```

This should list any references to 9.04 in you sources list

shouldn't that be "jaunty" as in "a" and then "u"...

.

---

### Post by philinux on 2009-07-14
Sounds like the PEBKAC bug struck again. :lolflag:

---

### Post by tarps87 on 2009-07-15
> **LewRockwell said:**
> shouldn't that be "jaunty" as in "a" and then "u"...

.

Not in my mind :)

---

