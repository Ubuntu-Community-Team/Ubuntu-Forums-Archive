---
title: "Network problems... Please Help!"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by chrome101 on 2008-11-14
Hi ppl,

I have just changed the my desktop XP to Hardy. Everything works really well. My laptop (satellite pro6100) has been upgraded to hardy and running sweet. I mainly use the laptop for programming, php/mysql/python etc...

I have a xampp development server on the laptop for website projects. When the desktop was running xp, I could connect to the laptop server through the network using http://192.x.x.x/<dir> or the hostname of the computer. 

On the desktop I have installed a lampp server using a howto: found in the wiki section. That was successful! I setup a default <index.html> page in the root directory and can access it in the local browser (firefox).

The problem is that I cannot connect to it from the laptops browser. I get a page not found message. This problem is the same the other way around (the laptop too has a default index page).

We have just moved and got a new ISP. I have checked the router settings and IP addresses and the two computers are listed with the correct IPs.

I have checked the status of the built-in firewall (UFW) on both machines and it is off in both cases.

Also, folders that are supposed to be shared cannot be seen on opposing machines. 

Networking is not my strongest point and I seem to have hit a brick wall. I have been told about opening ports, but I dont know where to start on that on.

Are there any howto's that could help or has anyone got any ideas of how to solve this problem

Thanks in advance... 

:confused:

---

### Post by chrome101 on 2008-11-16
wow... all weekend... great response

---

### Post by xen-uno on 2008-11-16
You need to explain the topology of your network. Sounds like your using the desktop as an internet gateway for the laptop. If so, I'm having similar problems using the Ubuntu desktop as a gateway for my Xbox 360.

---

### Post by Iowan on 2008-11-16
Machines can **ping** each other?

---

### Post by chrome101 on 2008-11-18
Ok, here it is... We have recently changed ISP (from BT broadband to Virgin) Each machine (desktop and laptop)is wireless and connects to the router this way. 

I have sucessfully pinged each machine and thats as far as I can get. Each machine gets on the internet with no problem but cannot see each other via http nor does the network seem to appear.

The router shows that the two machines appear on the network with IP addresses and name but not much else happens

---

### Post by chrome101 on 2008-11-23
Sorted... I have found the problem... I turned off the firewall on my windows laptop and did the same on the desktop (although I thought this had been turned off before)... by doing this I am now able to see share files through the network and connect to my server...

:popcorn:

---

### Post by Iowan on 2008-11-24
Progress is good :) Now I suppose you can investigate to see if/how it's possible to open the firewall(s) for file sharing, but still keep out the bad stuff.

---

