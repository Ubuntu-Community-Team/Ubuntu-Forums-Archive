---
title: "ssh and vnc - am I encrypted?"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by bcn17 on 2008-07-17
I have been trying to get vnc (remote desktop) working over an ssh tunnel. Here are the details- I think it is working but I'm not sure if I am indeed using the ssh tunnel for my vnc or not. Here is the details.

COMPUTER #1 - my computer   
COMPUTER #2 - moms computer

both computers have openssh-server and xtightvncviewer installed.

I have been reading the tutorial at [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH) for help but ran into problems. However I have tried this and it works but the main question is am i using my ssh tunnel?

If i enable the remote desktop via my moms computer by going to preferences- remote desktop- enable view and enable control i can then simply type- 

```
vncviewer mom'susername@momsipadress:0
```

and wala i have her desktop on mine. However, I plan on doing this remotely when I am at college so I want to use ssh. 

If from my computer I type ```
ssh -Y momsusername@momsip 
```I can access her computer via terminal window- the -Y enables secure X11 forwarding. then I can type 
```
vncviewer
```
and xtightvncserver pops up
next I type into the xtightvncserver cli
```
momsipadress
```
presto- I have her desktop in a window on my desktop. 

The questions is am I using vncviewer through ssh or is the second way analogous to the first?

I tried doing the vnc + ssh howto says but i always got error display. What do you guys think? Am i tunneling this through ssh or is this independent? THANKS!

---

