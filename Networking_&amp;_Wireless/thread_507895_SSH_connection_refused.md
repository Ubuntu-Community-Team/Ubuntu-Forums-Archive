---
title: "SSH: connection refused"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by zuzuzzzip on 2007-07-23
Ubuntu 7.10
openssh-client & openssh-server installed
port 22 is listening (nmap), sshd is running

So when I try to connect to my Ubuntu host through Putty on Windows on global IP-address, I (still) get this error!

I can connect to localhost so server is up and A-OK, and also my port 22 is listening.
I tried all this -> [http://www.linuxquestions.org/questions/showthread.php?t=352163&highlight=tcp6](http://www.linuxquestions.org/questions/showthread.php?t=352163&highlight=tcp6)
But I get an error when I do:```
sudo nc -l -p 22
```which is: "**Can't grab 0.0.0.0:22 with bind**"
What does this mean? I found out that 0.0.0.0 is my device...

Perhaps I need to Port Forward on my router?

Thanks in advance

---

### Post by dreadlord_chris on 2007-07-23
> **zuzuzzzip said:**
> Ubuntu 7.10
openssh-client & openssh-server installed
port 22 is listening (nmap), sshd is running

So when I try to connect to my Ubuntu host through Putty on Windows on global IP-address, I (still) get this error!

I can connect to localhost so server is up and A-OK, and also my port 22 is listening.
I tried all this -> [http://www.linuxquestions.org/questions/showthread.php?t=352163&highlight=tcp6](http://www.linuxquestions.org/questions/showthread.php?t=352163&highlight=tcp6)
But I get an error when I do:```
sudo nc -l -p 22
```which is: "**Can't grab 0.0.0.0:22 with bind**"
What does this mean? I found out that 0.0.0.0 is my device...

Perhaps I need to Port Forward on my router?

Thanks in advance

:lolflag: You're sitting behind a router? Unless your router is configured *pass-thru* then yes, you'll need to forward the port.

---

### Post by zuzuzzzip on 2007-07-23
> **dreadlord_chris said:**
> :lolflag: You're sitting behind a router? Unless your router is configured *pass-thru* then yes, you'll need to forward the port.

Well that sucks, because the router has a login which I don't know because it's from my dad's work :) it's a linksys wireless-g one :P

---

### Post by punx45 on 2007-07-23
look up the default password for the model, and try it, if it doesnt work, you can hard reset the unit to factory defaults (CAUTION will erase any ISP settings! make sure you know username/passwords etc. if necessary)  with the little button that you need a pen or something to reach.   press and hold it for 30-60 secs, should do the trick.   then go reconfigure the router and make sure to change the password!!

also if you havent already, make sure the LAN IP for the ubuntu machine is static.   i believe this can be changed in /etc/interfaces?  (correct me if im wrong)

---

### Post by zuzuzzzip on 2007-07-24
yeah, that's the problem see :P it's not a default password that is set... and I don't think I should erase the ISP settings as only the company knows them. Although the linksys router is connected to a adsl-modem...
I'll have to ask my dad :)

I'll get that static IP anyway.
Thanks!

edit: it's /etc/network/interfaces :)

---

### Post by punx45 on 2007-07-24
i think i misunderstood.. this is a router currently AT your dads work?   or is it one he brought home from work for you to use? which computer is connected to this router?

that makes a difference :-D

being connected to DSL you dont want to do anything.   at least here in the states DSL providers use PPPoE which requires a login and password, whereas cable companies lease you out a DHCP assigned IP, so no logins needed.

> **zuzuzzzip said:**
> 

edit: it's /etc/network/interfaces :)

i was close!

---

### Post by zuzuzzzip on 2007-07-25
no the routers at home, provided by work and locked with their router login (which i need to know).
And I can't hard reset cause then indeed I will lose PPPoE login to my ISP... I think,
 because this wireless router is linked to another one, so maybe that's the actual router/modem to my ISP with PPPoE (and it most likely is) so I'll have to ask my Dad when he's back from holdiays :( :P

Thanks for your help anyways :)

---

### Post by punx45 on 2007-07-25
yeah, that is possible.   if the other router is your gateway (the one being provided a global IP by your ISP) then that is the one that you need to configure to forward SSH to your computer.   you shouldnt have to get into the wireless one at all.   depending on how the network is set up.

---

### Post by MadMario on 2007-09-04
Last week I saw a seminar about ubuntu, and they made it sound like it was easy to use and any idiot can do it. Now I see that that is not true. Trying to simply do an SSH to an Ubuntu system requires a lot of technical/network knowledge. It certainly is not as easy as just pushing a button to get everything to work. I'm going back to Fedora.

---

### Post by dreadlord_chris on 2007-09-07
> **MadMario said:**
> Last week I saw a seminar about ubuntu, and they made it sound like it was easy to use and any idiot can do it. Now I see that that is not true. Trying to simply do an SSH to an Ubuntu system requires a lot of technical/network knowledge. It certainly is not as easy as just pushing a button to get everything to work. I'm going back to Fedora.
yeeeaah....
this is not an operating system problem - it's a **network device** problem
the router would have to be configured to forward the SSH connections - ***the same way*** - no matter what OS was being used on the computer connecting to the device.

---

### Post by zuzuzzzip on 2007-09-11
> **dreadlord_chris said:**
> yeeeaah....
this is not an operating system problem - it's a **network device** problem
the router would have to be configured to forward the SSH connections - ***the same way*** - no matter what OS was being used on the computer connecting to the device.

exactly, my router will not allow ssh-connections. It's easy to change, just open your gateway's address in you browser and you are configuring you router.

---

