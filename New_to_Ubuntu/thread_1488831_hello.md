---
title: "hello"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by feedback2amit on 2010-05-20
I just wana ask that how to make a broadband dial up in ubuntu operating system
kindly help me

---

### Post by Tahakki on 2010-05-20
Broadband? You don't have to dial-up broadband - just pop in your ethernet cable and you should be good to go. :)

---

### Post by WinterRain on 2010-05-20
> **feedback2amit said:**
> I just wana ask that how to make a broadband dial up in ubuntu operating system
kindly help me

Do you have broadband or dial-up?

---

### Post by feedback2amit on 2010-05-20
> **Tahakki said:**
> Broadband? You don't have to dial-up broadband - just pop in your ethernet cable and you should be good to go. :)
actually i am asking that in window xp
we go to start>control panel>new connections
in this way we can make dial up in XP.
on that reference i am asking that in Ubuntu how will 
do this in ubuntu.

---

### Post by feedback2amit on 2010-05-20
> **WinterRain said:**
> Do you have broadband or dial-up?
i have broad band

---

### Post by linuxman94 on 2010-05-20
If your Ethernet cable is plugged in then ubuntu will automatically recognize that it is there and it will connect.

---

### Post by Linux_junkie on 2010-05-20
In Ubuntu there is an applet called Network Manager which will attempt to setup and connect your pc to the internet via cable; wireless or mobile broadband.

---

### Post by feedback2amit on 2010-05-20
actually i am asking that in window xp
we go to start>control panel>new connections
in this way we can make dial up in XP.
on that reference i am asking that in Ubuntu how will 
do this in ubuntu.

---

### Post by feedback2amit on 2010-05-20
> **Linux_junkie said:**
> In Ubuntu there is an applet called Network Manager which will attempt to setup and connect your pc to the internet via cable; wireless or mobile broadband.
actually i am asking that in window xp
we go to start>control panel>new connections
in this way we can make dial up in XP.
on that reference i am asking that in Ubuntu how will 
do this in ubuntu.

---

### Post by Linux_junkie on 2010-05-20
I've just told you how it works in Ubuntu.  Its very easy, easier than in WinXP.

---

### Post by EssexEagle on 2010-05-20
> **feedback2amit said:**
> actually i am asking that in window xp
we go to start>control panel>new connections
in this way we can make dial up in XP.
on that reference i am asking that in Ubuntu how will 
do this in ubuntu.

Like linuxman94 and Linux_junkie said, with broadband in Ubuntu you can just plug in your ethernet cable and Network Manager should do the rest for you.  Are you saying that you've tried this and it doesn't work?

---

### Post by ajgreeny on 2010-05-20
> **feedback2amit said:**
> actually i am asking that in window xp
we go to start>control panel>new connections
in this way we can make dial up in XP.
on that reference i am asking that in Ubuntu how will 
do this in ubuntu.
Do you have a USB broadband modem?  These need a bit more fiddling to get them to work, or they used to at any rate.

Tell us more, and don't keep repeating the same thing in your posts - we now know that, but can't help unless you tell us a bit more about what you have tried so far and what has happened.

---

### Post by Kafubie on 2010-05-20
I would say you would have to contact a broadband company.
Example: Timewarner Roadrunner, Verizon fios, comcast.

They all cost about the same and give you different 
Download and upload depending on your area.

---

### Post by halitech on 2010-05-20
Do you have to enter a username and password in order to connect to your ISP even with a broadband connection? If you do then you have what is called a PPPoE connection. Who is your Internet Provider? That might give us a better idea on what you need to do.

---

### Post by jlaki on 2010-05-20
Something like a broadband dial-up does not exist.

You're maybe trying to configure the ADSL connection. Is this correct?

---

### Post by dineshs on 2010-05-21
You can try any of the following methods
1. DSL tab in Network manager to configure your Broadband
2. Terminal method via sudo pppoeconf
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) 
3.Configure your modem with the username and password given by ISP so that the broadband will be ALWAYS ON.

For the first two methods to work,your modem should be in BRIDGE mode and for the third method modem should be in PPPoE mode(Most of the modems support both)

---

