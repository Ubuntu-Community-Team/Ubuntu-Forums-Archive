---
title: "Help! VNC problem"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by athenaa on 2010-07-27
Hi,

I am trying to connect to my ubuntu computer from a windows machine, I did the setup in 
Menu->System->Preferences->Remote Desktop, 
but I just get a black screen.

I have the same setting on another ubuntu machine, and that one works perfectly.
may be I'm missing something, or I've forgotten some setting.

I looked everywhere on the internet, but non of the solutions I found solved my problem,

I really appreciate any help, don't know what else to do :(


Thanks,
Athena

---

### Post by YesWeCan on 2010-07-27
Is this is a Windows issue? What application on Windows are you using to view the remote Ubuntu desktop?
When you say it works on another Ubuntu machine do you mean that machine can view the remote desktop on the first Ubuntu machine or are you saying that the Windows machine can see the other Ubuntu's remote desktop?

---

### Post by athenaa on 2010-07-27
I'm using vnc viewer.
I don't think it's a windows issue. I can see the other ubuntu from my windows machine.

As I remember, I just set the system-> preferences->remote desktop on the other ubuntu, and I was able to connect from my windows 
using vnc viewer, but for some reason, it doesn't work with the other machine. 
When I connect to the machine, I can even see the gadget saying "another user is controlling your machine", but the rest of the screen is black.


edit:
turns out, I messed up with something in Xorg,
when I reinstalled it, problem solved.
 every time I try to install the suggested updates, my graphics get messed up.

---

