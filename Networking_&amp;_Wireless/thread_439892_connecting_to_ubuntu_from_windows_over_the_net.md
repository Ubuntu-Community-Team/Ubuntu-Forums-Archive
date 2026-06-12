---
title: "connecting to ubuntu from windows over the net"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by firdooze on 2007-05-11
I'm having difficulties connecting to my ubuntu server from my windows machine.. 
I prefer to work on command prompt, thus i tried to connect using openssh/putty..

but i can't seem to connect to the server using either.. tried using vnc too but i can't seem to get the connection.. my gut feeling is that it is due to my dynamic ip address. i've signed up a free account on no-ip.com but it still dosen't solve the problem.. do I have to do tunneling or something like that? do point me to the right direction please! =)

i have no problems connecting when i'm in the same network though.. my ubuntu is running openssh sever..

I've tried searchin here and googling but i can't seem to find any answers. Any help is greatly appreciated! Thanks!

---

### Post by firdooze on 2007-05-11
oh yeah just to add... it seems that most of the guides are made for terminals in the same network.. i.e use ip address like 192.168.1.99 

i need something that works with external ip address (if this is the term used LOL)

---

### Post by mlentink on 2007-05-11
Did you enable port-forwarding in your router?

---

### Post by hartz on 2007-05-11
fidooze, I successfully use no-ip.com to provide a name and connect using putty from my cell-phone to my linux box.  (My Nokia 9300 cellphone has got a full keyboard - I've reviewed it on my blog)

Besides no-ip and getting an ssh-server installed, I also needed to configure my Firewall/router to forward the incoming connection to my linux system.

Being paranoid, I selected a random high port number, which I have configured on my router to be forwarded to port nr 22 on my linux system.  (yes I know - Security-through-obscurity-is-no-security, but this is just one more layer to discourage scripted attacks)

The exact details on how to do this is specific to the router make and sometimes even model number.  There are some very good guides on the internet on how to configure incoming port forwarding, something you also often need to do in otder to get your e-donkey download client, IM-client, VoIP client, and online games to work.

On my specific router the page for forwarding incoming connections is somewhat confusingly called "virtual server configuration".  Look in your manual for this, or Google for *forwarding incoming connections* and the make and model of your router.

---

### Post by firdooze on 2007-05-11
i've forwarded port 22 for my ubuntu box.. 
TCP: 22 & UDP: 22 :: are these settings correct?? 

do i need to forward any other ports besides port 22? 
i don't think my linux box has a firewall because I didn't install any

---

### Post by firdooze on 2007-05-11
btw, when i want to connect from my windows ssh, under the option server I should enter something like ::: abcdef.myserver.biz  ?? this is what i obtained from no-ip.com

---

### Post by firdooze on 2007-05-11
hey i got it up!! i used the ip (xxx.xxx.x.xxx) instead of the abcdef.myserver.biz
well, i'm not sure whether this ip will change.... hope i'm connecting correctly..

hell i even managed to get vnc to work! haha.. typing this on my laptop through my ubuntu server hahaA!

---

### Post by totalnub on 2007-05-11
this looks like the same deal that i want to do....problem arises when i try and figure out what ip to type in to putty. any ideas? i am fowarding port 22 to my ubuntu box.

---

### Post by ninjaprawn on 2007-05-11
im having a similiar problem, but mines a little more complicated!

i can get the ssh tunnel working, but i connect to my linux box on port 443. this is because my proxy from the xp machines doesnt allow any traffic except port 443 and 80!

i then need to set vnc to go down the tunnel to port 443 to connect to the vnc server!

how??

---

### Post by firdooze on 2007-05-13
> **totalnub said:**
> this looks like the same deal that i want to do....problem arises when i try and figure out what ip to type in to putty. any ideas? i am fowarding port 22 to my ubuntu box.

you might wanna register with a free account on [no-ip.com]("http://www.no-ip.com") (if you don't get static IP from your ISP)
then type in the hostname that you have registered with them into putty or ssh.. then, compile and run the IP update client from their download section into your ubuntu.. now your the hostname will point to your external IP address and you can access your box from outside! =)

hope it works for you! gd luck!

---

### Post by firdooze on 2007-05-13
> **ninjaprawn said:**
> im having a similiar problem, but mines a little more complicated!

i can get the ssh tunnel working, but i connect to my linux box on port 443. this is because my proxy from the xp machines doesnt allow any traffic except port 443 and 80!

i then need to set vnc to go down the tunnel to port 443 to connect to the vnc server!


how??

if i'm not wrong you can assign a different port for vnc to work... maybe someone else can offer suggestions.. bump! :lolflag:

---

