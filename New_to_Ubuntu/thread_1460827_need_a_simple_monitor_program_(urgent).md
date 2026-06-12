---
title: "need a simple monitor program (urgent)"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by azerty123 on 2010-04-23
Hello guys

I recently built a lan with several computers, and i want to view and observ what my children are doing in their computers (running windows)

Iam an absolute beginner with ubuntu and i want a** simple** tool to [COLOR=Red]control[/COLOR] their computers, and [COLOR=Red]cut[/COLOR] the net from them if necessary

any help? 
#sorry for my english, its not my mother language

thanks in advance

---

### Post by tomcheng76 on 2010-04-23
i don't think you can do it in your LAN machine (Ubuntu)

but i believed that you are using a router. So, you can open up the router admin page in firefox and disconnect the wan function if neccessary.

---

### Post by kanikilu on 2010-04-23
I suppose you could install VNC server on their computers and check in with the client on your computer. Although "cutting the net" would probably cut you off too.

Other options include collecting logs and data with Wireshark, but you're unlikely to be able to catch something in real time and deal with it immediately.

Alternatively, you could setup a machine as a firewall and only allow sites that you approve of...

---

### Post by azerty123 on 2010-04-23
thank you brothers for your replies

i've found tuxcut similar to netcut
[http://irvian.blogspot.com/2009/11/tuxcut-netcut-on-ubuntu.html](http://irvian.blogspot.com/2009/11/tuxcut-netcut-on-ubuntu.html)

Am not that brave to install it, because i googled for few minutes and i didn't found it neither@ sourceforge nor@ubuntu software center

any suggestions?

---

### Post by arrrghhh on 2010-04-23
Honestly the best way to catch stuff in real-time is with a filter, proxy, what have you.

The *easiest* would be to setup OpenDNS on your router, and use their filtering service.  I am in no way affiliated with this company, I just use their services and have been happy with the results.

Now if you want, you can put the DNS settings on their individual machines, but they could always modify those settings unless you block them access with a policy or some such sort.

The other option would be something like a squid proxy or filter thru your Ubuntu box, but that gets complex and I would not be much help there, as I tried setting up squid and failed miserably :(

---

### Post by azerty123 on 2010-04-23
[B]thank you so much for the usful info arrrghhh

[/B]         > [COLOR=DimGray]Honestly the best way to catch stuff in real-time is with a filter, proxy, what have you.

+

The *easiest* would be to setup OpenDNS on your router, and use their filtering service. I am in no way affiliated with this company, I just use their services and have been happy with the results.[/COLOR]
[B]how can i do so? and how about that "tuxcut"?
[/B]

---

### Post by arrrghhh on 2010-04-23
> **azerty123 said:**
> [B]thank you so much for the usful info arrrghhh

[/B]         [B]how can i do so? and how about that "tuxcut"?
[/B]

I've never used tuxcut, it seems like that would take a lot of work on your end.  The suggestion I made runs 24 hours a day, without any additional user intervention once it's setup.

Do you understand how DNS works?  Go to the opendns.com site, they have very good directions on how to get it setup.  You'll need a username and password setup with them, it's free.  Then once you have your router setup to use opendns (again, they have very good instructions on their site, for most major routers) you can setup your filtering options.  You can have opendns filter by types of sites (keywords, metatags, etc) by choosing categories to block (which is probably what you want for your kiddies) - or you can block individual websites.  Site-by-site isn't going to work really, I recommend the category blocking for kiddies.

---

### Post by jbiggs12 on 2010-04-23
I've used Squid for a while and absolutely loved it. Just install squid on a computer that's constantly running (it will need to be running if you plan on accessing the internet through it) by getting on a shell and typing ```
sudo apt-get install squid
```

And from there, you can look at various websites that teach you how to configure the software. It's a bit tricky at first, but you can easily get the hang of it: block websites for certain computers, block certain computers completely, etc etc.

Cheers, Jack

---

### Post by MooPi on 2010-04-23
Sounds like the OP wants supreme/ultimate control over the kids connection foremost. The instructions on tuxcut should work well. Open a terminal:
```
wget http://bitbucket.org/a_atalla/tuxcut/downloads/TuxCut-3.2_all.deb
``````
sudo apt-get install arp-scan
``````
sudo apt-get install dsniff
``````
sudo dpkg -i TuxCut-3.2_all.deb
``````
sudo tuxcat
```That last command is directly from the instructions but looks like a typo( tuxcat versus tuxcut)

[            ]("http://bitbucket.org/a_atalla/tuxcut/downloads/TuxCut-3.2_all.deb")

---

### Post by arrrghhh on 2010-04-23
I was just presenting him with options that did not require constant monitoring.  Pretty much impossible to monitor kiddo's connections 24/7, and OpenDNS affords that.

A squid proxy will as well, but they're NOT easy to configure, and to my knowledge keyword/categorical blocking still not possible.

---

### Post by fromthehill on 2010-04-23
if you want to constantly see what they are doing it probably a lot less time-consuming if you put the computers in the same room where you are.

I don't know how old your children are. if they are in their teens secretly spying on them can seriously backfire if they find out
you should talk to them about the dangers on the internet and tell them if they see something like that they should talk to you about it

---

### Post by achase79 on 2010-04-23
dansguardian is a filtering and squid configuration tool.  You can limit access by content, time, or specific sites by setting up rules so you don't have to constantly observe the entire activity.

---

### Post by azerty123 on 2010-04-24
now, the problem seem a whole lot smaller!
thank you guyz for your time&help, i appreciate it

---

