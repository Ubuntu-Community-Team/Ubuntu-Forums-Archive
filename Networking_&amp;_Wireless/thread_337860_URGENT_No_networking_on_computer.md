---
title: "URGENT: No networking on computer"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Brian Boyko on 2007-01-13
I would like you to help me with my networking problem.

I am installing Ubuntu on a new computer, with an ASUS P5B-E Motherboard.  

The network adapter, (on the motherboard) does not work either in LiveCD or with a fresh Ubuntu install.  

I'm on a deadline (12:01 AM January 15) so please CC your responses to brian.boyko (at) gmail (dot) com

Thank you.

Brian Boyko.

---

### Post by mojoman on 2007-01-13
Give some more info. What does ifconfig give for output?
/Mojoman

---

### Post by Brian Boyko on 2007-01-13
Sorry Mojoman.  Right now installing Windows to see if it's a problem on the hardware layer.  

Will do so as soon as I can.

---

### Post by Brian Boyko on 2007-01-13
Here's the skinny: 

1) I've installed a small Windows partition and I can get the Internet working on that. It's not the hardware, in other words.

2) I'm downloading Feisty Fawn and I'm going to see if Feisty's live CD picks up the network interface. 

3) Perhaps NDISwrapper could help here (even though it's meant for wifi cards), but the only way to get it is via the net - I have a flash drive, but don't know what to download.

---

### Post by mojoman on 2007-01-14
My advice is to hold the ndisrapper, at least for now (though I know very little about these, i've never needed to use it).

This is a built-in network on a, I think, common motherboard and you should be able to get this to work without too much hassle. 

I might be stating the obvious here but under system - adminstration - networking (in the Gnome menu) you should see the built-in network (probably as eth0). You'll need to be logged in with your administrator login in order to see this on the menu. Are these settings corrects and is it acvtivated?

/Mojoman

---

### Post by Brian Boyko on 2007-01-14
Mojoman: 

In System-Administration it would not even detect the network card (only a modem, which I hesitate to add, I don't have.)

I got some help via the Ubuntu chatroom on freenode and they pointed out that that particular network interface wasn't supported, there was a driver but it was highly experimental and I would need to recompile my kernel. 

I decided to drive to Wally World (it was after midnight) and just pick up a 10/100 Ethernet card.  I picked up the only model they had, plugged it in, and it worked.  

Solved the problem with $15 bucks.

---

### Post by mojoman on 2007-01-14
> **Brian Boyko said:**
> Mojoman: 

In System-Administration it would not even detect the network card (only a modem, which I hesitate to add, I don't have.)

I got some help via the Ubuntu chatroom on freenode and they pointed out that that particular network interface wasn't supported, there was a driver but it was highly experimental and I would need to recompile my kernel. 

I decided to drive to Wally World (it was after midnight) and just pick up a 10/100 Ethernet card.  I picked up the only model they had, plugged it in, and it worked.  

Solved the problem with $15 bucks.

$15 for a ethernet card in the middle of the night. You just gotta love America :D

---

### Post by Brian Boyko on 2007-01-14
Actually, funny you mention that.  One of the reasons I'm okay with the 15 dollar card is because it's 10/100 base T, not gigabit Ethernet.  If I was living in Europe or Asia, I probably wouldn't have found that an acceptable solution - it's just that broadband speeds are so slow here Gigabit Ethernet is overkill.

---

