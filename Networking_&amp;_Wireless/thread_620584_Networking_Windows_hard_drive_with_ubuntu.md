---
title: "Networking Windows hard drive with ubuntu"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by sent17inel on 2007-11-22
I've read some posts on networking windows computers to share drives with ubuntu. But all the directions seem out of my league. I really want to get one of my windows drives in the other room set up as a shared drive between my whole family. 3 laptops. 2 using windows xp and one using windows 2000. 2 desktop computers. One using Windows Xp and one using Ubuntu gutsy gibbon. Most of the posts ive read talk about using samba which im not too familiar with and they also mostly had servers that had network drives so its not the same as my case since i want to connect to my windows xp desktop computers hard drive and transfer files to them from my gutsy gibbon desktop computer and my windows 2000 laptop. This would be extremely handy and useful! Does anyone know an easy way to set this up? Also im using a linksys router with wifi which is how all our computers get the internet. Do i need to configure anything in the router?

---

### Post by kevinatkins on 2007-11-22
Hi,

OK, a bit of clarification regarding Samba might be useful here. Samba comes in two parts - a client and a server component. By default, when you install Ubuntu, the Samba client is installed, which means that you should be able to connect to a Windows machine that has been set up for file / print sharing. If, however, you also wanted your Ubuntu machine to appear in your Windows network and to share files (and printers..) *from* your Ubuntu machine, you would need to install and configure the Samba server component..

But if all you want is to access that windows shared drive, Ubuntu already has everything in place. The first thing you need to do is to correctly set up file / print sharing on that Windows machine, then perhaps verify with the other Windows machines. Once you're happy that the Windows side is working properly, all you should need to do is go to Places -> Network, select 'Windows Network' and select your workgroup, then the share name.

---

### Post by mikeycantoon on 2007-11-22
I have a similar thread going on right now on the same thing.  When I first installed ubuntu I could see my windows shares and access them, copy files, everything.  Now a week later I can no longer see the windows network.  And I haven't changed anything.  I can go on my windows boxes and browse the network all day long but now ubuntu can't see them.  So I don't know how I can see them before and now not and also I don't know how to fix it, I have no clue whats messed up, and so far I have had no replies yet on how to fix it.

-Mikey

---

### Post by sent17inel on 2007-11-22
its not working... i tried to do the stupid simple windows file sharing thing but only the laptop is showing up in the network and thats when i view the My Network places from the laptop so its only seeing itself. i cant get the xp desktop and the windows 2000 computer to see eachother.... any ideas?

---

### Post by sent17inel on 2007-11-22
Nevermind... its all working on the windows side. i tested every windows computer i own. they can all transfer files among eachother... now i just need to figure out how to connect my ubuntu computer... any ideas on how to do that?

---

### Post by sent17inel on 2007-11-25
anyone know how to set it up in ubuntu?

---

