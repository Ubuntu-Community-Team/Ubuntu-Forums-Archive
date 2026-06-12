---
title: "Problems with Broadcom 4303 wireless card in Gutsy"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by angry-broadcom-user on 2007-10-21
I have a Broadcom 4303 wireless card in a Compaq Presario R3000, and so far have had no luck in connecting to my wireless network.

I can see my wireless network when clicking on the network icon, but when entering the wireless (WPA) key the connection seems to freeze and stops. When I put the mouse over it, it stops at 'Waiting for Network Key for the wireless network <networkname>'. I know the key is correct, so that can't be the problem.

I have followed numerous different forums using ndiswrapper, fwcutter and the built-in configuration in Gutsy and have not been able to connect using any of the methods. I am hoping that somebody can help me here.

Thanks

---

### Post by phillipgi on 2007-10-24
I have exactly the same problem. I've got a Toshiba Satellite Pro A10 with an unnamed wireless card (although if memory serves correctly, it's based on a Broadcom chipset).

When I try to connect, I get the "Waiting for key from network" message, then the whole system freezes. It won't respond to anything, I have to cold reboot it to continue. Onboard network works fine.

I'm running Gutsy (fresh install), and the wireless worked fine in Fiesty.

---

### Post by angry-broadcom-user on 2007-10-24
:) I am glad I'm not on my own - lets hope someone knows what to do...

---

### Post by kopchickm on 2007-10-26
Same problem here...total freeze after trying to use my network card, no matter what the security settings are.

---

### Post by alexbone on 2007-10-26
i'm having exactly the same problem.. help please

---

### Post by mschap on 2007-10-26
I have the same problem.  However, intermittently I can connect and have no problem, but 5 minutes in it will drop the connection completely and not reconnect.  I can connect at the network at work and it is patchy in connecting though the signal strength is great and worked beautifully on Fiesty. 

In addition, I cannot connect at home at all.  I have changed the key on the router and still no luck.  Again, under fiesty no problem.

Hopefully, someone does have an answer to this.

By the way the scanner support is now fixed and I am  very thankful for that.

---

### Post by mschap on 2007-10-27
Has anyone found a solution to this issue?

---

### Post by angry-broadcom-user on 2007-11-01
No - I hope someone knows what to do... :(

---

### Post by angry-broadcom-user on 2007-11-04
bump

---

### Post by racin on 2007-11-04
I have the same problem also. "However, intermittently I can connect and have no problem, but 5 minutes in it will drop the connection completely and not reconnect. I can connect at the network at work and it is patchy in connecting though the signal strength is great and worked beautifully on Fiesty."

It seems to be a DNS issue if you configure your network manually and put in your ISP's DNS server instead of your router address it works better.

---

### Post by angry-broadcom-user on 2007-12-06
:(
Anyone?

---

### Post by Lorac1949 on 2007-12-06
I also have one of the 43xx wireless cards (in a Dell Inspiron 1520) and have followed the instructions from 2 different posts.  One set of instructions at least got me to the point where I can *see* my network connection (and the neighbors').  However, once the passcode is entered it goes nowhere.  Sometimes it shows the signal strength at 98% and a few minutes later it goes to zip!  Waz up!  Wireless works beautifully in Windows.  Go figure.  Can someone help?

---

### Post by jan quark on 2007-12-20
same problems here, have 43xx firmware installed and after few minutes of fast internet connection inet slows down and then stops...

so many people have this problem why is there no solution to it. I know that the firmware is restricted and must be re-engineered but nevertheless ...:(

---

### Post by jeetfeet on 2007-12-30
Same problem here. I have the HP zv6000 laptop with AMD64 processor. The wireless chipset is a Broadcom 4306 - I installed Gutsy and followed the online help for setting up the restricted drivers for the Wireless and ATI Graphics cards. Everything seemed OK at first but then I began to notice that if I accessed the network immediately after authenticating to my AP the machine would totally freeze. I mean locked up tighter than a drum - Caps/Num lock lights won't respond. This happens repeatedly like clock work. I can launch XP Pro from a different HD with no probelms. I also can get the Gutsy to lockup if I start a virtual session in VMWare and access the network. Total lockup. I'm a EE/CS and do a lot of firmware development and this definitely looks like a device driver or driver interface issue. Ubuntu experts please help!!! :confused:

---

### Post by kevdog on 2007-12-31
Use ndiswrapper instead of the restricted driver.  The restricted driver although it technically works, is very buggy and leads to a lot of disconnects, or unstable connections.

---

