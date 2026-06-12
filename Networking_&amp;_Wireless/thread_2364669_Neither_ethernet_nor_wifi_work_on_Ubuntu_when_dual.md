---
title: "Neither ethernet nor wifi work on Ubuntu when dual booting?"
date: 2017-06-26
forum: Networking &amp; Wireless
---

### Post by royalt56 on 2017-06-26
I recently dualbooted my computer with Widnows 10 and Ubuntu 16.04.2
When I boot Windows 10, I can't connect to the internet via ethernet and wifi, but when I use Ubuntu, I can't connect with either.

With wifi, whenever I attempt to connect any wifi network (my own and xfinitywifi), it starts connecting but then it disconnects.
It's basically the same with the ethernet too. When i plug the cord in, it starts connecting to the internet then disconnects. They both basically do the same thing, except ethernet does it constantly, and with wifi it only does it when i click on the network

Ive used 3 or 4 linux os' on my laptop and they all work fine with the internet, but with my computer its not

what could i do to connect to the internet? is this a common problem?
also im a huge linux noob so i need a little bit more explaining if thats okay.

p.s. i spent hours trying to find a solution but i havent found a single one that works yet

---

### Post by ajgreeny on 2017-06-26
> **royalt56 said:**
> I recently dualbooted my computer with Widnows 10 and Ubuntu 16.04.2
When I boot Windows 10, I [COLOR="#FF0000"]can't[/COLOR] connect to the internet via ethernet and wifi, but when I use Ubuntu, I can't connect with either.

With wifi, whenever I attempt to connect any wifi network (my own and xfinitywifi), it starts connecting but then it disconnects.
It's basically the same with the ethernet too. When i plug the cord in, it starts connecting to the internet then disconnects. They both basically do the same thing, except ethernet does it constantly, and with wifi it only does it when i click on the network

Ive used 3 or 4 linux os' on my laptop and they all work fine with the internet, but with my computer its not

what could i do to connect to the internet? is this a common problem?
also im a huge linux noob so i need a little bit more explaining if thats okay.

p.s. i spent hours trying to find a solution but i havent found a single one that works yet
Was that a typo above that I've highlighted in red?

It sounds as if you can not connect using either wifi or ethernet in either OS, but I suspect you may have meant that you **can** connect when using Windows but not when in Ubuntu; please clarify.

---

### Post by royalt56 on 2017-06-26
Yes sorry for that, I did mean "can" not "can't"
i can use the internet on windows 10
but i cant on ubuntu

---

### Post by ajgreeny on 2017-06-26
See Wireless-info in my signature below and follow instructions to run the script and post the results back here.
Somebody who knows more about networking and connecting will probably be able to help sort this out for you with some suggestions.

---

### Post by johndough2 on 2017-06-27
Hi

The obvious things are  Drivers for your Ethernet and WiFi and the network manager, 
EG: Wicd or try something like...
sudo aptitude reinstall network-manager network-manager-gnome

and of course posting the output from the script, as requested above, will give some clues.

---

