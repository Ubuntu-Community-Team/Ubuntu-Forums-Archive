---
title: "Peculiar internet problem"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by lewis1711 on 2008-05-08
I think this is my first post, so hi all:D

Now, onto the issue. I am sharing an ADSL connection with others through a router. Anyway, as is the case the internet often stops working, we occasionally have to "reset" the modem by pulling the power out and putting it back in.

After a while though I noticed pattern. I had gaim on pretty much all the time, but whenever I tried to start up Nicotine Plus (a p2p client), the internet would stop responding and we'd have to reset the modem. Once I stopped using that we had to reset the modem far less, and we're all happier.

Now I've noticed that whenever I try and start GAIM while emesene is running, the same thing will happen, ie my "modem lights" panel app tells me I'm still connected to the net, but I can't open up any pages or log into any services. So I strongly suspect this isn't a nicotine problem, but something to do with my connection settings.

Can anyone point me in the right direction?

---

### Post by prshah on 2008-05-08
> **lewis1711 said:**
> Now I've noticed that whenever I try and start GAIM while emesene is running, the same thing will happen, ie my "modem lights" panel app tells me I'm still connected to the net, but I can't open up any pages or log into any services. So I strongly suspect this isn't a nicotine problem, but something to do with my connection settings.

Can anyone point me in the right direction?

Take a look at my (solved) thread: [http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox](http://ubuntuforums.org/showthread.php?t=718709&highlight=lynx+firefox)

Maybe it can help? 

Also, since you are sharing the connection with others, if the above doesn't help, perhaps one of you is using up the total available bandwith?

---

### Post by lewis1711 on 2008-05-08
I have plenty of bandwidth available when the internet is working, so I don't think it's merely the connection maxing out, I should have more than enough to run a browser and two chat services, is there some config file that says only this many apps can access the internet or something?

I will try resetting the Routers MTU to 1492 (as soon as I google that and figure out what that means:)) I'm afraid the rest of that link was over my head.

EDIT: Ok, I've done a bit of research about MTU, but I still have a questions
1. What website should I use to ping to determine the optimum number?
2. I am sharing the connection with 3 other computers, how might this effect them and how should I take this into account?

---

### Post by prshah on 2008-05-08
> **lewis1711 said:**
> 
EDIT: Ok, I've done a bit of research about MTU, but I still have a questions


MTU fixes are in the black magic category for me. I was desperate, read about this, decided to try it, never repented. Wish I could be of more assistance. 

Maybe someone else.... ?

---

