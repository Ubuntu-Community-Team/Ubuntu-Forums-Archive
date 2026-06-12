---
title: "Printer help"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by kdunn on 2011-04-04
I currently have a ubuntu 10.10 desktop basically set-up as a print box. The printer I have is a HP Photosmart 2600 series and it works fine when used directly from the ubuntu desktop. 

The problem I am having is my laptop is running windows 7 now and I just can't seem to work out how to connect to this printer through the ubuntu box. I have trolled through several guides to no avail. Can someone either supply me with a guide or link me to one that will work? Please know that I am a noob still at ubuntu but I'm learning. 

To complicate this just slightly I also have a mac laptop and it would be nice if I could also print from it as well. I haven't been able to find any guides specifically for 10.10 and would really appreciate the help.


Thanks in advance for the help.

---

### Post by pi3.1415926535... on 2011-04-04
It would be helpful to know what the type of set-up is, and where in the process the problem is, for example, can your laptop find the printer but not connect to it?

---

### Post by jtarin on 2011-04-04
See if this [post]("http://ubuntuforums.org/showthread.php?t=1339956") will give you some information to understand the process....then post back with any problems you encounter.

---

### Post by kdunn on 2011-04-04
Sorry for being vague. The windows 7 laptop doesn't see ubuntu box. neither does the mac laptop which I though was odd. As far as basics the printer is set to be shared through the printing menu. So my main problem is getting all of them to see eachother.

---

### Post by Mark Phelps on 2011-04-05
Hate to say it, but the simplest solution may be to purchase a Print Server, hook the printer to that, and access is from all your machines over the network.

---

### Post by walt.smith1960 on 2011-04-05
> **Mark Phelps said:**
> Hate to say it, but the simplest solution may be to purchase a Print Server, hook the printer to that, and access is from all your machines over the network.

I agree with Mark except that according to HP's web site, the HP Photsmart2600 is already network enabled.  If that is the case, I'll bet you could plug a cable from your router to the printer, go to printing in System -> Administration -> Printing.  Click on the "add" button and follow the prompts. I'll bet the printer is found and software is installed. I don't have that printer so I don't know if you have to select networking on the printer or if it sees a network connection and configures itself.  It might help to go to synaptic and add the HPLIP package to help with printer administration.

---

### Post by Sef on 2011-04-05
Could you describe the steps that you did in order to try and get your 10.10 to act as a print server?

Have you read [Network Printing with Ubuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")?

---

