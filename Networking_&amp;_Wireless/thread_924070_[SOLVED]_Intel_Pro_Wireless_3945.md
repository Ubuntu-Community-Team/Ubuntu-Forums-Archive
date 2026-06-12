---
title: "[SOLVED] Intel Pro /Wireless 3945"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by joshmuffin on 2008-09-19
hello, i am new to ubuntu and having some troubles with my intel Pro (R) /Wireless 3945ABG wireless card. i can connect to open networks and wpa personal which are at my house though when i go to school it is wep 128bit hex and i can't connect, i have the right key as it works in windows xp. i think the connection may be hidden though it shows up in the network manger thing (system tray). my fried is running 8.04 hardy and connects however i am running 8.10 and cant. i only updated a few days ago and couldn't connect in hardy either.
i am running a lenovo/imb x60 and i am quite new to linux
any help would be GREATLY appreciated.

btw i have tried downloading and compiling the iwlwifi3945 driver and get all sorts of errors.

---

### Post by joshmuffin on 2008-09-22
Please help im desperate, i know its possible my friend has it working, as much as i love ubuntu i think i might have to change

---

### Post by lotacus on 2008-09-22
There really should be no problem connecting with WEP. It's quite interesting because people usually have trouble connecting using WPA. What I would find out is what type of security your school is using for it's security. Colleges and Universities use RADIUS for authentication (if their smart), and it would all depend on their configuration of that RADIUS server. Do you remember having to register your MAC address with the school, or have to install a Certificate or anything like that?

What you can try doing is testing WEP with your own wireless network and see if it connects, but I bet it has to do with the schools network policies.

---

### Post by joshmuffin on 2008-09-23
> **lotacus said:**
> There really should be no problem connecting with WEP. It's quite interesting because people usually have trouble connecting using WPA. What I would find out is what type of security your school is using for it's security. Colleges and Universities use RADIUS for authentication (if their smart), and it would all depend on their configuration of that RADIUS server. Do you remember having to register your MAC address with the school, or have to install a Certificate or anything like that?
my friends have told me the network is "hidden" i dont know if that has anything to do with it. but there is definetly no mac adress registering or certificate. and my school and the smartest to say the least:P

> **lotacus said:**
> 
What you can try doing is testing WEP with your own wireless network and see if it connects, but I bet it has to do with the schools network policies.
i will try that and post my results as soon as posible, as i say i have connected to that network from ubuntu, i vaigly remember it was because i installed linux-backports-modules-hardy-generic but im having troubles installing the interpid ibex equivelant linux-backports-modules-intrepid-generic

thank you very much lotacus

---

### Post by joshmuffin on 2008-09-23
i have just checked and my router only has two encryption options WPA-Personal, and WPA-Enterprise. it also says WPA-Enterprise would need an external RADIUS server, im assuming wep can use RADIUS aswell. btw i just found out my friends worked out of the box.

thankyou in advance for all your help :)

---

### Post by joshmuffin on 2009-01-01
I just stumbled on this again and I thought I'd let you all know that an upgrade to Intrepid Fixed it

---

### Post by TadeoDiaz on 2009-01-05
I am having a similar problem. I can connect at home to a WEP authenticated connection but not at school to a hidden connection.

Do you happen to know what update fixed it?

---

### Post by joshmuffin on 2009-01-06
No  idea this was months ago, sorry.
I'm having no troubles, I'm running jaunty jackalope now.

---

