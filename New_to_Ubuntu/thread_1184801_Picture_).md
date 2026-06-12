---
title: "Picture? :)"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by duds2008 on 2009-06-11
Hello everybody! I hope you are all well!
Using the command line is pretty straight forward and simple to use. The picture I get in my mind is like being a monkey in a tree climbing about from branch to branch!! I am relatively new to networking and do not fully understand much about ports. I know port 22 is used for ssh! Could anyone give me a quick picture on how to understand what ports are all about in pretty much the same way as I see the CL? It really helps when you can see things from a different perspective. At the moment I see them as being in a city and knowing that for me to get to a superstore I need to follow "such and such" a road, and follow the rules for that particular road. Does this sum it up? I hope this is not a silly question.
Any help is sincerely appreciated!
PS: Am planning on setting up a home server, hence my interest in ports:) Thank you.

---

### Post by unutbu on 2009-06-11
Hello duds2008! Think of your machine like a McDonald's restaurant.
When you run a service like ssh, it is like opening up a drive-thru window. 
People who want to talk to you via ssh drive up to the window. That window is the port.

When you run a second service, like mysqld, you are opening up a second drive-thru window.
People who want to talk to mysqld need to drive up to this other window (port).

So to complete the picture, your machine is like a mega-McDonalds with many separate drive-thru windows (ports), one for each service.

---

### Post by duds2008 on 2009-06-11
Thank you Unutbu. This is the type of picture I'm talking about! There are so many ports!

---

