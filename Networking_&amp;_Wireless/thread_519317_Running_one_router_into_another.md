---
title: "Running one router into another"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by NoSmokingBandit on 2007-08-06
At work we have a Linksys befsr81 to which we want to add wireless ability to. I told my boss to get a wireless access point that i could just plug in and it would work, but he went and go a Netgear Wireless N router. How can i set it up so the Netgear acts like a access point?

---

### Post by Mr. C. on 2007-08-06
Hmmm.  Have you read a single word from the user manual ?

One would be hard-pressed to find an access-point only piece of commodity hardware today.  They are essentially all multi-function appliances, performing NAT/PAT, routing, firewalling, DHCP services, VPN, etc.

Spend a few minutes becoming familiar with the web interface of the product, and learning what you can do with it.  You should have no trouble adding it to your existing network, but you will likely have to disable certain services already performed by your existing hardware.

MrC

---

### Post by NoSmokingBandit on 2007-08-07
If the manual had told me how to set it up this way, would i be asking anyone here for help?

This is what i wanted him to get:
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367689584B03](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367689584B03)
That you can essentially just plug in and go, but i need to know how to add a router to function as a access point/switch.

---

### Post by psusi on 2007-08-07
Disable the dhcp on the thing and plug it into the network NOT using the uplink port.

---

### Post by kevdog on 2007-08-07
I did it the reverse of you -- having the a wired router--->wireless router---->Cable Modem---->Internet

The purpose of the wired router was basically to turn a room with 1 connection into four.  The wireless router acted as a dhcp server, and was responsible for port forwarding.

To make this work the LAN address of the wireless router was assigned (192.168.1.1).
The LAN address of the wired router was assigned (192.168.2.1) <---Basically a different subnet
All computers, wireless devices on the 192.168.1.1 subnet with DHCP server on the 192.168.1.1 subnet.

As far as the connection
Cable Modem ----Cat 5 ---->Ethernet Port of Wireless Router --->Port #1 on Back of Wireless Router--->Cat 5 --->Port #1 Wired Router (Not the ethernet port!!!)--->Port #2 Wired Router--->Cat 5---->Computer Ethernet Card.

Im not sure if this is what you want to do.  I basically wanted the wired router to act as a splitter.  Im sure you could reverse the configuration, however just be aware that if you want all the computers on the same subnet you want only one DHCP server. Also pay close attention to how the routers are wired, with the ethernet port on the second router not being used.

Took me a while to figure this one out.  Hopefully it will help you!

---

### Post by mips on 2007-08-07
Double post !!!

[http://ubuntuforums.org/showthread.php?t=518861](http://ubuntuforums.org/showthread.php?t=518861)

---

### Post by NoSmokingBandit on 2007-08-07
lol, yeah, i couldnt remember if i hit the post button or not before closing the window, so i searched and couldnt find that thread, so i assumed i didnt, i guess i did. Oh well, my bad.

Ok, so if i disable DHCP on the wireless router, then plug that into the wired router via cat5 into port 1 it should work? Sorry about being a network noob, the most i have ever done is a simple home network here in my house, but i love to learn computer stuff, so this is cool.

---

### Post by psusi on 2007-08-07
Yes

---

### Post by Mr. C. on 2007-08-07
> **NoSmokingBandit said:**
> If the manual had told me how to set it up this way, would i be asking anyone here for help?

Nobody can know what you did and didn't do, or what you understand and didn't understand.  The "duh... of course I did" response can never be assumed when helping others.  Your post was very light on details.  I gave you a generic answer to your generic question.

> **NoSmokingBandit said:**
> 
This is what i wanted him to get:
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367689584B03](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1126536803676&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0367689584B03)
That you can essentially just plug in and go, but i need to know how to add a router to function as a access point/switch.

It doesn't really matter what you wished happened; that's over and done.  What matters is that you understand the network your are trying to administrate. 

MrC

---

### Post by NoSmokingBandit on 2007-08-07
I responded to you the way i did because you seemed very rude, and it seemed as though you were insulting my intelligence by assuming right off the bat that i didnt even try.
I posted the link to the access point because you said:
> 
One would be hard-pressed to find an access-point only piece of commodity hardware today.

Everyone else helped me out just fine, and i dont want this to be an argument between us, so i'll just try random stuff out until it works.
I am not the network administrator, i just happen to be the only person at work who knows how a computer works, so i get stuck doing everything.

---

### Post by Mr. C. on 2007-08-07
NoSmokingBandit, it was the brevity and tone of your post.  There's an inherent contradiction with your position.  You admit your unfamiliarity with networking and equipment, yet were comfortable advising your boss on purchasing decisions.  I wasn't intending to insult your intelligence, but did challenge your energy and effort in helping others to help you.  In general, one gets more help when one puts in sufficient energy and effort into seeking knowledge and understanding.

Its all about asking intelligent, useful questions.

MrC

---

### Post by NoSmokingBandit on 2007-08-07
I know enough about networking that i can tell my boss an access point is the easy route, but i dont know enough how to set up a router to act like one. Its not that hard to comprehend that i have limited knowledge. If you arent going to post anything useful just stay out of this thread, nobody else had a problem helping me.

---

### Post by Mr. C. on 2007-08-07
I gave you the help you asked for, in as much detail as one could *reliably* give, given *your* lack of clarity on even the product model!  I indicated you would have to disable certain services.  Other's hazarded guesses as to what those services were, but without more concrete data, they are only guesses.  It serves little purpose to have dozens of people tossing out random guesses until they randomly converge.

It was entirely impossible from your initial post to "comprehend" your knowledge or lack thereof.  But your laziness was apparent.

MrC

---

### Post by kevdog on 2007-08-07
Hopefully you can

1. Wire the routers together as indicated
2. Turn off DHCP on the router you dont want to issue DHCP
3. Put the two routers on different subnets
4. Put the DHCP router on the same subnet that you want your computers.

Just wanted to know if this strategy worked for you!

---

### Post by psusi on 2007-08-08
You don't need to worry about different subnets.  When acting as an access point the device has no address.  Just do as I said before and it should work fine.

---

### Post by NoSmokingBandit on 2007-08-08
I am waiting for everyone to leave the office so i can work on it, but ill let you guys know if it works or not. Thanks for the advice.

---

