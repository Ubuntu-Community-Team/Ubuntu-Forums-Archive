---
title: "Desktop Sharing, Is there and easy way"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Kedster on 2009-04-22
Hey guys,

I have recently gotten quite a few people to start using ubuntu as their primary OS and I think thats great. Although iv helped them over the phone and for some actually went over and did the installation for them and got them set up pretty stable, some have had problems using some of the software understanding certain things and for some there system has become glitchy(for what ever reason I don't know right now). I am only able to really get to there system by driving to there house and helping them. Most of them live pretty far away. what I would like to be able to do remotely help them from my computer. This is some what of a problem because they are mostly computer literates, they are learning tho. The reason this causes a problem is because they are mostly if not all behind routers.

Alright so, from what i understand is that a router hand out a computer a new ip address every time it connects to the computer. If thats true, how could i know what a certain computers ip address. What part of the ip address do i need and where could they find it. Also would the other people that need help have to forward port. would I have to forward ports.
Also I may need help using the remote desktop client, as in how to connect and which one to use.

I hope this all makes sense, if you need more information please ask.

---

### Post by sazan on 2009-04-22
I know VNCserver and Screen for sharing your work in a private network, but it will be interesting to see how we will do it via internet with dhcp.. 

looking forward from experts for advice..

---

### Post by Cybie257 on 2009-04-22
> **Kedster said:**
> Hey guys,

Alright so, from what I understand is that a router hand out a computer a new ip address every time it connects to the computer. If thats true, how could i know what a certain computers ip address. What part of the ip address do i need and where could they find it. Also would the other people that need help have to forward port. would I have to forward ports.
Also I may need help using the remote desktop client, as in how to connect and which one to use.

I hope this all makes sense, if you need more information please ask.

To begin with, for the Internet IP address that 'can' change occasionally without paying the extra for a static IP, you can have the other users go to [www.whatismyip.com](www.whatismyip.com). That will give you the IP address to use from your place to theirs.

As for their IP address.. It's best if they can set their computer up for a static IP address and then they will need to go into the router and forward port 5900 to that IP address to allow the connection. This works great for DSL, and maybe even dial-up. As for Comcast, it's more complicated as they are modems, rather than routers. You can't set anything in the modem to forward ports or whatnot. 

I won't go into the Comcast settings unless you need them, so just ask and I will dig those up an how to get that to work. 

I'll leave this for a start and see what further questions you have. 

OH, BTW, be sure to turn on remote desktop on the client computers and it's best to select the option with a password, otherwise they either leave the computer open, or have to shut it off (for security) each time you are done. Basic info, but through I'd throw that in.

-Cybie

---

### Post by Kedster on 2009-04-22
alight thanks for the help 
right now I am not able to test stuff but i have one question right now

Because each router is different how would i instruct them to forward ports, is there a command i can send them to just let them input into terminal so that i can just send them a command or are almost all router configs the same. Or is there a guide i could send them. like i know how to forward ports on my comp but i'm deff not a professional at that.

---

### Post by PhrankDaChickenGeek on 2009-04-22
[http://portforward.com/](http://portforward.com/)

Has pretty much every common home router listed
This can't be done via the command line, because the settings needs to take place on the router, not the local computer

---

### Post by windfix on 2009-04-29
Here's a different approach:

Got to elluminate.com and sign up for their free "vRoom".  Elluminate is a full featured web conferencing system, including sharing desktops (as well as voice, multimedia, whiteboard, and application sharing).

Enter your vRoom, which allows 3 people to connect maximum.  (bookmark the URL for easy access later).  Email the URL to your pal, and they will also connect.  As the owner, you have the "moderator" priveleges (you're the power user).  Right click their name in the participant list and request desktop control.  You'll see their screen and share their mouse.

Elluminate is completely Java, so it should work on all platforms.  You can even assist those frootloops using Windows or Mac OS.

---

### Post by little_penguin on 2010-08-09
Try Teamviewer - it's available for linux and windows and does not need any port forwarding in firewalls. Good if you need to give someone remote help fast.
 
[www.teamviewer.com]("http://www.teamviewer.com")
 
There are other excellent alternatives like NoMachine NX, FreeNX, SSH with VNC or X forwarding, etc. but these require more configuration and setup on both the server and client machines.

---

### Post by Peter09 on 2010-08-09
The option I use is X11vnc reverse connection.

I create a launcher on their desktop which has the command

```
x11vnc -noxdamage -connect <my ip address>
```at my end I run the command 
```
x11vnc -listen
```This allows me to see their desktop, also they do not need to modify their router or have a static IP address. I do need to port forward my router and have a static IP address, but for me thats not a problem. The only other issue is that I must run the listen command before they use the support launcher.

HEY THIS THREAD IS OVER A YEAR OLD....

---

### Post by WaCope on 2010-08-09
I 2nd Team Viewer, it's free and easy for the not so tech savy to use, plus it works on multiple platforms.

---

### Post by endotherm on 2010-08-09
personally I recommend FreeNX/NeatX. it does require a forwarded ssh port, but it's about the only option short of a vpn that I would feel safe allowing access to from the internet. other than forwarding 22 and setting up fail2ban/denyhosts, the install is pretty.

---

