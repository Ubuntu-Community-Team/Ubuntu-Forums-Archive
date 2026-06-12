---
title: "Do i need to use a firewall if i connect through a router"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by hoppyandy on 2009-01-12
My question is do i need to use a firewall such as firestarter to connect to the internet if my connection goes through a router with a built in firewall, i do use p2p programs which can be a pain to set up with some firewalls (Only have windows experience)due to multiple in and out connections to loads of different ip addresses, i used kaspersky when i had windows which allowed me to accept all traffic for the p2p program i was using, not sure if firestarter has that. Are there other firewalls available which may suit this better.
just wanted your experiences, opinions and recommendations.

Thanks

---

### Post by kansasnoob on 2009-01-12
If you're running 8.10 gufw may already be installed. Look in System > Administration and see if you see Firewall Configuration.

Or go to Terminal and run:

```
gksudo gufw
```

If it says it's not there then:

```
sudo apt-get install gufw
```

If it's older than 8.10 then get the .deb here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

It's a .deb so it's easy!

Then:

[ATTACH]99654[/ATTACH]

Just tick on Firewall Enabled!

Or go to Terminal and run:

```
ufw enable
```

BTW, Firestarter has not been in development since like 2005!

---

### Post by stefangr1 on 2009-01-12
Ubuntu (and basically all other linux distributions) has a very good build in firewall, that doesn't need any configuration by the average user. This is in fact one of the main advantages over windows, you just don't need to worry about this sort of things!

So, no you don't need to (and probably should not) configure anything. Just forward the appropriate ports in your internet modem.

---

### Post by ugm6hr on 2009-01-12
I would say it is probably unnecessary. Ubuntu generally has all ports closed as default.

If you find that your P2P reports that ports are closed (and hence not functioning correctly), use ufw (or gufw).

Check what port your P2P software is using (usually somewhere in Preferences).

Then:
```
sudo ufw enable
sudo ufw allow <port_number>
```

That enables the built-in ufw firewall, and opens the port <port_no>

---

### Post by bodhi.zazen on 2009-01-12
> **hoppyandy said:**
> My question is do i need to use a firewall such as firestarter to connect to the internet if my connection goes through a router with a built in firewall, i do use p2p programs which can be a pain to set up with some firewalls (Only have windows experience)due to multiple in and out connections to loads of different ip addresses, i used kaspersky when i had windows which allowed me to accept all traffic for the p2p program i was using, not sure if firestarter has that. Are there other firewalls available which may suit this better.
just wanted your experiences, opinions and recommendations.

Thanks

I think it is better to ask what do you want a firewall to do for you ?

Your router has a firewall already and a second one is probably redundant, however, there are valid reasons to run a firewall on your desktop.

---

### Post by stefangr1 on 2009-01-12
What p2p software are you using? 

Problems are usually due to not having the ports that specific p2p programs use forwarded to your pc in the internet modem (most modems have a hardware firewall build in). Also, sometimes people forget to specify a fixed ip-address for their pc. Setting up your own software firewall, would probably make troubleshooting more difficult in stead of helping you out.

If you have multiple things wrongly configured, changing one thing doesn't make things work anymore!

---

### Post by Claus7 on 2009-01-12
Hello,

I will contribute to this thread by telling you this:
if everything is working ok, you do not have to worry about anything. If it's not working as you expected it, then you have to take some steps to adjust things to your needs. I do not have experience with new versions of ubuntu, yet I think that the procedure is similar.

Back in Dapper time, when I was two years junger, there was a program that was called firestarter! This program AFAIK still exists!
The program in question enables you to open ports from your firewall. Why you do need that? You need that, because by default ubuntu and linux in general comes with its ports closed for security reasons. So if you want to use a program that has to pass by your ports, you have to allow it to do so, from firestarter.

So far so good. Yet, even if you succeed surpassing your firewall there is another impediment to your P2P programs. This is called: router. It is fearsome and cause endless sleepless nights! And if you are in my shoes (I hope not, even though they are clean and nice ones!), you have to say to IT(your router), every time you open your pc, that the ports you want to be allowed, to be allowed indeed!!!!
Back in our story, you have to allow your programs from your router as well.

In order to do ALL the above I give you this link, which points you to my attempts to solve the issues I have already described you.
[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)

I know that the temper of my answer is a little bit "poetic"(describe it as you like), yet you told us to share our experiences, so I decided to write in a more "free" format. I hope that you understand what I did, that the link I provide you is crystal clear, and that you will be able to solve your issues very easily either exactly as I solved mine or with a similar way!

Just FYI you might think of experimenting with iptables as well, yet someone else should contribute to this.

Regards!

---

### Post by cb34 on 2009-01-12
if you setup your hardware firewall properly, you dont need to set all kinds of seperate software firewall rules.. but it is still good practice in my opinion to run:

sudo ufw enable
and
sudo ufw status
this will show any rules you have, if any.

then use you hardware router firewall.

and if you ever need to modify something within linux to do with ports like for torrents, open gufw, do what you want, and close gufw.

then run sudo ufw status and you will see the rule there.

basically enable ufw from the terminal, and use the graphic frontend gufw just to deal with the rules.

