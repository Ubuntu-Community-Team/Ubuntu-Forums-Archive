---
title: "HP Pavilion dv5000 question"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Firch on 2009-11-21
I'm currently chained down with my laptop through a wired connection and I want to break free from my chains and begin my Wireless glory days with what I already think is the best OS I've ever used. I have one problem though. it says that my wireless is disabled. the light that says it is on is on however so I was wondering if there was something I had to do manually for it to be enabled.

I'm new to linux so go easy on me.

---

### Post by Bucky Ball on 2009-11-21
System->Administration->Network

Is the wireless card enabled? If not:

Unlock->Wireless->Properties and set it up with the correct details to connect with your router/network (ESSID, security key). 

System->Administration->Hardware Drivers. Anything there? Have you got all updates? Were you offered a restricted driver for the wireless card? What Ubuntu release are you using?

9.10 is proving problematic for some at the moment (and not others). Only came out end of last month. That situation continues to improve. 8.04 LTS is rock solid.

Do you know what brand the wireless card is? 

Welcome to Ubuntu. ;)

---

### Post by Firch on 2009-11-21
it says the multicast is enabled but it is inactive. hardware drivers brings up nothing. I'm using 9.10.

---

### Post by LunaticHiatus on 2009-11-21
worse comes to worse, you have to buy a wireless card. I got an asus WL-167g off neweggs which has worked great for twenty bucks.

---

### Post by Firch on 2009-11-21
Yea I was thinking I might have to do that. I just figured I was overlooking something stupid and small.

---

### Post by Firch on 2009-11-21
update. I ran a check for updates and it turns out I had a huge amount that I needed to get so I got all the necessary ones and now when I search hardware it finds two pieces of hardware it didn't before and one of them is my wireless adapter. now when I mouse over the area where it would show me how strong my connection is it says "device not ready" 

Any ideas?

---

### Post by Bucky Ball on 2009-11-21
Now go to System->Admin->Hardware Drivers

Thinking about a new card is way premature. [-(

Open a terminal (Applications->Accessories->Terminal) and paste this command in then hit return:

```
lspci
```That will list all the devices in your machine. Somewhere near the bottom of that list you will find your wireless card. I have the dv6000 and that uses a Broadcom card which works 'out of the box' ie it should be picked up by the updates and you should be offered the restricted drivers.

While your in the terminal paste this command also:

```
iwconfig
```Copy and paste the result back here if you could.

---

### Post by Firch on 2009-11-21
as it turns out I WAS overlooking something small. I decided to reboot and see if it helped,which it did. I'm typing this as we speak via a wireless connection using 9.10. 

thanks for all the help!

---

