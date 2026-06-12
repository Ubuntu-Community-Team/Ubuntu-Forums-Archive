---
title: "Using Ubuntu Jaunty Jackalope 9.10 as server?"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Juice87 on 2009-11-05
Ok, here goes. I am using above stated version of Ubuntu for a couple of months now, and it's working perfect. I live in a student house, and we want a server for streaming movies / music, downloading stuff and hosting game servers, so all stuff is in 1 place and always reachable. 

Is it a wise idea to use the standard Ubuntu Jaunty Jackalope 9.10  as a server platform? Thing is my friends need to be able to use the server as well ( for example adding something to the newsserver download qeue ) I don't think a server edition will come in handy this way.

Is is possible to create remote GUI login accounts that go to the same Desktop for example? And I want them to only do basic stuff, and don't demolish the system. 

I hope you guys have any thoughts on this one. 

p.s. : I did not know where to post this, either here or the server forums, because this stuff seems kinda basic. 

Tanks in advance,

Juice

---

### Post by dvlchd3 on 2009-11-05
Look into Mythbox.  It is typically used to record shows, etc.  But it can also be used to store and stream movies:

[http://www.mythtv.org/](http://www.mythtv.org/)

There is actually a Ubuntu distro for mythbox called Mythbuntu:

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by ukripper on 2009-11-05
i think this thread belongs to "server platforms" section.

---

### Post by Mighty_Joe on 2009-11-05
> **Juice87 said:**
> Is it a wise idea to use the standard Ubuntu Jaunty Jackalope 9.10  as a server platform?

If it is stable on the hardware, sure.  MythBuntu in my mind is more for the next-to-the-TV role recording and viewing shows.  If this box is just going to sit in a closet and serve files, Ubuntu should be fine.

> **Juice87 said:**
> 
Is is possible to create remote GUI login accounts that go to the same Desktop for example? 

Ubuntu supports [Remote Desktop]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html"), if that's what you're looking for.

---

### Post by Juice87 on 2009-11-05
> **Mighty_Joe said:**
> If it is stable on the hardware, sure.  MythBuntu in my mind is more for the next-to-the-TV role recording and viewing shows.  If this box is just going to sit in a closet and serve files, Ubuntu should be fine.



Ubuntu supports [Remote Desktop]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html"), if that's what you're looking for.


For the Mythbuntu thing I'm thinking of using Tversity under Wine. I'm not going to record anything, just stream content of my server. 

A question about Remote Desktop ( I've used it before ). Is it possible to link 2 accounts ( 1 admin, me, and 1 "normal" account to one desktop? 

Thanks, 

Juice

---

### Post by e-Gee on 2009-11-05
Using Ubuntu Jaunty Jackalope 9.10 as server? ...........Wrong animal :D

---

### Post by wojox on 2009-11-05
Yeah you using 9.04 or 9.10?

---

### Post by Maheriano on 2009-11-05
9.04 = Jaunty Jackalope
9.1 = Karmic Koala

---

### Post by Mighty_Joe on 2009-11-05
> **Juice87 said:**
> A question about Remote Desktop ( I've used it before ). Is it possible to link 2 accounts ( 1 admin, me, and 1 "normal" account to one desktop? 


I don't think Remote Desktop is controlled by users.  You share the "server" desktop and any client can log in.  The only options for security are: to ask you logged in at the "server" for permission or 2. to prompt the client for a password.
Xtunneling is also an option. You can run a program on the server and have the GUI appear on the client.

---

