---
title: "Help with turning on wireless RF"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by macmichael01 on 2007-01-21
anyone know the command to turn on your wireless cards RF.  Drivers and everything are installed for me but there is no RF. One my last ubuntu install I thought that there was a command to turn this on. or maybe a command to tell to activate it when ubuntu starts. any suggestions?

---

### Post by ingo on 2007-01-23
sorry for the dumb question, but what does RF stand for?

---

### Post by macmichael01 on 2007-02-03
Stands for Radio Frequency

---

### Post by ingo on 2007-02-04
Thanks for your answer, but I'm still in the dark as to what you want to achieve. 

Can you connect to the network?

---

### Post by Johan! on 2007-02-04
Please tell us what kind of hardware you use.

If you use an Acer laptop, search for acer-acpi or acerhk.

---

### Post by macmichael01 on 2007-04-23
wow I forgot that I started this discussion.  Well I have the typical that everyone seems to have the Linksys broadcom 4318  wireless 54g. I remember reading somewhere that there was a way to turn on the wireless card b/c when you look at the iwconfig file it shows no packets being sent or received. On the card itself, it shows that the power light is on but the link light is not.  I found that by typing these commands in,

sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

 it seems to turn on the wireless card and then it finally does what it is supposed to do but when you restart its back to no link light again.  I also remember reading somewhere that there is some command that you might have to enter when the OS loads so that it knows to turn on the card.  I hope this all makes sense.

I recently upgraded to Ubuntu 7.04 and I am having the same problems. any suggestions??

---

### Post by webdr on 2007-04-23
hmmm, I'm on Edgy, but this may work for Fiesty as well, not sure.
Check this thread:
[http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless](http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless)
-RacerX

---

### Post by macmichael01 on 2007-04-23
Thanks I shall give it a try

---

