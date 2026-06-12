---
title: "After updating wireless internet stoped wortking"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-02-08
I updated Ubuntu 8.10 the other day, It must have installed about 200updates. After updating it asked to restart so i did and when i started it back my wireless internet was gone, i have no clue how to fix this. any help?

---

### Post by lkraemer on 2009-02-08
You can select a previous Kernel in the grub menu to get you back online
while you post more information.

You probably got a Kernel upgrade and that disabled your wireless.
You are going to have to post the drivers or method that you used
to get your wifi working.  Did you use madwifi or what.

Open a terminal window and type
lspci -v|less

then post what it returns.
Also:

lshw -C network
iwconfig
iwlist scanning

 
lkraemer

---

### Post by Rave Gloves on 2009-02-14
Sorry i havent replyed to this thread in a bit, but i will get the output up tonight and see if you dudes can help me.

---

### Post by Crafty Kisses on 2009-02-14
Please post those results stated above and by any chance do you know what kind of wireless card you have?

---

### Post by growlf65 on 2009-02-15
I encountered the same thing when I installed xubuntu on my Thinkpad.  My solution was to reinstall (no biggie since I didn't have anything to lose), and when it wanted to do the 200+ updates I removed the update for Ubuntu's wireless manager and installed wicd.  It connected right up and I haven't had a problem since.

---

