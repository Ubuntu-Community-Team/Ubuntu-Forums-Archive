---
title: "Cant find wireless HPzv5000"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Elotero on 2007-06-19
I have an HP ZV5000 ... kind of old but cool... i think my wireless card is an IntelPro... There is a Wireless on/off button but the button wont turn on.. this may be why i get no signal. I keep pushing the button but it doesnt turn on.  I have been able to use wireless very easy when i was using Windows. Dont know why it shut off when i switched to ubuntu 7.04... can anyone give any help?? im researching the web and cant find anything to get past step one of finding a connection.. any help is greatly appreciated.. thanks


E

---

### Post by Elotero on 2007-06-19
How do I find out what kind of card i have in Ubuntu anyway???

---

### Post by Bachstelze on 2007-06-19
```
lspci
```

---

### Post by Elotero on 2007-06-19
So cool thank you... Broadcom BCM4306 802.11/g wireless lan.. and i screwed my self even more..  ibeenfollowing this tutorial and now when i go up to the network icon in the corner i dont even get the option to choose wireless.. only wired and dial up.. thank you so much.. 

ATI radeon rs300

---

### Post by Elotero on 2007-06-19
i did the scan in the terminal and it says "interface doesnt support scanning".. before that it said no wireless devices found.. thats not cool...

---

### Post by mattplank on 2007-06-19
I am having EXACTLY the same problem. Same laptop, same card. 
Also, I'm a total newbie. So any help would be great. Especially if it was written for a newbie. Who knows nothing at all.
Thanks.

---

### Post by Ayuthia on 2007-06-20
If you have a wired connection, you can try:

sudo apt-get install bcm43xx-fwcutter

From what I can tell, this method should work for bcm4306.

---

### Post by Elotero on 2007-06-20
> **Ayuthia said:**
> If you have a wired connection, you can try:

sudo apt-get install bcm43xx-fwcutter

From what I can tell, this method should work for bcm4306.

I will try this as soon as i get home.. thank you very much for the help.. i will let you kow how it goes... i will finally get wireless working!!!!!

---

### Post by Elotero on 2007-06-20
> **Ayuthia said:**
> If you have a wired connection, you can try:

sudo apt-get install bcm43xx-fwcutter

From what I can tell, this method should work for bcm4306.


i get this error in the terminal:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


please help...

---

### Post by Ayuthia on 2007-06-21
This generally means that you have another program (synaptic, add/remove, update manager) open.  You just need to close them and that should fix it.

---

