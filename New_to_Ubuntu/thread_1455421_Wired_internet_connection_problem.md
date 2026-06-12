---
title: "Wired internet connection problem"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-15
I have noticed a problem in that once ubuntu is finished booting, using the internet through a wired connection dosen't work, however kubuntu does detect that there is a wired connection present. So if i want to use the internet, i have to make sure that the wired connection is inserted before the booting up process if complete. How can i fix this?
Using Kubuntu 9.10, KDE 4.4.2 if its relevant

---

### Post by zvacet on 2010-04-16
You can replace Kubuntu network manager ( I don't know exact name) with **wicd**.

---

### Post by Falc7 on 2010-04-18
I have tried wicd several times, it never seems t connect to wireless networks for me

---

### Post by mgranet on 2010-04-18
Have you tried manually adding a persistent connection to network manager?

EDIT: Also, you are using DHCP, correct?

---

### Post by Falc7 on 2010-04-20
I tried, but it didn't fill in any of the correct bits of information for me, like the network name, so i think something went wrong.
I belief i am using DHCP yep

---

### Post by mgranet on 2010-04-20
Give this a try. (hoping the wicd install won't affect network manager)

Right click on your network manager widget in your systray, then manage connections. 
Under the wired tab, click Add, then make sure the connect automatically button is selected. Under the Restrict to Interface dropdown, select (eth0). EDIT: I assume you have a wireless network as well. Restrict to Interface value is a temporary setting.
Under the IP Address tab, make sure the Configure dropdown is set as Automatic (DHCP).

---

### Post by Falc7 on 2010-04-21
Unforunately it didn't work work, i've noticed that if i start with it plugged in, i can take the LAN cable out, and put it back in and it will connect straight away, no problems. But if it isen't plugged in during boot up, then it won't

---

