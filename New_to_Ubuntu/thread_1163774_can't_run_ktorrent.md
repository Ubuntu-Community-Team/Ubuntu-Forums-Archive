---
title: "can't run ktorrent"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by lx.jksn on 2009-05-19
I need help to run ktorrent
I run ktorrent last some days but after somedays i got problem. i can't open ktorrent
i click ktorrent in program but it will not show anything like application on taskbar.
Also from a terminal i try to start:
sunil@Cssc:~$ ktorrent
sunil@Cssc:~$ 
i have not get any errors..
plz help me...
my email - [email]lx.jksn@gmail.com[/email]

---

### Post by superprash2003 on 2009-05-19
try reinstalling it..

---

### Post by zeroseven0183 on 2009-05-19
> **superprash2003 said:**
> try reinstalling it..

Or you can try installing alternative torrent clients like Vuze, BitTorrent Download Client, or the default application Transmission BitTorrent Client.

---

### Post by lukeozade on 2009-05-19
[B][U]Gui Instructions;
[/U][/B]
You could remove ktorrent from the system using your local package manager such as Synaptic or KPackagekit, this would be the easier way for you. If you don't want to do it this way then you could try using the terminal.

_**Terminal Instructions;**_

As long as you don't have any important settings in ktorrent you could try 

**sudo apt-get remove ktorrent**

(This will remove ktorrent using administrative privileges)

Providing that's successful then you can simply do;

**sudo apt-get install ktorrent**

(This will install ktorrent using administrative privileges)

This will install it again, hopefully getting it to work again :)

If you have any problems performing these commands, please post here again no need to supply your email address.

---

