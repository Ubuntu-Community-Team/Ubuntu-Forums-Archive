---
title: "Cannot connect to wired LAN"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by youngbill on 2007-06-06
I am a new Lenix/ubuntu user.  I installed WinXP Pro x64 and ubuntu 7.04 for dual booting on my new  Core 2 Duo computer.  I have a wired LAN with Linksys router, static addressing, and DSL modem.  My new XP Pro OS connects to my LAN, sees all the devices on my LAN including a print server, and connects to the Internet through my router and DSL modem.  The LAN works properly.

I installed ubuntu using the 64-bit live CD.  The installation was smooth without problems.  I configured network settings using the same static IP address, subnet mask, gateway, and DNS servers that I use successfully in WinXP Pro.  I confirm that my wired connection is activated.  (The box is checked.)  But, ubuntu does not appear to connect to the LAN.  I see no components on my LAN.  Firefox cannot access the Internet.

I tried a different static IP address for ubuntu without success.

Since the WinXP Pro OS on the same computer is successful, I assume the problem is not the network hardware.

Since I am brand new to Lenix/ubuntu, I must be missing something simple.  I searched ubuntu help documents and the online forums without finding anything useful.

I would appreciate some help.  I am brand new to Linux/ubuntu so keep your suggestions simple. Thanks

---

### Post by boucek on 2007-06-06
Can you ping your router?

What is the output of **ifconfig** in the terminal?

---

### Post by renzokuken on 2007-06-06
run the following commands from the terminal

```
sudo ifdown eth0
sudo ifup eth0
```

and see if anything changes

---

### Post by youngbill on 2007-06-09
Thanks for your responses.

I am new to this forum.  When I posted this message, I was not sure it took, so I reposted.  For more details, see my later post titled "Network Connection Problem", same user name, youngbill.

Responding to your suggestions, the output of ifconfig is in my later post, pinging my router yields no responses (all times are zero), and using the two commands did nothing new.

Please review the details in my later post.  The details may suggest a solution to you.

I will follow my later post and close this one.

---

