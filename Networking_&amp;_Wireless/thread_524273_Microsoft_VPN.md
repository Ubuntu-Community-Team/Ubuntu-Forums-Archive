---
title: "Microsoft VPN"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by bert_pereira on 2007-08-12
Hi Guys, 

I have installed Ubuntu 7.04 and the only issue i am having is with the VPN i need for internet connectivity - I understand from the threads that i read that i need to install the pptp plugin for Network manager, however, i would then need to switch back and forth bw Ubuntu and XP to get the files - Is there a way i can download a package containing all the dependencies for the installation of this plugin??

Bert

---

### Post by steveneddy on 2007-08-12
You don't need VPN for internet connectivity.

What type of connection do you have?

DSL, dial up, cable....

---

### Post by bert_pereira on 2007-08-13
I am using an ISP that uses VPN - I have a dialer in windows which i use to connect - Here are the details of the VPN connection: 

Device Name: WAN miniport (PPTP)
Device Type: VPN
Server Type: PPP
Transports: TCP/IP
Authentication: MS CHAP V2
Compression: MPPC
PPP Multilink framing: Off
Server IP Address: 125.209.124.1
Client IP Address: 125.209.124.52

I have managed to install the pptp plugin for Network manager but now i keep getting the error 'Incorrect username or password'

Thanks in advance

Bert

---

### Post by jrusso2 on 2007-08-13
Thats a pretty weird setup.  I don't have a clue how to do that in Linux.  I mean MS Chap authentication.  What ISP is that?

---

### Post by bert_pereira on 2007-08-13
Well i'm in Pakistan and the ISP is ConnectPK

Bert

---

### Post by bert_pereira on 2007-08-13
Does anyone have an idea??

---

### Post by snmahmood on 2007-08-14
I am also a user of that cable network service i also need help on it can someone help us

---

### Post by imdano on 2007-08-14
[http://pptpclient.sourceforge.net/](http://pptpclient.sourceforge.net/)

It's not the easiest thing in the world to get working, but the support section of the site it excellent and will help you get everything set up.  If you use NetworkManager, you can a plugin that will integrate it in to the GUI that might make it a little easier to use.

---

### Post by afzalnaj on 2007-08-27
i am also a user of that service....have been searching on this forum...so far no solution...please help us!! there r plenty of ppl using this service who want to migrate to linux but can't due to this problem

---

### Post by steve.horsley on 2007-08-27
I have succesfully connected to an MS VPN using the instructions (manual configuration) here:
[http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-debian.phtml#configure_by_hand)

But there is one thing I don't understand with your setup - if you can access 125.209.124.1, then surely, you already have internet access?

---

### Post by snmahmood on 2007-10-03
I could access the site on lan of the isp but i could not connect internet.Also when i try to write  /etc/ppp/chap-secrets  on these files it says these files r protected & cannot be written plz tell in detail as i m a beginner & trying to migrate to ubuntu

---

