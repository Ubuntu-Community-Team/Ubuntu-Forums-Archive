---
title: "Connection to Internet on Hardy 8.0.4"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by newDrapersDrakeUser on 2008-07-15
Hi 

I have recently installed Ubuntu 8.0.4 on my desktop.It works like breeze barring one small problem that i have to reboot my desktop once before the broadband connection gets working. I.e if i am logged in and working internet connection will be working but if i shut down my m/c and boot it at later point of time it will not connect to net unless i reboot it one more time then.

There is virtually no difference in processes or settings i find between two restarts but always takes me two restarts to make internet connection working.

I am using Wired broadband connection with automatic IP setting. Roaming mode is also enabled for the same.


Can some one help me with this.

Thanks

---

### Post by wahabr on 2008-07-15
try:
> 
sudo pppoeconf

after that set the option to turn the connection automatically after every start of the computer, wish it will help

---

### Post by newDrapersDrakeUser on 2008-07-15
I tried running the command 

sudo pppoeconf but after scanning it gives error stating

           Sorry, I scanned 1 interface, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.

the process figures out the eth0 as my network interface but the network connection icon shows as lo.

Please suggest

---

### Post by wahabr on 2008-07-15
> sudo poff dsl-provider

then try again to do the 
> sudo pppoeconf

---

### Post by newDrapersDrakeUser on 2008-07-17
Hi 
Thanks for help but sorry to inform you that this had also no effect. 

Please suggest
Thanks

---

### Post by khayden39005 on 2008-07-17
i tried this and the output was
/usr/bin/poff: No pppd is running.  None stopped.
any ideas?

---

### Post by newDrapersDrakeUser on 2008-07-20
Internet connection on my hardy has now stopped working suddenly. On same m/c windows counterpart is able to connect to network without any problem.

On ubuntu earlier it was working with two restarts but suddenly it has stopped connecting to network.

Please help...

---

### Post by newDrapersDrakeUser on 2008-07-20
I did a complete reinstall of ubuntu 8.0.4 now it is able to connect but again back to two restart stage.

Can some one please help me correct this two restart problem.
:(

---

