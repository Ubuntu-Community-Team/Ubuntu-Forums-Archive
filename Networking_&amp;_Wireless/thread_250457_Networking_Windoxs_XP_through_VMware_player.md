---
title: "Networking Windoxs XP through VMware player"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by etotehpii on 2006-09-04
I'm sorry if a question has already been asked like this but I couldn't find exactly what I was looking for when I searched the forums.

I just recently got windows xp to work with VMware player and I am totally clueless as how to enable windows xp to connect to the internet.  I've read that all I need to do is set up a network between ubuntu and windows xp home.  However, I do not know how to set this up or if this is the correct solution.
I use wireless internet and my ra0 is configured correctly.  This has been a lot of fun tinkering with this so far.  I had a real hard time configuring windows with my wireless router on a real install(I dual boot).  Ubuntu was very nice and connected right away.

Thanks

---

### Post by pufuwozu on 2006-09-04
You get to choose if you want to have a NAT connection (piggy-backs Ubuntu's connection) or create a bridge when you're creating the virtual machine.

---

### Post by etotehpii on 2006-09-04
Thats the problem, I don't know how to do either of those.  Can you point me in the right direction?  I will look around for what you said though.

Thank you

---

### Post by etotehpii on 2006-09-04
Alright I think I've figured it out.  Took some digging but I found a NAT file that gave a gateway IP.  I pluged that IP into windows and that seemed to do the trick.
Loading stuff like Java ends up causing 100% CPU usage.  Is this a normal occurance?  I have an Athlon 64 X2 4200+ each running at 2.2Ghz.  Perhaps thats the best VMware Player can do?  I've also heard about disabiling a debug would help speed up the emulator.

Thanks

---

