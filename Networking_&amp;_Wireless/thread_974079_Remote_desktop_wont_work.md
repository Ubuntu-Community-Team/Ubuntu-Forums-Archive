---
title: "Remote desktop wont work"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by arnoldg on 2008-11-07
Hello, 

i have installed ubuntu 8.10, now i wan't to connect from a windows pc to the ubuntu by remote desktop.

in ubuntu i enabled this feather, but when i now connect from windows to ubuntu.
I have to enter the password. Next there is only a blank black screen with a very small square in it. after a while vnc stops and shut down. i also tryed thightvnc. same problem.

what could be wrong. the windows pc and ubuntu are in a local network.

---

### Post by arnoldg on 2008-11-07
Is there nobody who could help me.

with vnc viewer on the windows machine, it says 

"Read: Connection reset by peer (10054)
Do you wish to attempt to reconnect to 192........."

what does this measn

---

### Post by jonobr on 2008-11-07
Hello


I may not be able to help, but can you clarify,
Your not using remote desktop on you Win client, you are using vnc,tight vnc or ultra vnc viewers.
I am guessing you have installed VNC server on your Ubuntu 8:10 machine?
Is that correct?

---

### Post by arnoldg on 2008-11-07
no i don't have installed the vnc server.

can i use the devolp remote desktop viewer within windows ?
if so, how do i setup this.

do i only have to enter the ip adres.

i use windows vista home

---

### Post by jonobr on 2008-11-07
Just CHecking to see if you have allowed remote connections.

Im upgrading to 8:10 at the moment but will test for you once done.

In general, 
Go to System>> Preferences >> Remote Desktop

Check......
Allow other users to view your desktop
Allow other users to control your desktop
Remember this is allowing people to connect remotely so set a super duper password!!!

Then using your vnc client connect to the IP address and hopefully it will ask for a password

Once again, once my upgrade is complete, I will give it a try myself

---

### Post by Sami_Sdata on 2008-11-07
I had remote desktop enabled under Hardy and used a remote connection from my work regularly.  Under Ibex I found the screen writes to be unusably slow.  x11vnc does work just fine under Ibex.  If you can't get remote-desktop to work you might try disabling it and installing x11vnc.  I did not get the blank screen you are seeing but the screen writes were so slow that if I started the connection with the screensaver already running it would be a minute or two before I had the desktop showing instead of whatever screensaver was running.  

to install x11vnc
sudo apt-get install x11vnc

to run it from a local xterm or ssh into the ubuntu box and run
x11vnc -noxdamage -display :0

The noxdamage isn't always needed but helped with compiz running.  x11vnc can be set up to run at startup I believe but I've never used it that way.  I prefer to only have the server running when I'm ready to use it.

---

### Post by jonobr on 2008-11-07
Just tried the connection to Ubutnu 8:10 after upgrade and chaning the remote desktop settings.

Launched vnc session from tight VNC using default connection options.
Allowed access when prompted on Ubuntu and all seemed to work,
not super fast but workable

---

### Post by arnoldg on 2008-11-08
i had tryed tight vnc, next i will try is the x11vnc from sami_sdata. i let you hear if this solves the problem.

with x11vnc i don't need to change any settings.


i have installed x11vnc, but the problem exist. this is verry strange, stil a black screen and nothing else.

---

### Post by krunge on 2008-11-08
> **arnoldg said:**
> i had tryed tight vnc, next i will try is the x11vnc from sami_sdata. i let you hear if this solves the problem.

with x11vnc i don't need to change any settings.


i have installed x11vnc, but the problem exist. this is verry strange, stil a black screen and nothing else.

You have to run x11vnc manually by hand in a shell, as Sami_Sdata indicated.  It's not clear you did this, did you?

If you did, post the output that x11vnc printed out to the screen, including when you try to connect with a vnc viewer.

---

