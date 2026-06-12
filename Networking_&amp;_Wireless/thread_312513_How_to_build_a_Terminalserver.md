---
title: "How to build a Terminalserver?"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by Don_DiZzLe on 2006-12-04
Hello peeps,

I'd like to know how to build a Terminalserver with Ubuntu with Windows clients. First of all, I guess i need Ubuntu Server for the job, but where do I got from there? Which packages do I need to install and so on...

Any help would be much apreciated.

---

### Post by halfvolle melk on 2006-12-04
What is it that you want to do exactly?

For one thing, you could install **openssh-server** on the Ubuntu server and use [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) to access it from your Win machines.

---

### Post by Don_DiZzLe on 2006-12-04
We willen dat mensen inloggen op de server maar dat ze werken in een windows omgeving, dus ze loggen in de Linux server en de clients werken dan in Windows XP of 2000.

---

### Post by halfvolle melk on 2006-12-04
Let's keep this in English so others can chime in to help or read it for tips :)

You want people to be able to log-in from a Win-based system using a GUI? I don't know much about that but maybe you could use FreeNX or something like that. Maybe someone else knows more on the subject (someone that speaks English for instance ;)).

---

### Post by Don_DiZzLe on 2006-12-04
Your right, my bad I'll say it in English.

Yeah i just installed freenx server on my Ubuntu box set the port to 8888 in those 2 files in the wiki [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) , now what remains is installing the freenx client on my other Windows box

---

