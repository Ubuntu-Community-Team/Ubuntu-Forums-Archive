---
title: "Ubuntu laptop not appearing in Vista network folder"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by re2851 on 2010-05-10
I am trying to run synergy between 2 unbuntu machines (a laptop and a desktop, clients) and a vista machine (desktop, server).  Works fine between both desktops.  I have the files right but when I start the laptop client, the vista server doesn't even notice.  

I remember at one point when i was trying to set up the connections between the desktops, i was having the same problem and it was because when i'd open the network folder on the vista desktop, the ubuntu desktop was not visible.

I remember having to do a bunch of stuff before the vista machine would recognize the ubuntu machine was on the network.  

Now i need to do that again so the ubuntu laptop will appear in the vista computers network folder.  I just can't remember what i had to do to get the vista machine to recognize the ubuntu machine in the first case.  Can anyone help me?  I'm not very good at this so some very basic step by step directions would be really great.  If anyone has a link to a good tutorial or somethin gthat would be great too.  thanks.

---

### Post by gzarkadas on 2010-05-10
I believe the problem is that Vista uses NTLMv2 by default for network authentication. You 'll have to configure it to accept LM, NTLM, as shown in this [link]("http://www.linux-watch.com/news/NS4434907782.html") (the recipe is at the 9th paragraph).

---

### Post by McRat on 2010-05-10
<---  Newbie.

Go to Places-> Computer -> File System -> Home -> YOURUSER -> Public.

Right click _Public_ for menu.  Look for sharing.  It might have to load some drivers for win networking.

Now on your Vista Machine.  Make sure File Sharing and Network Discovery is on.  Can't tell you which commands those are, as it seems to change every week. 

What I can't figure out yet, is why some XP/Vista machines are really slow reading the Ubuntu machine, and others haul butt. Some take a couple minutes to even see the Public file.

---

### Post by re2851 on 2010-05-11
fixed the problem.  figured it out.  the ubuntu laptop had to have a user on it with the same name and password of the vista machine. that fixed it.

---

