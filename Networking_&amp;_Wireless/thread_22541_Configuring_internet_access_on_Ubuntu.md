---
title: "Configuring internet access on Ubuntu"
date: 2005-03-28
forum: Networking &amp; Wireless
---

### Post by Michael_Grosberg on 2005-03-28
Hi, I'm a new Ubuntu user, I installed Hoary a couple of days ago.
Now, I'm not a linux guru but I have some experience.
In other distro's, I configured my PPPOE eathernet ADSL modem during the install process.
When I installed Ubuntu the installation process did not offer me the option of configuring a PPPOE connection. Instead, it asked me to configure a DHCP server. The problem is, I've no idea what that is. It also suggested I consult my "web administator" or some such! Obviously I don't have one at home!

I chose to skip the configuration as I did not know what to do, and then the installation continued without further options.
When the system finished installing, I had no internet connection and no idea how to set one up. The help didn't help me on this - there was nothing about PPPOE there - just dialup and LAN. 

It didn't take too long to reboot to windows, find a web board with the instructions - typing PPPOECONF does the trick - and be up and running.
But that shouldn't be happening in a usability oriented distro!

I think I'm pretty computer savvy, at least in the Windows world, so anything that is beyond my scope is probably beyond the average user's ability, and asking about DHCP servers in the middle of an installation process, when the user can't even find out what this is all about, can be intimidating. Now, I'm guessing I missed something in the installation process, pressed the wrong button, and maybe there IS a PPPOE configuration somewhere along the way, but the fact I missed it so easily indicates there is something wrong here.

Once I figured this one out, everything was fine and I'm enjoying Ubuntu tremendously, but this "welcome" to Ubuntu really bugged me

So, to sum it up:
1. Did I miss something? How was it SUPPOSED to work? was I supposed to run PPPOECONF? if so, why wasn't it mentioned anywhere?

2. Where is the appropriate place to suggest changes to the help and installation text? Are they considered bugs?
I'd like to suggest an addition to the quickstarter guide to cover this issue, and a change in the install process to indicate to non-technical people what they should do there. I'd also like to suggest promoting the quickstart guide to a more prominent place in the help, as I found it to be the most useful and practical piece of documentation I've ever seen in the Linux world.

---

### Post by dseomn on 2005-03-28
[QUOTE=Michael_Grosberg]Hi, I'm a new Ubuntu user, I installed Hoary a couple of days ago.
Now, I'm not a linux guru but I have some experience.
In other distro's, I configured my PPPOE eathernet ADSL modem during the install process.
When I installed Ubuntu the installation process did not offer me the option of configuring a PPPOE connection. Instead, it asked me to configure a DHCP server. The problem is, I've no idea what that is. It also suggested I consult my "web administator" or some such! Obviously I don't have one at home!

I chose to skip the configuration as I did not know what to do, and then the installation continued without further options.
When the system finished installing, I had no internet connection and no idea how to set one up. The help didn't help me on this - there was nothing about PPPOE there - just dialup and LAN. 

It didn't take too long to reboot to windows, find a web board with the instructions - typing PPPOECONF does the trick - and be up and running.
But that shouldn't be happening in a usability oriented distro!

I think I'm pretty computer savvy, at least in the Windows world, so anything that is beyond my scope is probably beyond the average user's ability, and asking about DHCP servers in the middle of an installation process, when the user can't even find out what this is all about, can be intimidating. Now, I'm guessing I missed something in the installation process, pressed the wrong button, and maybe there IS a PPPOE configuration somewhere along the way, but the fact I missed it so easily indicates there is something wrong here.

Once I figured this one out, everything was fine and I'm enjoying Ubuntu tremendously, but this "welcome" to Ubuntu really bugged me

So, to sum it up:
1. Did I miss something? How was it SUPPOSED to work? was I supposed to run PPPOECONF? if so, why wasn't it mentioned anywhere?

2. Where is the appropriate place to suggest changes to the help and installation text? Are they considered bugs?
I'd like to suggest an addition to the quickstarter guide to cover this issue, and a change in the install process to indicate to non-technical people what they should do there. I'd also like to suggest promoting the quickstart guide to a more prominent place in the help, as I found it to be the most useful and practical piece of documentation I've ever seen in the Linux world.[/QUOTE]
 The default install doesn't ask about dhcp. Did you change any boot options on the install cd (e.g. expert mode)?

You probably need to install pppoe (using the Synaptic Package Manager or apt-get) then run pppoeconf (all lowercase). This probably isn't the correct/easiest way to do it (as I have no experience with PPPoE), but should work.

---

### Post by Michael_Grosberg on 2005-03-29
No, I wasn't on expert mode,  I pressed enter when the command prompt came up. 
Guess it was some bug, I guess I'll just file it.

Anyway I wasn't asking about how to solve it, I already did, I was just wandering where I went wrong - my purpose in posting is to make Ubuntu a better product by figuring out if this is a bug and notifing the powers that be about a possible problem in the install process.

---

