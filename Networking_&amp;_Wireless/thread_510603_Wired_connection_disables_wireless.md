---
title: "Wired connection disables wireless"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by AndyPopely on 2007-07-26
I'm using Feisty Fawn and mostly connect to my router wirelessly.  It connects automatically to my router on a Feisty Fawn restart with no problem.  If I connect to my router using a wired connection that too connects with no problem.  

Now the problem.   If I disconnect the wired connection to the router and reboot Feisty Fawn the Network Manager doesn't even try to connect wirelessly to the router.

To resolve the problem I have to edit /etc/network/interface and comment out all the lines describing the wired connection then reboot Feisty Fawn and then wireless works as it did before.

Is there an option that allows me to switch between wired and wireless connections without me editing /etc/network/interface ?

---

### Post by NilsE on 2007-07-26
It's clear that you noticed that when one is active the other is disabled and that is by design.

However, I have also noticed that most times when I go from a wired connection to a wireless connection it works just fine.. Sometimes it does not always automatically go to the wireless but all I have to do is left click the network icon in the panel and then click on the network I want and it connects fine.  By the way, that is the nm-applet icon I am talking about.

---

### Post by AndyPopely on 2007-07-27
Yes me too if I click on the nm-applet icon I can select my router from the list and it will connect though it has never been able to connect wirelessly automatically after a wired connection.

I was hoping that if the Network Manager detected no wired connection it would try to log me on automatically via my wireless connection as it does now when there are no wired connection details in the /etc/network/interface file

Does this imply that if a wired connection has ever been used then you'll never be able to automatically connect wireless ?

---

