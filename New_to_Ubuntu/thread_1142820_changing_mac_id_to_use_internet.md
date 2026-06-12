---
title: "changing mac id to use internet"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by nayeem007 on 2009-04-29
As im sharing net a net connection with my roommate i need to change my mac id when i establish network connection. but in ubuntu 9.04 i cant do this. And each time I click on the Auto ethernet a new entry is created. Plz anyone give me advice.

---

### Post by freak42 on 2009-04-29
does

```
sudo ifconfig 'interface' down
sudo ifconfig 'interface' hw ether 00:00:00:00:00:00
sudo ifconfig 'interface' up
```

work? (replace the 00:00 with your mac hw adress)

hth

---

### Post by abhiroopb on 2009-04-29
look in snaptic for the program: **macchanger-gtk**, its a really easy gui for changing the mac address.

---

### Post by nayeem007 on 2009-05-01
i still cant change my mac ad.Ifconfig doesnt work,it says permission denied. I download macchanger in .deb format but it cant be installed. Please give a solution.Plz

---

### Post by freak42 on 2009-05-01
> **nayeem007 said:**
> i still cant change my mac ad.Ifconfig doesnt work,it says permission denied. I download macchanger in .deb format but it cant be installed. Please give a solution.Plz

are you the only user of this computer? are you in the sudoers list (to get root privileges)? If not you have to talk to the administrator of the machine

---

### Post by nayeem007 on 2009-05-01
yeah Im the only user.What can ido?

---

### Post by anjilslaire on 2009-05-01
One option is to get a router and put both machines behind it, with NAT enabled. This way, the ISP will always see 1 machine connected (the router) and then you can have as many machines connected simultaneously as you want.

---

### Post by freak42 on 2009-05-01
> **nayeem007 said:**
> yeah Im the only user.What can ido?

then you should have root rights, and the rights to do whatever you want with ifconfig? (as long as you prepend sudo)?

did you copy the commands from above in a terminal (with the sudo)? Were you asked for a password?

---

