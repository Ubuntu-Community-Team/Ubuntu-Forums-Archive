---
title: "Internet connection sharing (haw to set this up?)"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by BronenG on 2009-07-30
I am a newbie, i installed in the past many Linux distros on my PC, but i always play a little with them and then go back to Windows. So i newer study them in depth. My problem is that i haw a sister :). She is connected to my PC over a crossover LAN cable. She is using my PC to go trough it to the Internet. I am connected to the Internet with a D Link WiFi car installed on a PCI slot.
So the problem is that when i install Ubuntu she cant connect to the Internet. On windows it is easy to make a Internet connection sharing. But i really don't know haw to do that on Ubunu.

To be more specific. My sisters PC uses WinXP and it has a static IP adres. We had little problems connecting our two PCs together automatically with DHCP.Her PC :
[LIST=1]
[*]IP:[INDENT]192.168.0.2[/INDENT]
[*]Subnet:[INDENT]255.255.255.0[/INDENT]
[*]Def. Gareteway:[INDENT]192.168.0.1[/INDENT]
[*]DNS:[INDENT]192.168.0.1[/INDENT]
[/LIST]

My PC: 
[*]IP:[INDENT]192.168.0.1[/INDENT]
[*]Subnet:[INDENT]255.255.255.0[/INDENT]

I am connecting over my WiFi to my friends router to gain Internet acces. I dont know the IPs of the router.
In Ubuntu the WiFi sets up automatically and i can connect to the Internet.  But i don get any connection to my Sisters PC over my LAN cable. I tried to set it up manually, and it worked. But not for Internet connection sharing.

I would be very grateful if anybody can help me set this up. I haw read some Internet Connection Sharing posts and they are not a big help to me cos i don understand them very well. Ore better to say, i know very little about LAN and WiFi connections.

---

### Post by nhasian on 2009-07-30
i think this will help:

[http://webupd8.blogspot.com/2009/02/ubuntu-internet-connection-sharing.html](http://webupd8.blogspot.com/2009/02/ubuntu-internet-connection-sharing.html)

---

### Post by Iowan on 2009-07-30
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is another one to check.

---

### Post by Geoff918 on 2009-07-30
Judging by what you're saying--I would be very close to positive that your router IP is 192.168.0.1. It seems your router is also doing DNS server resolution.

PS - Static IPs are assigned only through the interface, in other words it may be a static IP in windows, but that means little to nothing in terms of another operating system. It could be set to dynamic or static either way.

Here's a question for you: Are you able to access the local area network through your sister's connection (anything in the 192.168.xxx.xxx range is private and only addressable on your local area--it's a universally reserved range)? My thought is that the network card may actually not be operating properly.

Try logging into [http://192.168.0.1](http://192.168.0.1) and see what happens. My bet is you get a login screen for your router. Depending on your router these are usually set to a standard username and or password. Something like "admin", "admin" or "admin", (blank), or (blank) "admin". Something of that sort, probably an internet search for your router brand will tell you what to use if it has never been set before.

Hope this helps!

---

### Post by sam_delta on 2009-07-30
you can also install firestarter firewall (nice gui), and you can set up internet sharing pretty easy with its gui.

sam

---

### Post by BronenG on 2009-07-31
I didnt saw that one :), im gona try it later if the other resolutions don worck. Thanck you for your replay!

---

### Post by BronenG on 2009-07-31
Iowan, thank you to, but i saw that one, and it confused me. I did not make it work. It hang on the begining.

---

### Post by BronenG on 2009-07-31
Geoff918, i can connect from my machine where i installed Ubuntu to my sisters shared files. I can also connect to the Internet   with my WiFi card. The router address is 192.168.1.1 cos it really asks me for the login information. I think the cards are working fine. They worked when i got WinXP installed on my machine. I tried Firestarter, and it did not work. In Ubuntu my IP is set manual. I also haw the problem that my sister can not see my Ubuntu PC on the network. I suppose we are not in the same Workgrup ore something similar.
I am going to try now to connect her, and i am going then to post the results.
Thank you all for your replays :)

---

### Post by BronenG on 2009-07-31
People i made it! The guide [http://webupd8.blogspot.com/2009/02/...n-sharing.html](http://webupd8.blogspot.com/2009/02/...n-sharing.html) has made it work.
I am not sure, but i think does something like Firestarter but it rely works. I was not sure about the last step cos it wasn't tel where exactly should i add the text. I add it at the beginning and it works.

Thank you all! :) You are great!

---

