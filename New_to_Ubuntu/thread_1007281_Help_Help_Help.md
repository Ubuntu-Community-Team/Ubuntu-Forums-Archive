---
title: "Help Help Help"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Oliver.BS on 2008-12-10
Hi all I think I have nearly cracked setting up a network which I can acess from home I just need your help to finish it off

I am trying to acess me dell laptop at home running linux which is connected to my router and I am trying to acess it using a Mac. 

I have signed up to No-iP and one I get home I will add a host which is my dell laptop add the IP adress and the Free DNS name. 

Once I have done this what do I need to do to my router and what other software do I need on both Mac and Linux machine at home ? 

If you know of a guide of how to set up this please let me know as I have been trying to do it for days now please.

---

### Post by Titan8990 on 2008-12-10
You will need to forward the ports on your router depending on what you are trying to do. Your topic title and question lack description. Saying that you are trying to "access" your laptop couldn't be any more vague. What is it that you want to access? 


If you are say, trying to ssh to your linux box, you would need to forward port 22 on your router to your server's IP address.

---

### Post by Oliver.BS on 2008-12-10
> **Titan8990 said:**
> You will need to forward the ports on your router depending on what you are trying to do. Your topic title and question lack description. Saying that you are trying to "access" your laptop couldn't be any more vague. What is it that you want to access? 


If you are say, trying to ssh to your linux box, you would need to forward port 22 on your router to your server's IP address.

I am just trying to acess it so I can get files run apps etc I want my laptop to ask a storage unit.

Once I have a DNS set up what software do I need on my mac to connect to my linix and what software do I need on my linux machine.

---

### Post by Titan8990 on 2008-12-10
Well, you have tons of options. My recommendation is ssh/scp. 


To install ssh/scp server on Ubuntu:


sudo apt-get install ssh-server



The ssh client is installed by default on the MAC so you don't have to do anything other than learn how the scp syntax goes (took me a bit to get it down right).


You should have a look at the following man pages:


man scp

man ssh


You will need to forward port 22 to your server.


Edit: MAC OS X is also a UNIX based OS so the functionality for the two to interact are built-in.

---

