---
title: "PPPoE"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by miezatb on 2008-03-04
I have 2 operating systems: win xp sp2 and Ubunt 7.10 which I'm experimenting with lately, I'm trying to learn it. I can't seem to configure my internet connection

in xp I have to 2 connections for the internet, one is LAN and the other one is Broadband (PPPoE) which requiers user name and password.

Ubuntu sees them both but I can't configure the pppoe, it asks for a phone number and prefix wich I don't know and don't need in xp and without those I can't press ok. if I type something random, it doesn't work

what to do?

---

### Post by erginemr on 2008-03-04
What is the brand of your broadband modem? Can you please find it in Google and post here the link?

And how do you connect it to your computer (via USB or via Ethernet Card)?

---

### Post by edonia on 2008-03-04
Did you use the pppoeconf tool for setting up a connection?

---

### Post by miezatb on 2008-03-06
> **erginemr said:**
> What is the brand of your broadband modem? Can you please find it in Google and post here the link?

And how do you connect it to your computer (via USB or via Ethernet Card)?

I don't acctually have e modem in the house, the internet comes in my house through a simple network cable on LAN

---

### Post by miezatb on 2008-03-06
> **edonia said:**
> Did you use the pppoeconf tool for setting up a connection?

I tryied from the menus from ubuntu, if that is an utility like command prompt well tell me how will I find it

---

### Post by ulver on 2008-03-06
Click on menu-> accessories-> terminal
Than type in it ```
pppoeconf
```
Now just enter the information that your ISP has provided.
With enter you select, with tab you skip fields.

---

### Post by edonia on 2008-03-06
first  install it. just type in a terminal: 
sudo apt-get install pppoeconf

then run the program in a terminal, like descriped in the post bevore.

I guess, your pppoe login will be fine after that

---

### Post by miezatb on 2008-03-06
I finally done it ! Now I'm posting from ubuntu :) 

I found "terminal" I typed pppoe, pppoeconf and nothing, it told me to root. I didn't know how and still don't. I tryed many commands from help and after many comands later I typed sudo pppoeconf and that did it. a nice guied how  to configure and bingo baby

---