another frontend to the built-in iptables, firestarter, which is not being actively developed anymore like was mentioned, i still find useful from time to time, to watch connections in real time. i just use firestarter sometimes to watch port action live.. and shows blocked ports and connection attempts also, in realtime.

---

### Post by Captain_tux on 2009-01-12
Yes, of course you do... if you're using Windows, that is ;)

---

### Post by bodhi.zazen on 2009-01-12
> **Claus7 said:**
> Back in Dapper time, when I was two years junger, there was a program that was called firestarter! This program AFAIK still exists!
The program in question enables you to open ports from your firewall. Why you do need that? You need that, because by default ubuntu and linux in general comes with its ports closed for security reasons. So if you want to use a program that has to pass by your ports, you have to allow it to do so, from firestarter.

This is only partially true.

The ports are closed because there are no listening servers.

The default firewall, however, has always been permissive. It does not need to be configured to allow P2P as you suggest.

Firestarter is no longer maintained and the default configuration tool is now ufw. gufw is the gui front end.

---

### Post by cb34 on 2009-01-12
dont mean to cause any trouble.. but why does everybody keep saying there is no listening ports by default, what about cups LISTENING or the other 2..3 services that are listening on a fresh install that each time i have to disable and remove??

---

### Post by brian_p on 2009-01-12
> **cb34 said:**
> dont mean to cause any trouble.. but why does everybody keep saying there is no listening ports by default, what about cups LISTENING or the other 2..3 services that are listening on a fresh install that each time i have to disable and remove??

The cups daemon only listens for requests from localhost. Therefore there is no problem. What are the other listening services?

---

### Post by Claus7 on 2009-01-12
Hello,

> **bodhi.zazen said:**
> 
Firestarter is no longer maintained and the default configuration tool is now ufw. gufw is the gui front end.

Things are evolving and changing! As I said, trying to make things working back then, I did exactly what I described. Opening ports both in my firewall and router. The one via firestarter and the other via port forwarding. And it seemed to be working not only for me, yet for others as well. What I can get from what you write is that someone should not change anything to one's firewall (via firestarter). Also, do I miss something, because reading this thread I'm not the only one knowing that the ports were closed for security reasons*. Or maybe this is implied in your answer as "partially". 
*EDIT:Not in this thread. Yet, I have come across this statement.

Regards!

---

### Post by cb34 on 2009-01-12
> **brian_p said:**
> The cups daemon only listens for requests from localhost. Therefore there is no problem. What are the other listening services?there are a few i dont remember off hand.. i think some smtp thing and something else.. but they say LISTENING in netstat, and to test when i set my hardware firewall so im in the Demilitarized zone, and try to attack my machine.. those ports are open, so i dont know what you're talking about its on ly on the localhost, and even if it were open only to the lan, who says i want people on my lan to have cups access by default.. or maybe not on a default setup, but with a normal first update, all that stuff is active.. i dont like it. i dont even have a printer, i purge everything so in netstat i only have bootpc:68 running for dhcp. why is cups attached to so many packages.. i always have trouble where things want to reinstall cups and a bunch of other things, and i remove most of the meta packages that do that.. just saying.. cups and a few others are buggers. there should be an option on install, if you would like to install the printer server and other things, not just do it auto. sorry to babble off topic kinda.
edit-> this is actually one of the reasons i installed debian with expert install, so i have choices... hmmm.. now that i think about it, i guess you can run ubuntu install in expert mode too and have choices.. so forget that comment.. but still there are services listening by default.

---

### Post by abn91c on 2009-01-12
if you want to test your ports go here, click on the proceed button then scroll down to the bottom of the page for the tests where is says Shield's Up Services [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by brian_p on 2009-01-12
> **cb34 said:**
> there are a few i dont remember off hand.. i think some smtp thing and something else.. 

Localhost is the machine you are sitting at. A default cupsd does not listen out for any requests from the LAN.

There is no smtp server with a default desktop install, so you must have installed it afterwards. Not to worry. Its default configuration is 100% safe.

> .. but still there are services listening by default.

There are only two. cups and avahi. Both can be purged if you desire. Should installing a package pull in either again you should examine the reason why and if you disagree file a bug report.

---

### Post by cb34 on 2009-01-12
avahi.. that's it! i hate it! like i hate cups! and i dont install anything else, i know what im doing, it installs s.hit by default man.

i port scanned my 668 or whatever port i saw at the time that cups runs on.. it was open! purged cups, re-checked.. closed.

???

---
p.s. there are TONS of packages that want to pul in cups and/or avahi.. i have to go nuts everytime fiddling with aptitude just to get some simple program installed.. lots of them, cant name names, cuz theres so many that want avahi and cups.. its not fun.

---

### Post by hoppyandy on 2009-01-14
> **abn91c said:**
> if you want to test your ports go here, click on the proceed button then scroll down to the bottom of the page for the tests where is says Shield's Up Services [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

Many thanks for all your opinions on this, just for information i have ubuntu 8.10 and i use transmission p2p i havent as yet installed a firewall and could only find firestarter in add and remove thats why i mentioned it. i have not got any problems other than i am new to linux and still windows paranoid . tested using the above link kindly sent to me and was impressed with results couldnt get through any port - so i think that answered the question.

Thanks all again for your support

---

