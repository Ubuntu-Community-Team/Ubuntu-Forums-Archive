---
title: "VNC looks messed up"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-11-09
Hi,

I tried running vncserver on my machine, and it seems to load without a "problem" ...the only thing is, when I connect to it all I get is a GUI with a terminal in the GUI. Is there a way I can load a desktop to make it look a little more like a normal session? 





RHEL 5.3 - but I figure it's a VNC problem, so I turn to the wisdom of the Ubuntu Forums :D

---

### Post by B34ST1Y on 2010-11-09
Nevermind! It was in the ~/home/USER/.vnc/xstartup config file - All I had to do was uncomment the top two lines, which said in the commented directions would load the profile :) 


Oops! Hopefully this helps someone else!

---

