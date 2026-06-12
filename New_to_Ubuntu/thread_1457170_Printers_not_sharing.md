---
title: "Printers not sharing"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Slownis on 2010-04-18
My ubuntu machine acts as a print server and a file server for two windows laptops and a Mac laptop.  When I go into 'Printing', I have the printer enabled and shared.  Under Access control I have 'Allow printing for everyone except these users:'.  On Server Settings, I have 'Publish shared printers connected to this system' checked.  However, I'm unable to see the printer on the network.  Please help!

Edit:  I did 'Connect' on the server menu, and now I'm able to see the printer on the network from one of my windows xp laptops, and install it by using downloaded drivers, but then it says 'Access Denied, Unable to Connect' after it is installed.

Edit#2:  But then I restarted the Ubuntu Machine and the printer doesn't show on the network again.  I would like to not have to do the 'connect' for the print server every time I have to restart the Ubuntu machine'

---

### Post by paydaydaddy on 2010-04-18
I don't have my printer set up the way you do so I can't directly address your problem. I do have a couple of suggestions though. 
Have you see the wiki here:

[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

Also, check to make sure that you don't have a firewall interfering. I had to enter a range of IP addresses to get my printer (shared on windows) to consistently work.

---

### Post by Sef on 2010-04-18
1) What version of Ubuntu are you using?

2) What are the make and models of your printers?

---

### Post by Slownis on 2010-04-18
> **Sef said:**
> 1) What version of Ubuntu are you using?

2) What are the make and models of your printers?

I have Ubuntu V9.10 installed.  

I have 3 printers, a Brother HL-5140 laser printer (my workhorse), an HP PSC 1210xi all in one printer (for scanning and light color work), and an Epson Stylus Photo R280 (for photos).  Right now I'm just trying to get the Brother working.  It has worked with this setup in the past but now its not.  The HP I have never been able to network due to lack of an *.INF driver.  I recently removed samba and reinstalled it, and I think something got messed up in the process.

---

### Post by Slownis on 2010-04-24
Any help on this?

---

### Post by Scunnered on 2010-04-25
I have my printer connected by USB to my Ubuntu system and my partner accesses it from her XP laptop.  From memory when I setup her system I had to disable my firewall and opt for Microsofts one before it would work properly.  Looking on her system I note that the printer is set as default and is shown as Stylus-Photo-R265 on IP address :631.  I had a bit of bother initially with MS over the printer name but eventually it took.

Not too sure if this assists  but hope so

---

### Post by Slownis on 2010-04-25
Don't know exactly what I did, but its working now.  On the MAC, I deleted all the keys in Keychain Access and set it up again, and when I went to print something it asked for creds and I put in my main login info for the Ubuntu machine.  On my XP computer I just added it like normal.  Not sure why it worked this time.  Thanks guys.

---

