---
title: "wireless lan connection without router"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by pckong on 2008-01-27
Hi all,

I have two sets of wireless cards and 2 computers. I need to set up my own wireless network without using router. I have search relevant topic but found very little. Do anyone know how to do it? I don't have a router,

Pete

---

### Post by pckong on 2008-02-04
Hi, 

I still have the problems.... :(  they are for educational purposes...

Can anyone help?

---

### Post by Ayuthia on 2008-02-04
It has been a while since I have done it and I did it between Windows and Linux.  You can try setting one of the laptops as an ad-hoc connection:
[CODE]sudo iwconfig wlan0 mode Ad-Hoc essid <make up a name>[CODE]
I think that should set that laptop to be able to transmit the essid name out and your other laptop should be able to see it.  The next step would be to get the IP addresses assigned.  This is where I don't know the easy way to do.  I used the Windows laptop to assign the IP addresses and then they were able to talk to each other.  You might try using Firestarter and dhcp3-server.  That might get you going.

Like I said, I am not for100% sure if this is the correct way of doing it or not.  You might try searching for ad-hoc internet connection sharing and that might provide you some better results.

---

### Post by pckong on 2008-02-04
Hi Ayuthia,

Thanks for replying. I am not with my laptop at the moment, but I will try it as soon as I can. 
Before I am not even able to set up the Ad-Hoc connection, and I cannot even see my other computer.

---

### Post by pckong on 2008-02-05
I can see the SSID now. But still not able to establish the connection. Thanks your help anyway. At least I took a great step

---

