---
title: "internet not connecting with mobile modem"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by AXeS on 2009-04-09
got a problem...

trying to connect to the internet with my mobile phone (w810i).
it picks up i edited the wvdial.conf file so that all the parameters are there. i run wvdial in terminal and when it gets to the 3rd init string (init3) then it gives an 'bad string' error.

i tried many different APN's,im using a vodacom sim and i just cant see whats the problem.

i picked up now that i can install a sort of wvdial gui (Gnome-ppp) i'll try it later tonight.have to manually download it then install.

can any0ne give me an idea what could be up?

---

### Post by Temposs on 2009-04-09
wvdial and gnome-ppp are for connecting to the internet with a landline phone. It is not for mobile phones. These programs are not what you need.

Simply plug in your mobile phone and click on the network manager icon(your internet icon with the blue bars if you're connected by wifi, looks like a couple computer screens otherwise) in the system tray. You should see something related to Mobile Internet and maybe something related to your phone model on there. If you do, click on it, and it should connect. I can connect this way with my mobile phone.

---

### Post by AXeS on 2009-04-09
na TEMPOSS im sure you can use WVDIAL for mobile,i checked a thread out with w880 and a w810 settings and they both just edited the wvdial.conf file.

to my knowledge its just as it says... a bad string and dont know what im spose to use but like you say its for a land line...hmmm my phone connects at usb and it picks up as a m0dem... now im super lost.

could you explain in a bit more detail what you replied now,i dont quite get your solution.

Thanx 4 the quick reply.

---

### Post by sswittch on 2009-04-09
> **AXeS said:**
> 

i tried many different APN's,im using a vodacom sim and i just cant see whats the problem.


Have you checked the vodacom site for correct APN settings.  Some require a default username and passwords, others don't need this at all.

Also some telecommunications providers require that if you are connecting to their APN via a PC (Even through a Mobile Phone or a USB sim modem) that you have it activated at their end.

---

### Post by AXeS on 2009-04-09
wait i get what you mean now...stupid me.

i did that,i get a vodacom connect select in the network system tray icon...but it keeps saying cant connect or something.
is there any other way to do so or do i keep going to windows for my linux progams.

keryx is beyond me unless thats the only 0ther way then i have to get to reading but i need a solution koz im beginning to feel awkward using windows everytime.

---

### Post by AXeS on 2009-04-09
> **sswittch said:**
> Have you checked the vodacom site for correct APN settings.  Some require a default username and passwords, others don't need this at all.

Also some telecommunications providers require that if you are connecting to their APN via a PC (Even through a Mobile Phone or a USB sim modem) that you have it activated at their end.


if it works in winblows i mean windows, should it not work in ubuntu?

---

### Post by Cousken on 2009-04-09
Hi,
I'm having the same problem, or so i think... I did just as you said, but the connection drops almost instantly. I will check out the local vodacom page for any tips on connecting.

---

### Post by AXeS on 2009-04-12
thanx,i will keep searching aswell.

---

