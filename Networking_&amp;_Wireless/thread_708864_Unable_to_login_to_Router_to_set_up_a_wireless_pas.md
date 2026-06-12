---
title: "Unable to login to Router to set up a wireless password."
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by avelez89 on 2008-02-26
Hello all. I am aware there are several similar threats but I haven't found one that addresses my issue yet, so thank you for taking your time to help me.

I connect to the internet through a ZyXEL Prestige 650H/HW31 modem, my Desktop computer (this one) is connected to it, and then I also connected a Wireless router (Linksys wrt54g) to the ZyXEL Modem such that my Laptop could connect to the internet wireless. Internet works like a charm on both machines (my desktop and my laptop.)

I want to connect to my Linksys wrt54g wireless router to set up a password. In the linksys manual it says I can login to the router by directing my laptops browser to [http://192.168.1.1/](http://192.168.1.1/), but when I try this, the browser tries to login to the ZyXEL modem and not the Linksys router. How can I login to the linksys router, for some reason it seems to be 'bypassed'? (all procedures are being done from the laptop)

Heres a little map for reference:

ZyXEL modem -----> Linksys Wireless Router---->Laptop
       I
       I
    Desktop


Thank you for your time!

---

### Post by rustybronco on 2008-02-26
Can you disconnect the cable from the modem to the router and then try it? hopefully the modem is not wireless also, if it is wireless then you may have to turn it off first.
I configured my router and changed it to 192.168.2.1 before I connected it to the cable modem.  (the cable modem was also 192.168.1.1)
you may want to change the routers address to something other than 192.168.1.1 to save the trouble next time.

P.S. all you need to type in is 192.168.1.1

---

### Post by superprash2003 on 2008-02-27
the problem could be because both your router's have the same ip which is 192.168.1.1.. change the ip of the wireless router to 192.168.2.1 or anything else!!so you can avoid a ip conflict

---

### Post by avelez89 on 2008-02-27
That seems like a great idea but how can I change the router's IP adress if I can't login to it to begin with? (the original problem) I can, however, log in to the modem and change the modems IP adress, will that cause any problems with my internet connections?

Thanks for your time!

---

### Post by mmichalik on 2008-02-27
If all else fails, you can get a pass through network cable and connect your PC directly to the wan port on the router, login and change the ip.

a pass through cable is different from a regular network cable.  You will have to go to a local computer store, more then likely something other then Fryes or CompUSA, and purchase one.

---

### Post by rustybronco on 2008-02-27
> **avelez89 said:**
> That seems like a great idea but how can I change the router's IP adress if I can't login to it to begin with? (the original problem) I can, however, log in to the modem and change the modems IP adress, will that cause any problems with my internet connections?

Thanks for your time!Both the modem and the router have the same I.P. address that won't work. it would be like you and someone else having the same telephone number, when you get called who are they going to reach?
did you try what was suggested first?
You know the modem works as it is, don't add something else to the mix by changing it.

---

### Post by Kevbert on 2008-02-27
I suggest you connect a cable from your PC directly to your wireless card and then see this page:
[http://www.tech-faq.com/forgot-linksys-router-password.shtml]("http://www.tech-faq.com/forgot-linksys-router-password.shtml")

Then you should be able to set the password any encryption etc.

---

### Post by avelez89 on 2008-02-27
I connected my router to my PC and edited all the details necessary from there. Problem Solved. Thank you very much for your time and help!

The ubuntu community is indeed the best.

---

