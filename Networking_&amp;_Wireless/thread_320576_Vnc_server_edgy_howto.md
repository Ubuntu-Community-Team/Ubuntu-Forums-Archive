---
title: "Vnc server edgy howto"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by nystagmust on 2006-12-17
I have been trying to set up a headless server which I am basically just using as a NAS. 

I want to be able to have the machine shutdown and restart and still be able to VNC into it.

I have tried all of the VNC server howto's with no success. I have fixed my font path and done everything the howtos say. 

One problem I might be having is that the first part of this howto [http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc+server+howto]("http://www.ubuntuforums.org/showthread.php?t=122402&highlight=vnc+server+howto") 

seems to mention setting some things up in the login setup screen menu. In edgy these dont seem to appear to be the same. I have tried doing other things to simulate what this howto described but to no avail.

My first question:

I have somehow managed to screw up my greeter for ubuntu. every time i start up now it says there was an error and it will have to use a backup greeter. What is the easiest way to simply reset this? 

My second question:

Can someone please writeup a howto for how to setup a vnc server on Edgy?
Or just specify, concisely, ALL the differences between the previous howto and the way to do it correctly in edgy?

Thanks!

---

### Post by MetalMusicAddict on 2006-12-17
Well for me, I run Xubuntu/VNC on my headless server. I have it autologon and x11vnc runs at startup. I just added it to the sessions. Its a little insecure ATM but theres no outside access.

---

### Post by nystagmust on 2006-12-17
That sounds like an acceptable solution metalMusic but can you give me a step by step approach to how you did that? 

Specifically what do you mean you have it autologon? How did you achieve that with x11vnc? Can you send me a link to the specific x11vnc Howto you used? Finally and most importantly are you using Edgy?

Thanks for your reply!

---

### Post by Zrock on 2006-12-17
wow after a week of looking and fighting with things i finnaly got it wroking thanks to the link in this post... Thanks.... Now im not sure how i missed that totorial I think iv red just about everything on this form...hehe

---

### Post by gurgle on 2006-12-19
I am looking for a way to connect up to a :1 session with VNC. I can connect up fine to my regular desktop, but i would like to start a new session with VNC. When I try and connect up to my ubuntu:1 session, it just bombs out on me. I followed the Wiki to no avail :(

---

