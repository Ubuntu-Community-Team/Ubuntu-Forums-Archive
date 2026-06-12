---
title: "Ubuntu 10.10 newbie can't connect to wireless connection"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by MatthewWilliams on 2010-12-08
I know that other people have had problems with this, but they seem like legitimate problems and I have no clue what I' supposed to be doing.

I just got the latest version of Ubuntu today, and I can't connect to the Internet. I go System>Prefrences>Network Connections to open that window. I go to the Wireless tab, click new, and type the name I want for the network and the SSID. I go to the Wireless Security tab and put in the credentials there. I click apply and... Nothing. What am I doing wrong?

Oh, and lspci | grep Wireless tells me "01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)". So if any of that matters... *shrug*

Any help would be greatly appreciated!

---

### Post by campb.andrew on 2010-12-08
Hey, i had these issues last night myself. What i know personally is that the drivers for my wireless weren't installed. I had to use an ethernet cable to connect and then update my software via the update manager. however, if you dont have the capability to use the ethernet port, you can check my thread on this to see if you can find anything useful. 

if you have ethernet access via a cable though, press alt-f2, and type update-manager -d and it should come up and automatically search for drivers and stuff and update. you should be fine afterwards.

Here's the link to my thread:
[http://ubuntuforums.org/showthread.php?t=1640443](http://ubuntuforums.org/showthread.php?t=1640443)

---

### Post by MatthewWilliams on 2010-12-08
Thanks for the quick response! I'm downloading the updates now, but I'll read your thread just in case. Thanks again!

---

### Post by campb.andrew on 2010-12-08
Ok. No prob. Glad i could help.

---

### Post by MatthewWilliams on 2010-12-08
Well, that turned out to not be the problem.

I'll check your thread thoroughly and report back.

**EDIT:** This is so incredibly confusing. >_<

I can provide any information you need and I can follow instructions, but I can't make heads or tails of what I need to do from that thread...

---

### Post by fatharraxman on 2010-12-08
sudo apt-get update
then system>Applications>Additional Drivers

---

### Post by fatharraxman on 2010-12-08
connect to wire first

---

### Post by MatthewWilliams on 2010-12-08
> **fatharraxman said:**
> sudo apt-get update
then system>Applications>Additional Drivers

"No proprietary drivers are in use on this system."

Also, I found this: I am able to get it to try to connect to my internet, but instead of showing the signal strength it just shows the lines glowing from the bottom to the top and back again. It's hard to explain, so I hope you know what I mean...

---

### Post by fatharraxman on 2010-12-08
Yah it happened to me once but in my case the password was not the right one check it if not done post a feed back and some one more experience will help you of course

---

### Post by fat yak on 2010-12-08
Presume you are trying to log in at home, to your own router. 
"but instead of showing the signal strength it just shows the lines glowing from the bottom to the top and back again"
that implies your computer can't find the wireless network.
When I have had problems with wireless connection, I make the SSID discoverable and turn the encryption off and see if the computer can connect to the network without encryption (only for the purposes of testing the link - turn it all back on again afterwards).
Then do one thing at a time (encrypt, hide SSID) and then see if you can connect, work out which part is causing the problem.
If it won't see the network without encryption, then it may be the wireless is looking at the wrong address. I have sometimes had to steer the computer towards the router. Instead of using DHCP, I have given the computer a static address and specified the gateway as the router address.

---

### Post by MatthewWilliams on 2010-12-08
Nope, my password's right. It's WEP, though, and there are a lot of options for WEP... I could be using the wrong one.

I'm not going to lie, Ubuntu's a bit intimidating at first. xD

**EDIT:** Oh, sorry, didn't see you there. :P

> **fat yak said:**
> Presume you are trying to log in at home, to your own router. 
"but instead of showing the signal strength it just shows the lines glowing from the bottom to the top and back again"
that implies your computer can't find the wireless network.
When I have had problems with wireless connection, I make the SSID  discoverable and turn the encryption off and see if the computer can  connect to the network without encryption (only for the purposes of  testing the link - turn it all back on again afterwards).
Then do one thing at a time (encrypt, hide SSID) and then see if you can connect, work out which part is causing the problem.
If it won't see the network without encryption, then it may be the  wireless is looking at the wrong address. I have sometimes had to steer  the computer towards the router. Instead of using DHCP, I have given the  computer a static address and specified the gateway as the router  address.


I'll definitely try this at some point, not sure if I'll be able to right now...

---

### Post by Jakey_TheSnake on 2010-12-08
Just popped into this thread, is your wireless router one where you have to press a button to activate a device registration period? Otherwise check the router settings, it may be undiscoverable to new devices or you may have to specify your hardware's MAC address for it to connect.

---

### Post by irenioskamoska on 2011-03-02
following....
in the " desktop>applications " couldn´t find the other drivers
and on " desktop>system>administration>hardware drivers " : there are 2 possible drivers for the network controller i have (Broadcom BCM4312)
and when i try to activate any it says: system error: failed to lock /var/cache/apt/archives/lock

by various triyings it says that the driver is activated and the connection´s getting ready

first i connected the web via ethernet and updates ubuntu

i hope it works!

---

