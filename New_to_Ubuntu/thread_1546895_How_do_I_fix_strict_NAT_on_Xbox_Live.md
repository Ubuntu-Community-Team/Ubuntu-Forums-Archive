---
title: "How do I fix strict NAT on Xbox Live?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by bodleya on 2010-08-06
Absolute beginner here, using a wireless modem dongle. I have successfully configured my netbook to connect to xbox live except whenever im using it, it will only get up to about 5-6Kbps. Also I have a strict nat warning when I log in and it tends to only let me play in small servers (5-6 players). My connection has the capability of running at about 130Kbps and was just wondering if it was the Nat problem or something else any of you out there could help me solve this frustrating problem.

---

### Post by SpockVulcan on 2010-08-07
Why are you asking this in Ubuntu forums. This has nothing to do with Ubuntu

---

### Post by bodleya on 2010-08-08
oh sorry, i forgot to mention im using ubuntu 10.04 netbook remix. Just not sure whether its my isp or some kind of config setting

---

### Post by Theft42 on 2010-08-08
I had this same problem but with my 360. I do believe you have to open up some ports for that computer.

And I knda figured you had Ubuntu or you wouldn't be here :lolflag:

But yeah google to find the Ports as I can not remember =/

---

### Post by bodleya on 2010-08-08
Thanks Theft, Im a total newbie and honestly i dont know how to open  ports manually. Is there some generic command for the terminal? I also  found the names of the ports which are:
TCP 80

UDP 88

UDP 3074

TCP 3074

UDP 53

TCP 53

---

### Post by Theft42 on 2010-08-08
Well my problem was fixed by going into the routers settings. as it's firewall and safety features were blocking the ports. If you go to your routers company website it should tell you how to access the setting for your router as some are different.


Like my Belkin router I would open my Internet Browser and enter in the address field 192.168.2.1 and it takes me to my routers settings. from there I would then open the ports..

But as said each router is different. 

What type of Router do you have?

---

### Post by bodleya on 2010-08-08
Thanks again... Im actually using a wireless modem, no router I think.

---

### Post by HPD2 on 2010-08-08
Your modem is also most likely a router too depending on your isp.You need to log into the router/modem and then just throw the xbox in the dmz. That should allow it to access the internet unrestricted.

---

### Post by Theft42 on 2010-08-08
I do believe it's the same concept the modem and router are just combined into one. Unlike mine where the IP gave me a modem and I had to buy a separate router. makes it a little easier if you can log into the modems address. Check the company that made the modems website and they should have the info there to access the settings.

I do apologize as I am not the very best at assisting like some other users but I try my best :lolflag:

I also apologize as it's 3am here and i need to get to bed for work. I hope my information can assist you and hopefully your problem will be solved.:D

---

### Post by Theft42 on 2010-08-08
> **HPD2 said:**
> You need to log into the router and then just throw the xbox in the dmz. That should allow it to access the internet unrestricted.

Apology for double posting this is a simpler solution if your modem/router has the option in the settings. But he is using his netbook for xbox live so the whole comp would be unprotected completely by the modem/routers firewall.

---

### Post by HPD2 on 2010-08-08
> **Theft42 said:**
> Apology for double posting this is a simpler solution if your modem/router has the option in the settings. But he is using his netbook for xbox live so the whole comp would be unprotected completely by the modem/routers firewall.

I don't know of any way short of using the computer as a router or attempting to make a lag switch that involves using a computer on xbox live, later being against the TOS and COC. Assuming you are dong the first, if you use a firewall on the computer allow access to those ports.

---

### Post by bodleya on 2010-08-09
Thanks again everyone for helping me out on this one. I am accually using a Huawei e160e, and looking about on other forums I dont think there is an actual way of opening ports manually. apparently because Its a modem plugged directly into my netbook there is no router. But if of course I would appreciate any help, if at all possible.

---

