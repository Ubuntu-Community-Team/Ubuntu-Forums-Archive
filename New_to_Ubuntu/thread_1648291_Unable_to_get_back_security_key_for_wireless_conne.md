---
title: "Unable to get back security key for wireless connection"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by Coa1z on 2010-12-18
I have an ibm thinkpad x31, running Ubuntu 10.04, everything appears to be working quite well, my only issue is that when I try to connect to my wireless connection, it keep prompting over and over for authentication to establish connection with the router. I am unable to hold a usable signal from my wireless connection. The authentication key is correct, but I'm not sure if I am using the right wireless security type. What can I do to approach this? I am actually very new to linux, sorry for lack of information/proper syntax. If there is any more information that you need, I have that on hand and I can provide that. Thanks for any and all considerations.

---

### Post by Eiji Takanaka on 2010-12-18
Just to rule out some potential variables to the proverbial equation. 

How far are you from the wireless router?
Have you experimented with different distances from the router to your workstation?
(Too far away is obviously going to hinder the distribution of radio waves, but so can too close/ environmental variables metal, refractive/reflective surfaces e.t.c

What encryption type are you currently using?

What o/s are you currently using? *My bad you have allready divulged this info. *

Please include as much information as possible. 

Using this it will be possible to eliminate some potential causes e.t.c

---

### Post by Eiji Takanaka on 2010-12-18
Are you using case sensitivity?

It sounds more like an authentication problem than anything else, im going to say you've used some common sense and tryed the whole distance as a trial/error thing.  ;)

---

### Post by Coa1z on 2010-12-18
Update: I just found out that one sure issue is that my wireless card and whatever respective drivers that are loaded are only compatible with WEP security encryption. The newer router that we are running here has WPA (The newer better standard) and support for WEP as well, but is not setup currently, and I wouldn't want to compromise or otherwise disrupt the network. Is there a solution either driver wise or getting a new wireless card that could solve the issue. Here is my card...

cisco aironet wireless 802.11b

Thanks for your feedback on these various issues. Do you think that a driver update would fix this? I'm not sure if ubuntu 10.10 is going to work, so I'm just keeping it at 10.04. Am I going to have to upgrade my wireless card entirely as a hardware install?

---

### Post by Coa1z on 2010-12-18
Correction: The card is not compatible with WPA. but is providing options for WEP, which doesn't help me. Any way past this?

---

### Post by Coa1z on 2010-12-19
It has been very difficult finding drivers/firmware that will work with this specific card. Does anyone know of a wireless card compatible with IBM Thinkpad x31 wireless mini PCI slot? and does that compatibility work well for Ubuntu 10.04? and does it support WPA Security?

If you know of a resource page where I can get driver support/information for a certain card manufacturer/model number pertaining to Ubuntu, that would be really helpful in this context.

Thanks for your help.

---

### Post by Coa1z on 2010-12-19
Update: I can connect to my router just fine when there is no security enabled. Having WPA is essential to my ability to work from home and anywhere else I go. So this rules out any other potential causes... Leaving me with the solution that I need a wireless card, and a driver/firmware upgrade that will allow WPA connectivity on Ubuntu.

---

### Post by Eiji Takanaka on 2010-12-19
Sounds like you've diagnosed and found a solution to your dillemma dude, fair doos ;)

If you've checked the manufcaturers website of your current wifi card and its a nogo on wpa, then i would imagine wpa is the way to go, saying that i know this sounds dumb because i haven't really researched into it too much, can you still have a secure connection (SSH or VPN) over an unsecure network i.e open or wep? Isn't this referred to as tunnelling?

Perhaps im tripping though, i vaguely recall seeing it somewhere.....


- dan

---

### Post by Coa1z on 2010-12-22
Thanks for your help Dan, I forget that manufacturer sites can be helpful, I started a new thread to weed out the drivers that work for WPA in the thinkpad x31 machine.

---

### Post by Eiji Takanaka on 2010-12-22
No worries friend, hope you solve your problem :)

---

