---
title: "connection active but not connected ?!"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by dbch on 2010-04-15
I got a used computer.  It started acting wacked.  I got another mouse yesterday and it seemed  to be ok.
 
Now it won't connect.  It shows active connection but firefox shows page not found, no connection.  Even the software centre shows no internet connection, can't download.
 
It happened last night but I got it to work somehow, I don't know what happened.  Today I'm clicking at everything but it still won't load anything and shows active connection.
 
Anyone tell me what's going on?  Before my hour at the library is up???
 
Thank you!:confused:

---

### Post by ttshivers on 2010-04-15
Are you running a wired or wireless connection?

---

### Post by dbch on 2010-04-15
DSL cable.  I tried 'system testing'.  It had a pop up saying modem failed.  But its being working fine until just after I put the other mouse yesterday.  After I somehow got it to work I was using it for hours.  Turned the computer off, turned it on today and nothing.

---

### Post by sydbat on 2010-04-15
We need some more information so we can help you.

What kind of computer is it? A laptop? Desktop?

What version of Ubuntu have you installed?

As ttshivers asked - how are you trying to connect? Wired or wireless.

What is the type of Ethernet card does the computer have? To find out what type of card, run this in a terminal (Applications > Accessories > Terminal):```
lspci
```and post the results here using the [CODE] tags.

---

### Post by dbch on 2010-04-15
Desktop.  Latest version of Ubuntu.  
 
Connect?  Its a DSL Shaw Cable connection thru a cable router with my roomate.  It connected automatically. 'etho (or atho) connection established'.
 
Ethernet card - I've got 15 minutes left here, I live across the street.  I'll go check and come back.
 
Thanks!

---

### Post by dbch on 2010-04-15
Hi.  13 minutes left at the library.  
 
I ran '1spci' and it said 'command not found did you mean 'lspci''?  So I typed it and a hold load of stuff came ending with:
 
Broadcom Corporation BCM4401 100 Base-T (rev 01)
 
For network connections, its auto etho0 (default) under 'Wired'.  DSL is blank - we don't need a username or password.  Firefox says server not found.

---

