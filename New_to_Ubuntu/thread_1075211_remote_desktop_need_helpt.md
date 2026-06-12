---
title: "remote desktop need helpt"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by chrisr6 on 2009-02-20
aright so there has to be a tutorial or something somewhere on the web about this but I have been looking for 2 day now for help with setting up a remote desktop connection with no luck I am sort of new to ubuntu 8.10 but I do know a little bit any help with this would be great here is what I want to do 
I have a desktop running ubuntu 8.10 with a wireless connection to a dsl connection at my house and my sister has a laptop which I just put ubuntu 8.10 on because she was fed up with windows vista it is connected to the internet using wireless to a dsl router as well but she lives about 45 minutes away and does not know anything about ubuntu so I will have to do all of the work on the computer for her. I want to set-up a remote connection so that I can do this from my computer at home. I know it is possible I just have not had much luck I tried SSH but cant figure the program out please help I will answer all questions to my best knowledge thank you

---

### Post by NoReflex on 2009-02-20
Hello!

ssh gives you a shell to a remote computer so you can run any commands on that computer.
If you prefer "visual" connection to her computer you can use VNC. This is probably what you want since you will be both sharing the same desktop so she can follow your actions and learn along the way.
All she has to do is to go to System -> Preferences -> Remote Desktop and check "Allow other users to view your desktop". She should also make sure that "Allow other users to control your desktop" is checked and she should definitely choose a password so that only those who know the password can connect.
If her router has UPnP she could check "Configure network automatically to accept connections" and port 5900 would "automagically" be forwarded to her computer.
Anyway it is probably safer to forward the port manually from the router's web interface ([www.portforward.com](www.portforward.com) gives you specific instructions on how to achieve that for almost all router models).
After these steps have been completed you can select on your computer Applications -> Internet -> Remote Desktop Viewer and type in the IP address of her computer (the public one - she can find that using something like [www.whatismyip.com](www.whatismyip.com)).
I hope this gives you a starting point. Good luck!

Best wishes,
NoReflex

---

### Post by chrisr6 on 2009-02-20
i still cant get this to work this is driving me nuts i am starting to get frustrated i would just give up but i need this any more help would be great. thanks

---

### Post by mgmiller on 2009-02-20
When you put the IP address into vinagre (Remote Desktop Viewer) to connect to the remote machine, you must also specify the port number.  In this case it's 5900.  So for IP address, 69.123.456.789, you would enter the address: 69.123.456.789:5900

This assumes, you have set up the router at the remote end to forward vnc requests to the internal nat address at port 5900, of course.

In the top panel of the **remote computer** (the one you are trying to connect to), right click the network manager icon in the top panel and select "Connection Information"

In the resulting dialog, look at the IP Address: line
A typical entry would say something like 192.168.1.4 or similar.
This is your nat address.

Next, since you don't have a remote desktop connection yet, you will have to do this sitting in front of the remote computer, or have someone there do it while you talk to them:  Open the configuration dialog for the router on the remote computer by putting it's address in firefox.  The different brands use different addresses.  

From here, each brand of router is a little different.  You will need to get directions from:
[http://www.portforward.com]("http://www.portforward.com/")

What you will be doing is forwarding port 5900 to the nat address you discovered above.

Good luck.

---

### Post by chrisr6 on 2009-02-22
thank you i finally got it big help

---

