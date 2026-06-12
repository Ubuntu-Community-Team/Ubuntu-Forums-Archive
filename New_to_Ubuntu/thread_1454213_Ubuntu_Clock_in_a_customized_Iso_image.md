---
title: "Ubuntu Clock in a customized Iso image?"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-04-14
Anyway, I can have my startup script, change the time on ubuntu clock to the correct time zone?

Trying to find something that cane be done through command line.

And Soon, I will create a program that will ask people upon boot up what time zone they are in, and  the live cd will save their time in persistence.

I am just trying to find out how I would save the time on a isodevice and make it run from a startup script on boot up of a ubuntu live DVD 8.04.2.

Thanks in advance! :0

---

### Post by ericeclifford on 2010-04-14
Well I added ntp program to my customization script apt-get list.

Ill see how it goes and update.

---

### Post by ericeclifford on 2010-04-16
bump,

I tried to add NTP in the customization of the DVD,

but it still shows GMT time.

Do I have to remove a different "time keeper" for ntp work as default(ntp=network time)??

---

### Post by ericeclifford on 2010-04-19
B for bump :), someone know a way I can keep the timezone persistent with the live DVD iso image of ubuntu?

Is there a certain config file I can rm and then cp a modified version of the correct settings in its place.

---

