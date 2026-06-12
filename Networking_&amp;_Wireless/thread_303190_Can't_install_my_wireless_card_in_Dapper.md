---
title: "Can't install my wireless card in Dapper"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by HokeyFry on 2006-11-19
Hi. I have a Belkin 54g wireless notebook card, and i am having a heck of a time trying to get it to install in Dapper. I have had this same card working on my previous laptop, however, that one had a breezy install on it. This is the walkthrough i wrote and followed for every time ive ever installed wireless on a PC or laptop for anybody

[http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

and i have never had any issues with it ever. Is there something special or extra you have to do in Dapper, because I am really excited to finally have a decent computer that i can run linux on, and it would be a huge disappointment to have to be at the mercy of wires and such.


Thanks in advance for any help.

---

### Post by trubblemaker on 2006-11-19
Yeah it seems that the edgy repositories aren't 'all that' for ndiswrapper.  I've had alot of success getting people up and running building from source.  check the "from source" in my signature.  
It's going to be easy for you 'cause you seem to know howto use ndiswrapper, 
the from source install isn't really that hard, 
check it out.

Make sure to erradicate all instances of Ndiswrapper before installing from source. (no need to change your interfaces file)

---

### Post by HokeyFry on 2006-11-20
alright ill try doing it from source, but in the meantime how is it that ndiswrapper works perfectly fine in earlier releases but not in dapper or edgy? just a question, though, it doesnt need answering

---

### Post by trubblemaker on 2006-11-20
well here's the trick it works fine in both Given:
   There still isn't a native driver for your nic that they made default with kernel.  (this I think was a bad choice, there should be an attempt to see if ndiswrapper is present and warn you of possible "bad things" that could happen)

or

   You have a fresh install and not an upgrade. This is reportedly a good time it's only people upgrading with headaches.

---

### Post by HokeyFry on 2006-11-20
oh i see, i just finished upgrading my laptop like less than 24 hours ago


ill try doing your method once i get home from school and hope to god it works


man and to think i upgraded this thing cause i was too lazy to wait two hours for the CD image to download lol

---

### Post by HokeyFry on 2006-11-20
HAHA YES!

It worked I now have an excellent laptop with linux and wireless internet!!!


thanks trubblemaker, your walkthrough was very helpful, i owe you one

*EDIT* I don't know if this is normal but i had to put 'ndiswrapper' at the bottom of '/etc/modules' and reboot the laptop to get it to work, just so you know cause that part wasnt in the walkthrough

---

### Post by trubblemaker on 2006-11-20
not normal but i'll add it to the post thanks.

---

