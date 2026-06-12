---
title: "What can a Server do and not do?"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by leadoffdouble on 2009-09-28
Threefold question:

I am decent with computers.  I don't know code, although I can follow directives (but I don't know why I am doing what Im doing).  Typically it works out.

1.  Should I attempt to set up a server in my classroom.

2.  Can I set up a server and connect it to our school's Windows network (is this possible/wise)?

3. If I am logged into the Admin machine, can I view what each workstation if viewing?  I don't mean go through and track what websites they've visited... I mean view all workstations screens live - simultaneously?

Thanks

---

### Post by NullHead on 2009-09-28
What you're asking to do could be rather complex. 

[LIST][*]That depends on what you want to do with a server.
[*]Connect in what way? Wirelessly, file sharing, domain etc ...
[*]I guess something could be rigged using VNC, but this, as mentioned earlier, could end up being rather complex. 
[/LIST]

---

### Post by TinManofOz on 2009-09-29
I agree, what do you want to do with it? if you don't need a server stick with a Desktop for learning.

Setting up the server is no big issue (when you try to do something with the server, that's when things get hard). Just have another computer available to do research or ask questions if needed.

BEFORE you even think of connecting to the schools Network get permission! You can unintentionally wipe out the school network (I have seen this happen).

Not sure about being able to see all the other computers. If they are Microsoft OS you will need some sort of special software to see them. If you are building a computer lab get some help, your biting off a lot for someone new to Ubuntu (or new to any OS for that matter).

---

### Post by dvn3ch on 2009-09-29
Have to agree with TinMan on that.  Your idea is great but the complexity of the execution is even greater.  Apparently, greater than your skills, too.  

I have 4 systems running at the present time.  One Ubuntu Server (dedicated for my websites), two Hardys (one my main rig, the other for my daughter), and a lonely XP laptop that my wife uses.  With that said, it took me better part of a week to get the server to FTP with the XP laptop.  Ubuntu is inherently secure, so talking across platforms becomes an exercise in patience.

I suggest starting off with 8.04 (Hardy) Server and when it is up and running with the command line looking at you with menacing eyes, install the Ubuntu-Desktop with apt-get.  I was learning my way around the server and learning Ubuntu at the same time and found that I really needed that GUI to keep things familiar.

I applaud your can-do attitude but try getting the basics of command-line programming down first.  It will save you some future heartache.

---

### Post by leadoffdouble on 2009-09-29
Thank you very much.  My goal was to run a bunch of lame laptop wirelessly (thin client) throughout a small private school.  I wanted this network to run independantly of the school's network (windows) but I'll need the school's T1 to get my network on the internet.

I also have 6 HP mini's that came with the "mi" (HP's ubuntu).  We opted to move them to ubuntu 9.04 and deal with "no sound" for now.  My understanding is 10... will solve this.  

But I guess if I'm only doing wireless (google docs, etc), it doesn't matter what network Im connected to.  I thought I'd learn in hopes of getting a friend's school up and running in another country in the future.

I did get a gui to load to an older version of Ubuntu Server a few years ago.  Not sure how, I just followed the instructions (probably from one of you guys) and it worked.

I suppose what I REALLY want is to control/see, in real time, what my students are doing AND eventually be able to throw up anyone's screen on a projector in the classroom (once I buy it).

Thanks

Oh, another thought.  Can I set up my network and stick a wireless card in the ubuntu server, and just hook it up to one of our two access points and let the thin clients and mini's connect to the ubuntu server?  ...and have my windows network see the server as just another wireless machine?

---

### Post by NullHead on 2009-09-29
So it sounds to me like you'll need these things: 

A wireless router, a desktop PC with two monitors, VNC, partimage, and a saved pre-setup image of the OS you want to use on the minis. 

As for the "server", you're best off installing a desktop version of ubuntu, and loading on "server" applications. I believe any desktop will do for such a task. I suggest dual monitors for this setup so you can monitor the client's work, and also do work of your own. 

Having dual monitors will also assist in this projector treatment.

---

