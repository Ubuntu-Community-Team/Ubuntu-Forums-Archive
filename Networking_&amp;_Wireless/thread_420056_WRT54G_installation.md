---
title: "WRT54G installation"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by shahgols on 2007-04-23
Hi everyone,

I am a semi-newbie Linux user and am totally new to wireless.  Well, I have not set up my home wifi, so I guess I cannot even say that I am new to it. I've been reading all the wifi inforamtion that I can get my hands on, and it's very scary, I feel very confused and overwhelmed by it all.  Actually anything about networking overwhelms me.  

My setup at home is a desktop and a laptop.  I want to setup my network so that the PC is wire-connected to the wireless router.  Then I want to setup my laptop to access the wifi network.  First things first though...Yesterday I took the plunge and shut down the DSL modem, connected it to the router (also off), and then I turned on the DSL modem, and then the router and then the PC.  The lights on the DSL modem were all on (including DSL, ethernet, internet), which is good.   But I couldn't access the internet or access the router's setup page at either 192.168.1.1 or access the DSL modem's setup page at 192.168.0.1.  Can someone help me on setting up my PC to access the internet through the router?  Thanks in advance.

P.S., once that's done, I hope to get some help with setting up my laptop to access the network.

---

### Post by stump138 on 2007-04-23
first thing I would do is make sure that you have the cat5 (ethernet cable) connected to the new router properly, and that the desktop is plugged in to the new router right.

then try to connect to the new router via web brower at [http://192.168.1.1](http://192.168.1.1) 

If you aren't connecting do a ifconfig in terminal to make sure that you have an IP address that is in the 192.168.1.x range and that your subnet mask is 255.255.255.0.  From there we can start to work on gettin things going :)

---

### Post by shahgols on 2007-04-23
Thank you much for your help.

I connected the wires correctly, I am sure of that.  The cat5 wire from the DSL modem was plugged in to the "internet" port and the cat5 wire from the computer was then plugged in to one of the open ports (port 1 I believe).  But I didn't check ifconfig.  I'll do that as soon as I get home this afternoon.

---

### Post by shahgols on 2007-04-23
Strange, I did today what I did yesterday and guess what?  I got IP of 192.168.1.100 and a subnet mask of 255.255.255.0.  But I couldn't connect to the internet, so I rebooted and after the reboot it the internet works too.  I hope that it works flawlessly from now on.  So now on to the next step...setting up the home network.   Or if anyone can post links where they walk noobs like me through setting up a home network?  Thank you.

P.S., once the home network is set up, the next step would be to configure my laptop to connect to the wireless network, and I do have a good link for that, so I guess for now all I need is help on setting up the network please.

---

