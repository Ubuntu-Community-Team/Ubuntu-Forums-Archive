---
title: "Broadcom BCM94311MCG will not work with ndiswrapper or fwcutter"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by drunkmatador on 2008-05-06
I have been trying to get wifi running on my HP dv2000 notebook for a couple months with little to no success. The newest distro, Hardy Heron 8.04, is installed and I have tried using each method of getting my Broadcom BCM94311 working (ndiswrapper and b43-fwcutter, each separately). The only success I had was the other night when for some reason it started working.. but only for about an hour at a time and sometimes not connecting at all.

The blue light on the front of my laptop turns on, and it will say it's connected to a network (either one, all unsecured), but I cannot connect to any websites. Could it just be a DNS problem? 

Attached are some outputs from (I think) all the helpful commands. Let me know if there is anything I'm missing.


(dmesg was extremely long so i couldn't get the first part of it. if you know of a way that i can, let me know and i will post that as well.)



If you could please help it would be appreciated. Right now I don't have a home network set up, only a couple computers that are each connected to shared wifi at my apartments. So I'm limited to only using my desktop as is, and this computer through a crossover cable hooked between them.

---

### Post by viralbug on 2008-05-06
hey i have an hp pavillion dv2000 laptop with the same broadcom bcm94311mcg minipci. can you please explain how you got it working? i know hou havent been able to get it fully working, but in my case, the blue light wont glow, it just shows a red light indicating that it is disabled.
any kind of help would be appreciated. im a bit new to ubuntu.

---

### Post by drunkmatador on 2008-05-06
Well I basically followed one tutorial instructing me on how to get the card working through ndiswrapper.. I'm also pretty new to Ubuntu and Linux in general so it would be best for you to find that probably.

First you should probably run lspci and find out what exact card you have. I read that dv2000 notebooks can have many different kinds of cards in them. One of the things that comes up should say which Broadcom chip it is (if it even is broadcom, but i think it probably will be).

So open a terminal and type lspci and then either post here or find out what kind you have.

---

### Post by viralbug on 2008-05-06
hey i got it working! :D
i have dv2000 with broadcom bcm94311mcg, same as yours.
heres a [guide]("http://ubuntuforums.org/showthread.php?t=769990&highlight=bcm43xx-fwcutter")
i followed exactly those instructions and its now working perfectly fine. try it. hope itll work for you too. :)

---

### Post by mthmulders on 2008-05-06
I think I have the same hardware, but I don't have my laptop at hand right now.

The trick is that the b43 module (if I'm not mistaken) is loaded too early. You should blacklist it. Further, there is a script that loads the ndiswrapper module. Take a look [here]("http://ubuntuforums.org/showthread.php?t=769990&highlight=broadcom+ndiswrapper+b43").

---

### Post by drunkmatador on 2008-05-06
Good for you! Well what version of Ubuntu are you running? And had you tried to use ndiswrapper or anything previously? I'm thinking that might be part of my problem and I should just reinstall but I really hate to at this point.

---

### Post by mthmulders on 2008-05-06
I'm running Kubuntu 8.04. It's an upgrade from Kubuntu 7.10, where I have successfully used ndiswrapper as well. The firmware has never worked for me.

---

### Post by drunkmatador on 2008-05-06
Sorry, that reply was meant to go to the person above you, whoops! Thanks for your information though I'll make sure it's blacklisted correctly.. but I believe that it is.

---

### Post by mthmulders on 2008-05-06
Great; let me know if it worked for you ;)

---

### Post by drunkmatador on 2008-05-06
Well, I followed the post that helped viralbug, to the T (meaning exactly), and it turned out to work! I'm very happy that I got it working and with what seems like the better option of the two: ndiswrapper, as opposed to fwcutter.

---

