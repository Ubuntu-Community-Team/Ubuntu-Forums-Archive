---
title: "[SOLVED] Wireless suddenly stopped working"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by rmhodv on 2008-03-10
I am using 7.10 with a Netgear Wireless router. All has been fine since I first installed everything back in October 07. Then yesterday I switch on my laptop as normal and went to get onto the internet and nothing.I can see the connection, but get a password screen (see attached) Now I can't do anything. Any ideas?

---

### Post by SunnyRabbiera on 2008-03-10
you need the key from your network administrator...
how do you have your network setup?

---

### Post by rmhodv on 2008-03-10
This is the thread I posted, when I first set everything up.

[http://ubuntuforums.org/showthread.php?t=589328](http://ubuntuforums.org/showthread.php?t=589328)

---

### Post by rmhodv on 2008-03-10
When you say the key, what do you mean? I am the system administrator, but I set this up some months ago now so I can't remember. Can I delete the connection and start fresh?

---

### Post by rustybronco on 2008-03-10
> **rmhodv said:**
> When you say the key, what do you mean? I am the system administrator, **but I set this up some months ago now so I can't remember.** Can I delete the connection and start fresh?the key is stored in the router, you will have to go back into the router and see what password you used, then enter it into the screen you posted.

you do remember the login and password to your router don't you?

---

### Post by rmhodv on 2008-03-11
> **rustybronco said:**
> the key is stored in the router, you will have to go back into the router and see what password you used, then enter it into the screen you posted.

you do remember the login and password to your router don't you?

I Think so. How do you go back into the router?

---

### Post by rmhodv on 2008-03-11
bump

---

### Post by rustybronco on 2008-03-11
open a browser and type 192.168.1.1 (unless you changed it to something else ) your user name and password for the router.
[http://kbserver.netgear.com/kb_web_files/n101675.asp](http://kbserver.netgear.com/kb_web_files/n101675.asp)

---

### Post by rmhodv on 2008-03-11
Thanks Rustybronco. I'm based in Europe so will try this later this afternoon, when I return from work.

I'll post again to let you know how I get on. Thanks again for your help and effort.:guitar:

---

### Post by rmhodv on 2008-03-11
> **rustybronco said:**
> open a browser and type 192.168.1.1 (unless you changed it to something else ) your user name and password for the router.
[http://kbserver.netgear.com/kb_web_files/n101675.asp](http://kbserver.netgear.com/kb_web_files/n101675.asp)

Hi
I've done the above but nothing happens. I know I wouldn't have changed it to anything else? Really stuck :(

---

### Post by rustybronco on 2008-03-11
I guess i should have been clearer in my last post, you can't retrieve the pass-key if you cannot connect to the router. you must be cabled to the router or use a machine that can connect to it by wireless. 

Is the router connected up to a computer with a ethernet cable already? if it is connected by a cable, use that machine to log into the router.
if not cabled to a computer, connect a ethernet cable into the router ( not the single wan port, but into one of the four lan ports ) open a browser and type either 192.168.1.1 **or** 192.168.0.1, do you get a login window now?

if you do get a login window, you then will have to enter the user name and password (the default is username>admin and password>password **unless you changed it**), then you can go to wireless settings and retrieve the pass-key for the router.

---

### Post by rmhodv on 2008-03-11
Hi I tried connecting my laptop to one of the 4 ports using a ethernet cable and tried typing 192.168.1.1 and 192.168.0.1, but I don't get a login window.
I must admit I have now re-set my router to default settings by pressing the button on the back. However I still can't connect.

---

### Post by rustybronco on 2008-03-11
Either you didn't reset it properly or its broken.
check your manual for the correct procedure to reset your router.

---

### Post by rmhodv on 2008-03-12
Hi, I have read the manual and am sure that I have reset the router correctly. One thing that is strange though and maybe you can help me. When I connect to the router from my laptop via a ethernet cable, I can't see the 'wired' connection, only the 'wireless' connection. I have since learned that you can only configure the router with a 'wired' connection.
How do you connect to the router with the ethernet cable? Is there a setting that I am missing?

---

### Post by Hightide on 2008-03-12
Hi

Can you try a different  ethernet cable just in case there is a problem with the current cable? 

regards

:)

---

### Post by rustybronco on 2008-03-12
> **rmhodv said:**
>  One thing that is strange though and maybe you can help me. When I connect to the router from my laptop via a ethernet cable, I can't see the 'wired' connection, only the 'wireless' connection. I have since learned that you can only configure the router with a 'wired' connection.
Click on the network manager icon, select manual configuration, un-check wireless, check wired, close, open browser...

---

### Post by rmhodv on 2008-03-12
> **rustybronco said:**
> Click on the network manager icon, select manual configuration, un-check wireless, check wired, close, open browser...

Thank you. I'll give this a try and keep you posted.

---

### Post by rmhodv on 2008-03-13
> **rustybronco said:**
> Click on the network manager icon, select manual configuration, un-check wireless, check wired, close, open browser...

I've now tried this, but for some reason I can't uncheck completely the wireless, it kind of greyed out a little. Is this because my laptop is still picking up other wireless connections in my neighborhood? See attached

---

### Post by nkbj on 2008-03-13
I got a similar problem Yesterday when I replaced a wireless router. I use the same ESSID and WPA pass phrase as in the old router. One laptop (dual boot Vista and Gutsy) log on without problems so I know the router setup works. Another laptop (dual boot XP and Feisty) logs on in XP but not in Feisty. I get asked for the pass phrase but even when I type it in it does not connect to the router.

The router is a SMC2804WBR. Both laptops use ndiswrapper and Windows drivers.

---

### Post by rustybronco on 2008-03-13
> **rmhodv said:**
> I've now tried this, but for some reason I can't uncheck completely the wireless, it kind of greyed out a little. Is this because my laptop is still picking up other wireless connections in my neighborhood? See attachedNo, the wireless connections should have nothing to do with the button being greyed out, the only reasons I can think of is not cabled up properly (hooked to the wrong port-not plugged in all the way), the lan connection is disabled in the router (if that's possible I can check when I get home ) if its a pci card the card may have came loose in it's slot, or the card is bad.
with that said you did get a i.p. address so I suspect its not cabled correctly or disconnected, make sure the cable is hooked up to the correct ports on both the router and computer.

---

### Post by rmhodv on 2008-03-17
Sorry fot not posting sooner. We have had a really *bad* weekend. Just wanted to say that I have now fixed everything and the wireless is up and running. For some reason, the IP addresses had gone to static rather than dynamic. Just wanted to say 'thank you' to all of you who have helped espically rustybronco.
Thank you.

---

### Post by rustybronco on 2008-03-17
Sorry to hear about your weekend, I pray things get better for you.

---

