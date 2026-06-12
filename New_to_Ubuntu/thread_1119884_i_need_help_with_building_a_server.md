---
title: "i need help with building a server"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by pengin on 2009-04-08
basically i want to host a web forum and am completely new to servers, i need to start from scratch as i know nothing. so can you guys help me build a ubuntu server?

---

### Post by sailthesea on 2009-04-08
I don't know about the software you'll want to use, there are server specific distributions of all kinds available 
 For a basic self build you will need:
Some sort of computer, an old desktop is a good starting point (bigger is better) and any RAM, HDDs, expansion cards you can find In fact whatever you can get your hands on Hardware wise its all useful stuff
 A good high speed Internet connection obviously
 A wireless router if needed for access
 Keyboard and monitor for setup at least
 Maybe an additional Power supply unit
 Lots of leads and cables
 Somewhere dark and quiet and SECURE for it to live

 When you have a big pile of stuff put it all together and when you get a working setup Install your software 
 A server relies on speed and capacity sacrifice sound/video in favour of a text interface and make access your priority
 Building a machine isn't at all difficult Google away for info
 Basic precautions 
Power off when inside any machine
Ground yourself with a wrist strap before handling any components
Check Check Check again before testing for the first time (power connections especially)
And Good Luck!:p

---

### Post by achase79 on 2009-04-08
phpbb2 (a forum package) is available from the repos and it's dependencies will help get you a longer way to a usable web forum.  Someone else is going to have to help you with web server administration though.

---

### Post by PreviousN on 2009-04-08
> **sailthesea said:**
> 
Some sort of computer, an old desktop is a good starting point (bigger is better) and any RAM, HDDs, expansion cards you can find In fact whatever you can get your hands on Hardware wise its all useful stuff
 A good high speed Internet connection obviously
 A wireless router if needed for access
 Keyboard and monitor for setup at least
 Maybe an additional Power supply unit
 Lots of leads and cables
 Somewhere dark and quiet and SECURE for it to live


Whoa, whoa whoa! Slow down. We don't even know everything about what this person is trying to do. First of all, is the OP *only* going to run a web forum? How professional are you looking to go? If you need this for a business, I'd suggest looking into something that costs money, like a Virtual private server hosted solution. If this is for a small community of friends or a game clan, or something not "mission critical" you may not need professional hosting. You could theoretically do everything for free in that case. Would I recommend it? Not really, but it can be done. 

So, what do you need? Something professional, or something small for friends and family? How scalable does this need to be?

Also, sailthesea (no offense), a wireless router, wtf? You don't need a wireless router for a webserver. lol.

---

### Post by sailthesea on 2009-04-08
Non taken!;)
 I suppose I should have asked for a bit more info, but I'm a mechanic and when I see "build" I start thinking silly thoughts
 So Pengin if you give an idea of the scope of what you want to do I'm sure you'll get lots of useful help instead of me trying to get you build a Collosus in your garage!

---

### Post by MrWES on 2009-04-08
> **pengin said:**
> basically i want to host a web forum and am completely new to servers, i need to start from scratch as i know nothing. so can you guys help me build a ubuntu server?


Here is a guide I've recently used to put together a server running Hardy Heron 8.04.2 LTS.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

I only made it into a file and print server, but the guide was very useful. Might I also recommend these sites:

[http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts")
[http://ubuntuforums.org/showthread.php?t=254149]("http://ubuntuforums.org/showthread.php?t=254149")
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/")
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

Good luck,
Bill

---

### Post by PreviousN on 2009-04-08
My god. I'd love my own personal garage collosus! :-) Maybe I could terrorize the neighborhood with it... or use it to get a job :-). Anyways, since I know if I don't do this now I'll never get to it. Here's some help:

The free solution: Running a webserver on your own desktop computer. Difficulty: Medium to hard. Depending on experience and features needed. 

[LIST]
[*]First of all, check that you aren't breaking usage limits given by your ISP. Many block port 80 (the typical http port). If that's the case, you could use a nonstandard port. Not as professional, but it gets the job done.
[*]Second of all, if you want to be able to type a url into a web browser rather than an ip addres, head on over to [www.no-ip.com](www.no-ip.com), and set yourself up with free dynamic dns.
[*]Then, get the web server running. Install LAMP on your computer.Do this by following this guide: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop). Its pretty simple. Essentially a one click install. Tweak the setting if you need to host on a non standard port. That's slightly harder, to do that, just edit a text file. I can't remember the actual file, since its been a while since I've done it, but google has answers. Just search for "apache different port" For fun, I always choose 1337 :-) 8000 is common too. 
[*]If you're connected through a router, remember to forward the port! If you've set up your server to run on port 1337, forward 1337. You'll have to forward port 80 if you've chosen 80. You should then have your web server reachable on your local network. Try it! Open up a laptop and type in the ip address of your web server into the url bar in firefox. You should get a page back that says "Apache" "It Works!" or something like that. 
[*]Next, install phpbb. This is a web forum package that runs via apache. A post above mentioned how to do it. I think its sudo apt-get install phpbb. Really easy. It might be a little bit more complicated than that, meaning that you have to enter some information, such as admin name, etc. etc., but in general, not too difficult. 
[*]There you go. A free forum running on your desktop computer. Remember, if you turn off your computer your forum turns off too. If your IP changes, you'll need to update the dynamic dns. Some routers have the option to automatically update the ip address if it changes. 
[*] To access the forum, open a web browser, and type "localhost" in the address bar. If you chose a non standard port, type localhost:1337 or the port you chose.
[/LIST]
The reason why I asked what you needed, was if you needed it for local lan parties or family/etc. then you wouldn't need to go through the hassle of setting up a dynamic dns or port forwarding. 

Now, the professional solution. This is quite a bit easier, in my opinion. But much less entertaining:
[LIST]
[*] Do a web search for "web hosting service"
[*] Sign up, pay, and dig through all the crap. Get yourself a domain name, sometimes provided for free with the hosting deal.
[*] Install phpbb. Some web hosting services offer 1 click install of forums. 
[/LIST]

If its any kind of professional project, and needs to be accessed by more than say... 5 users. I'd go the money solution. Its usually guaranteed up for 99% of the time, much easier to install new services on (with 1 click installs, and whatnot) and just overall more professional. And its generally cheap. Like 5-6 dollars a month. 

One downer is that going professional you have to be careful what you buy. If you go with a shared hosting provider, you are unlikely to be able to survive any digg or slashdot effect. If you pay for a business ISP, you can build and run your own server, and will likely be able to survive it. 

Good luck. Hope ANY of this helps. If you have further questions I'm sure a bunch of people will be willing to help out.

---

