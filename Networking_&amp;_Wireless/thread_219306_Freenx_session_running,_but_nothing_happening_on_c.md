---
title: "Freenx session running, but nothing happening on client-side"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by rootberg on 2006-07-19
Hi, I just got freenx server to work on my Ubunu Dapper machine. I use the simple install (machine key  I think it is called) and well yea... it's up and running. I then try to connect using nomachines nx client for windows, from another computer. It makes the connection, and when I run the "--history" command in ubuntu for my user, I can see that my connection is "running". The funny/sucky part is that nothing seem to happen on the client side (winxp computer). It's like the program closed. Why doesn't the linux GUI appear (I guess it's GIMP right?) ?

Would really like some help on this one. This is my first post here btw, hope we have fun together and learn learn learn :D
Peace...

---

### Post by rootberg on 2006-07-20
I just wanna add, that it works to connect via the ubuntu computer running the server, with GUI and all...
Is it correct to write in the localIP of the ubuntu computer when I try to connect via client from winxp? I have opened port 22 for the ubuntu computer aswell.

---

### Post by rootberg on 2006-07-20
Ok I found the solution.
The winxp client on nomachine.com was version 2.0, you can't get the GUI up using that, you have to find the 1.5 version of the client, or upgrade your freenxserver so the two match. 
The old client can be found here:
[http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe](http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe)

I found it on the forums, so I was maybe a bit to eager...

---

