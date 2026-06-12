---
title: "Wireless and Buffalo Router"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by kenagleka on 2007-10-02
Wireless and Buffalo Router
I have a Buffalo router (WHR G54S) that works with XP but I cannot get a working wireless connection with Feisty 7.04 on my laptop.  Buffalo tech. does not support Linux, at least that is what I heard from the tech. guy.  My ISP does not support Linux so I strike out there.  
     Most certainly the problem is my ignorance.  I do not have a handle on the wireless process.  I  do not know what settings to use when I go to System Administration, Network and am confused by Buffalo's AOSS button which is supposed to make the wireless connection automatically.  
     I am most enthusiastic about Ubuntu.  I have had no bad surprises and lots of good ones in my 3 month experience.  Hopefully some more Linux adept user can help.  KEngleka

---

### Post by jdids on 2007-10-17
I ran into the same problem. I tried running Wine to get Buffalo Client Manager to work, but it didn't work at all. When I was about to give up and change my wireless router settings, this method popped up in my head, and eventually worked flawlessly.

Note: I used this method on Gusty Gibbon 7.10 Beta

Can connect with XP using AOSS? If so, here's a solution you can use without touching the AOSS button on your router and messing up your settings and connection.

- Using Ubuntu, connect your computer to the router with a internet cable. Then, when connected, open a web browser and type "192.168.11.1" in the address bar.

- When that is done loading, there should be a wireless group at the bottom right hand of the screen, and an "AOSS Setting Information" button. Press the button.

- If you still have a valid connection via AOSS and your XP machine, then there should be some dialog called "AOSS Client Information," and a list of the current wireless cards configured to run AOSS. Below that, there is a dialog for "Current Encryption Information 802.11g," and a list of encryptions used (Ex: AES, TKIP, WEP128...). After one of those, there should be a message like "AES (This is used now)" or"WEP128 (This is used now)" ... and so forth. 

- What you want to do now is try to connect to your AOSS network WITHOUT pressing the AOSS button. When asked for the key, enter the encryption key that is given under the connection type with (This is used now) after it.

Now you should be connecting to the AOSS network. Hopefully this worked out for you!

---

