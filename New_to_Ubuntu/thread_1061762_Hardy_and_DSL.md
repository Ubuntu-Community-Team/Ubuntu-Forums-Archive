---
title: "Hardy and DSL"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-06
I just converted a friend to Ubuntu 8.04
She has Verizon DSL...I used DSL many years ago with m$ and remember it wasn't as easy to get going as Broadband.
She has to add a second pc can
1. can i get her a regular lynksis router?
2. do i need to do anything special to get her online? with 8.04 network manager???

---

### Post by Temposs on 2009-02-06
I think it should work just fine. A DSL modem should just interface through an ethernet cable either directly into the computer or to a router, the same as with a Cable modem.

---

### Post by hyper_ch on 2009-02-06
well, I have no clue how it works there, but for DSL here you normally get a DSL modem which has username and password stored and then "autodials" for the connection (that's for the WAN part).

For the LAN part you normally have 1-4 ethernet pors and a usb port or a mix of it. There's normally nothing that needs to be configure from the linux side except for setting up a normal network. The dsl modem/router should by default act as dhcp server alos.

---

### Post by DarinB on 2009-02-06
Thanks i was hoping for it to be easy i remember years ago it was a pain to authenticate you needed to use a different setting in setting up ie. If any one that has dsl can chime in it would be great...i don't want the friend to think i don't know anything... we all know how people are they expect perfection from machines and anybody that does tech even part time, for free!!!!!!
Therefore the linksis router will work the same???

---

### Post by superprash2003 on 2009-02-06
how does internet work currently?? does your internet work as soon as you switch on your modem?? or do you need to use a dialer in windows to connect??

---

### Post by DarinB on 2009-02-07
she can get on line when opening ie .
Her other computer has xp.
My curiosity is to pre-empt any problems before i get there.
I do remember that you have to set up ie by hitting the button that says dsl vs broadband.

---

### Post by sizzlefire on 2009-02-07
I had verizon DSL and a linksys router a few months ago, and was using 8.04 at the time, and it all worked fine together. I don't think you will have a problem.

---

### Post by carml on 2009-02-07
Try to go to System->Help & Support and look for the Internet section,you'll find there the instructions to use a DSL connection with the Ethernet support.Think also to install Gnome PPPon from Applications->Add/Remove,so she'll be able to automate the connection like on Windows.I hope I have beeen clear and nailed the question. :)

---

### Post by ptn107 on 2009-02-07
Just plug everything in.  Works the same as cable.

One thing I did notice is that you do _**not**_ want the router to use PPPoE to connect to your isp, even though the setting says 'for most dsl users'.  This should not be a problem, though, since the default is 'dynamic ip provided by isp'.  Just double-check for your sanity, so your not wasting an hour wondering why you can connect to the router and not the internet.

---

### Post by superprash2003 on 2009-02-07
does she know the username and password for the DSL connection?

---