### Post by Papaskunk on 2005-04-01
DHCP is a a very old, supported, standard network protocol. PPPoE is the newer specialized protcol that DSL providers have pushed on users relatively recently. DHCP simply assigns you an IP address and gateway.

The beginning installation does ask about network installation, in standard mode. However, it also mentions that you can configure your network connections later. Since PPPoE requires extra software and is not as common as DHCP and other network protocols, it only makes sense to leave it out of the basic installation process.

However, I agree that the installer could be a little clearer about the 'setting up the network later' part. Perhaps it should ask if you would like to set up networking now or later. But this is nothing to be up in arms about!

---

### Post by Bill_Clarkson on 2005-04-03
I just had to put my 2 cents in there and say that PPPoE just passes your username and password to the server for DSL access and most people use the router now to do that by setting it up as the PPPoE log on device so you do not have to keep logging on every time you turn on your computer.  The router keeps the DSL connection alive.  Besides this you have a nice firmware firewall.   

BC

---

### Post by Strapatzer on 2005-04-04
First 'apt-get' pppoeconf, then run it.
I tried that, but then it appears that the modem is already taken by some process.
So the install program actually sets up something, wrong thing that blocks the possibility to set the connection up as it should be... Although I had chosen to set up  the network connection later...

---

### Post by Strapatzer on 2005-04-04
I've even had to reinstall Windows to visit this forum.
Now that it is 'fresh' again i'm beginning to wonder if I shouldn't simply stick with it...

---

### Post by raublekick on 2005-04-08
I'm having problems setting up my Ubunto Internet connection as well. I just unstalled Hoary. First thing I did when I logged in was try to connect to my router. That didn't work, it couldn't even see my router. But I was just online in Windows before I installed. I tried running pppoeconf, it saw my eth0, but it couldn't finish running the config! 

Unfortunately I messed up my MBR in my Windows drive (grr... I wish the Ubuntu installer wasn't so vague at this part), so I had to re-install Fedora. I even told Fedora to write to the MBR of the other drive, but it just did it to the Fedora drive even though I've installed GRUB onto that same drive before.

If anyone has any suggestions to get my other drive's MBR working again or get Ubuntu online I would be greatful.

---

### Post by koxaki on 2005-04-26
[QUOTE=Michael_Grosberg]Hi, I'm a new Ubuntu user, I installed Hoary a couple of days ago.
Now, I'm not a linux guru but I have some experience.
In other distro's, I configured my PPPOE eathernet ADSL modem during the install process.
When I installed Ubuntu the installation process did not offer me the option of configuring a PPPOE connection. Instead, it asked me to configure a DHCP server. The problem is, I've no idea what that is. It also suggested I consult my "web administator" or some such! Obviously I don't have one at home!

I chose to skip the configuration as I did not know what to do, and then the installation continued without further options.
When the system finished installing, I had no internet connection and no idea how to set one up. The help didn't help me on this - there was nothing about PPPOE there - just dialup and LAN. 

It didn't take too long to reboot to windows, find a web board with the instructions - typing PPPOECONF does the trick - and be up and running.
But that shouldn't be happening in a usability oriented distro!

I think I'm pretty computer savvy, at least in the Windows world, so anything that is beyond my scope is probably beyond the average user's ability, and asking about DHCP servers in the middle of an installation process, when the user can't even find out what this is all about, can be intimidating. Now, I'm guessing I missed something in the installation process, pressed the wrong button, and maybe there IS a PPPOE configuration somewhere along the way, but the fact I missed it so easily indicates there is something wrong here.

Once I figured this one out, everything was fine and I'm enjoying Ubuntu tremendously, but this "welcome" to Ubuntu really bugged me

So, to sum it up:
1. Did I miss something? How was it SUPPOSED to work? was I supposed to run PPPOECONF? if so, why wasn't it mentioned anywhere?

2. Where is the appropriate place to suggest changes to the help and installation text? Are they considered bugs?
I'd like to suggest an addition to the quickstarter guide to cover this issue, and a change in the install process to indicate to non-technical people what they should do there. I'd also like to suggest promoting the quickstart guide to a more prominent place in the help, as I found it to be the most useful and practical piece of documentation I've ever seen in the Linux world.[/QUOTE]
 Hello! I'm starter in Linux Ubuntu too. So i have a D-Link modem (ADSL) DSL-360Tver. I need help from beggining and tell me how to get access to the internet trough this modem and how to configure the internet connection if it is needed! Thanks all. Write my email [email]koxaki@gmail.com[/email] if possible because i'm tired and i cant search this forum! Bye!

---

### Post by nycrunner87 on 2006-06-26
Hi im new to linux and ubuntu also. i have been trying to configure my internet access for the past couple of days. where is this quickstart guide you mention, Michael_Grosberg?

I have a dsl modem and then a router, then my pc. im not aware of the commands used to configure wired ethernet access

---

### Post by masood on 2006-06-29
hi i m new ubuntu user too and dont know how to configure dialup connection, waiting for replies.

thnx

---

