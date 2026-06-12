---
title: "DV9000 Laptop, no network connection"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by causticburning on 2011-01-24
Hello, 

I've decided to try ubuntu studio, and the way it seems to have installed on my HP DV9000 laptop (yes, read the threads) is without either the wireless or the network connection.  This means I can't even really start to install webcam etc.

Is there a way I could somehow load the drivers I need onto a CD and make the OS look for them there?  If so, how do I do it?  Also I don't know how to find out what drivers I need.

This is all assuming there isn't something else kaput in there somewhere.

I don't really know where to start, so I'd appreciate a hand :)

---

### Post by wep940 on 2011-01-24
Wireless is usually just a matter of drivers - please post the output of:
 
lspci
 
-and-
 
lsusb
 
back here so we can see what chipset the wireless is using.
 
You also mention that you don't get a network connection - are you talking about a hard-wire connection?  If you connect an ethernet cable to your laptop and to a port on your router what happens?

---

### Post by causticburning on 2011-01-24
The output of lspci/lsusb is very long; is there any specific thing you want to know from it?

I don't have a network connection, I'm on another PC.

I currently have the computer plugged into my router and wireless switch on.

---

### Post by wep940 on 2011-01-27
[SIZE=2]I assume you mean you have the PC hard wired with an ethernet cable to the router?  If so, try this:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]- open a terminal window[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]- type:[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]sudo apt-get update <press enter>[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]Now go to system/administration/additional drivers (might say restricted or other drivers).[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]See if a driver shows and if so be sure it is enabled.  Now disconnect the cable going to your router.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Then go to network manager and be sure wireless is enabled.[/SIZE]

---

### Post by causticburning on 2011-01-27
This would work, except that **I don't have a network connection, even with the cat5 plugged between the router and my PC **

---

### Post by wep940 on 2011-01-29
In the output from lspci, look for the information that deals with network controllers and wireless adapters and copy/paste that here.
 
Also go to a terminal window and:
 
lshw -C network
 
and post that output back here as well.

---

### Post by wep940 on 2011-02-05
Also, as dumb as it sounds, be sure you are using the correct type of CAT5 cable - some are cross-over, some are straight-through.

---

