---
title: "Simple Network Monitoring"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by hayden92 on 2010-08-24
Hey guys,

  I have a small network at home, which all of my family uses. We've also got some boarders staying in our house at the moment.

  I've been having some issues with people getting to sites that they shouldn't be (torrenting, illegal, etc). I've tried talking to them about it, to no avail. I'm wondering if there's a program that will print up a list of computers that are connected to the network, and the website (or the IP of the website) that they are currently accessing. I don't mind if it's a CLI program.

  Thanks for any suggestions that you might have,

Hayden

---

### Post by arochester on 2010-08-24
Not directly an answer to your question, but you can filter at the level of your router rather than computers and apply filtering to all computers on your network. See: [http://www.opendns.com/familyshield](http://www.opendns.com/familyshield)

---

### Post by warfacegod on 2010-08-24
```
sudo apt-get install nmap
```

May be useful to you. If you like a GUI nmapsi4 should be installed as well.

---

### Post by tom.swartz07 on 2010-08-24
As arochester mentioned, you could outright block access to whatever sites you wish by using OpenDNS. I used it on my home network back in High School to keep myself off of Facebook during finals week. haha.


Its not too hard to set up, and (if I remember correctly) you could block sites for individual computers. 
If OpenDNS doesnt support that, your router might support that feature. Poke around with the config page on your router to find out.

---

### Post by QLee on 2010-08-24
[QUOTE=hayden92]
  I've been having some issues with people getting to sites that they shouldn't be (torrenting, illegal, etc). I've tried talking to them about it, to no avail.[/QUOTE]
It's your network, so if they won't play by network rules, deny them access, simple and also fair, they were warned.


 [QUOTE=hayden92]I'm wondering if there's a program that will print up a list of computers that are connected to the network, and the website (or the IP of the website) that they are currently accessing. I don't mind if it's a CLI program.[/QUOTE]

Your router should have that information on a page already.

---

### Post by hayden92 on 2010-08-25
> **QLee said:**
> Your router should have that information on a page already.

I've looked for something like that, but I can't find it. What would it be listed under?

---

### Post by LiquidMeson on 2010-08-25
You could see if your router supports ddwrt.

---

### Post by anewguy on 2010-08-26
> **hayden92 said:**
> I've looked for something like that, but I can't find it. What would it be listed under?

What brand and model is the router?

---

### Post by hayden92 on 2010-08-27
It's a Billion Router, BiPAC 7401VGP

---

### Post by anewguy on 2010-08-28
Wow!  Wish I could help with that, but I haven't ever heard of that router (perhaps it's because I'm in the U.S. and you're in Australia?).  Sorry I can't help on that!

Dave ;)

---

### Post by hayden92 on 2010-08-28
No worries Dave, thanks anyway :)

I've been fiddling around with 'nmap' and so far it's looking good. Thanks for the suggestions everyone, I'll be sorting my network out in no time!

Hayden

---

