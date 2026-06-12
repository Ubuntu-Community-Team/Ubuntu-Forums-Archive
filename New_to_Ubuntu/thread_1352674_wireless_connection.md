---
title: "wireless connection"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by johnizzle on 2009-12-11
i am a ubuntu newbie, and i really need help with my computer.
i have just recently upgraded to 9.10 and i use a acer computer with a belkin router.
i have a wireless connection, but i cant get on the internet, and i am pretty computer retarded haha. 
i would appreciate some help please, and please keep it simple.

---

### Post by blazemore on 2009-12-14
Do you mean you can see a list of wireless networks and can successfully connect to one?

---

### Post by johnizzle on 2009-12-14
yeah i can get a wireless connection and it says im connected but the internet wont work..

---

### Post by cartisdm on 2009-12-14
Is this a wireless network in your own house? Do other computers on this network connect to the computer?

---

### Post by johnizzle on 2009-12-14
yeah its in the house, and my brother has a hp hooked into the router and my mother has a toshiba with vista in the living room and its using wireless and works fine

---

### Post by cartisdm on 2009-12-14
Are you able to connect to the network if you hook up straight to the router via an ethernet cable?

---

### Post by johnizzle on 2009-12-15
no, but i can go through the modem

---

### Post by blazemore on 2009-12-16
SO you have this setup:

{INTERNET} --> [MODEM] --> [ROUTER] ~~~~~~ [Your PC]

And that doesn't work, but this does:

{INTERNET} --> [MODEM] --> [YOUR PC]

Is that right?

---

### Post by cartisdm on 2009-12-16
> **blazemore said:**
> SO you have this setup:

{INTERNET} --> [MODEM] --> [ROUTER] ~~~~~~ [Your PC]

And that doesn't work, but this does:

{INTERNET} --> [MODEM] --> [YOUR PC]

Is that right?

If that is the case then it's very unusual that you wouldn't be getting a connection unless some of the default settings have been changed on either your Ubuntu installation OR the router.  There are a few possibilities you can look into though:

- Is the router using MAC address filtering? (although I thought this was just a wireless setting and not affected by a ethernet connection, but I could be wrong)

- Check the firewall, proxy server, or any security settings that may be blocking your connection

- See if you can ping your router
     - if you can't, then the problem likely resides in the router settings
     - if you can, then try to ping an external website

- also make sure DHCP is setup on your computer (it should be setup correctly by default unless you changed any of the settings)

---

### Post by johnizzle on 2009-12-16
yes blazemore thats right

---

### Post by johnizzle on 2009-12-16
well at first i thought it could be the router, but if it was the router, wouldnt my moms computer not be working?

---

### Post by cartisdm on 2009-12-17
> **johnizzle said:**
> well at first i thought it could be the router, but if it was the router, wouldnt my moms computer not be working?

no, not necessarily.  If it is set to MAC filtering then it will only allow computers on the network that have been set

---

### Post by lotharmat on 2009-12-17
I was under the impression that if MAC filtering was used, the router would refuse to give an IP address.

Could you post the results of
```
ifconfig
```

---

