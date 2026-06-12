---
title: "Remote Login"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by novice_penguin on 2014-01-30
Hello everyone,

I was wondering, what do I need to configure on my end, to be able to log into my PC at home from my PC at school?  At school, I just login using "ssh myusername@host" to login to my account on the school's network, but when I try to login to my PC at home I get an error.  I can't remember exactly what the error message is and I am typing this from my home PC, so I cannot replicate the error message.  I tried letting my professor explain it to me, but to be honest, he wasn't very interested in giving me an answer.  A guy from class told me it might have something to do with my firewall settings, but I have never configured my firewall either.  I tried to login using my static IP address as well, in the same format as above, but with the same results.  I tried searching an answer before I posted this question, but I am not sure if the info I was seeking was relevant to what I need to know, due to my inexperience.  I looked at some info regarding remote login software, but I only found answers that related to "desktop sharing" software, which is not what I need.  I need to know how to login to my home network from another network.  Sorry if this question is confusing and I appreciate any help anyone has to offer.  Cheers!

---

### Post by bab1 on 2014-01-31
> **novice_penguin said:**
> Hello everyone,

I was wondering, what do I need to configure on my end, to be able to log into my PC at home from my PC at school?  At school, I just login using "ssh myusername@host" to login to my account on the school's network, but when I try to login to my PC at home I get an error.  

I can't remember exactly what the error message is and I am typing this from my home PC, so I cannot replicate the error message.  I tried letting my professor explain it to me, but to be honest, he wasn't very interested in giving me an answer.  A guy from class told me it might have something to do with my firewall settings, but I have never configured my firewall either.  I tried to login using my static IP address as well, in the same format as above, but with the same results.  

I tried searching an answer before I posted this question, but I am not sure if the info I was seeking was relevant to what I need to know, due to my inexperience.  I looked at some info regarding remote login software, but I only found answers that related to "desktop sharing" software, which is not what I need.  I need to know how to login to my home network from another network.  

Sorry if this question is confusing and I appreciate any help anyone has to offer.  Cheers!
Google OpenSSH server.

Your home PC needs to be running a SSH server (OpenSSH).  The server runs on an assigned TCP port.  Your home firewall needs to have "port forwarding set to accept all SSH requests forwarded to the assigned port on your PC.  You request access just like you so at school with ***you@yourIPaddress***, where yourIPaddress is your WAN connection IP address on the modem at home.

See [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") for Ubuntu Community Help on OpenSSH server configuration.

---

### Post by Lars Noodén on 2014-01-31
In addition to that, you might want to set up an account at a [dynamic DNS service](https://help.ubuntu.com/community/DynamicDNS) so that you can refer to your home router by name.  It's not necessary but it save you the trouble of having to look up your external ip address before leaving the house, as home ip addresses change frequently.

---

### Post by Bucky Ball on 2014-01-31
*Thread moved to **Networking & Wireless**.*

If you are attempting this on the school network, consult with you school's IT department before making any attempt to tunnel out of their system. This will better for all concerned. They will be able to give you specific instructions on how to do it and may even set up a private port for you. Or they may be completely negative and not allow you to do it at all. 

Until you know exactly what you are dealing with at the school end it is a futile quest. Don't attempt this without their help. If you meddlings pop up on their radar they will consider it a security breach and it will be squashed as an alien intruder unless they know it's you. There may be other consequences. It may be impossible to do without their co-operation in the first place and you should thoroughly research where the school stands on these sorts of activities.

PS: It's not your firewall, it's theirs, and I don't doubt it is a solid one. Which is why you need to speak to IT. By your professor's reaction they might not encourage your activities. 

While the advice of the other posters might be sound if you were in an internet cafe or at a friend's house, at school you are shrouded by their network and their security protocols. I would imagine there is no way out (or in) unless they create it. In the unlikely event the methods outlined above did get you out (or in) then there will be some not happy people breathing down your neck when their big red light starts flashing.

---

### Post by novice_penguin on 2014-01-31
Sorry for posting in the inappropriate section and thank you for all of your help.  While I can certainly see why one would be skeptical to allow a user access to their network, I feel my professor had no problem with my attempt to login to my home PC since he encouraged it (the class I'm taking is a Linux Scripting class).  I just don't know why he wouldn't have known it was because of not having the right software.  I think I am starting to doubt his expertise a bit, especially since my initial reaction was that I needed some kind of software and/or port issues.  Nevertheless, thanks again for all of your help and I will now learn more about this SSH software and what it means to use it.

---

### Post by Lars Noodén on 2014-01-31
It's good that he's encouraging.  There are several pieces to work out to get remote access to your home computer from campus or a cafe, though some of it is dependent on your specific set up and he cannot give generic advice about it. 

First you have to have openssh-server running on your home computer.  Be sure that is installed and that you are able to log in from another machine on your same LAN at home.  Using a second machine behind the router / modem takes that modem / router out of the question and lets you concentrate on just the server.  It should work out of the box, but it's good to take it one step at a time.

Second, you have to forward an external port on your router /modem to port 22 (ssh) on your home machine.  When you are away from home, it is to the router / modem that you will make the connection.  The exact details vary from model to model and brand to brand so that is the part he probably balks at and the part that we can help the least with.  You can set this from your LAN using the admin mode of the modem / router.  There should, somewhere, be a menu where you plug in the LAN ip of your home machine and choose an external port to represent it.  

Next, you have to find out your modem / router external ip address for that particular day.  You can look it up before you leave for school using [http://canyouseeme.org](http://canyouseeme.org) or a similar service.  Or you can sign up for a free or paid dynamic DNS service.  Most modems / routers are pre-configured to work with dynamic DNS services and all you have to do is plug in the account info and then you can refer to your home by name, regardless of whether the ip has changed or not.  Again, like with the port forwarding, this varies a bit from model to model and brand to brand.  

Last, once the above steps are in place you should be able to connect from outside to your home computer using ssh.

---

### Post by novice_penguin on 2014-01-31
Thank you that was a lot of helpful information and it all makes more sense now!  I'll try your advice and pass this info along to another person in my class that may want to know how.  Cheers!

---

### Post by Bucky Ball on 2014-01-31
It's great that he's encouraging, but about connecting to your PC using the uni network, or using your own network connection using a wireless dongle, quite separate from the uni network?

If the former, guess he would have told you how. If the latter, sorry about the confusion. ;)

---

