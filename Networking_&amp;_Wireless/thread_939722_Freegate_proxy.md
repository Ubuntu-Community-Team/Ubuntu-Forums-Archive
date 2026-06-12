---
title: "Freegate proxy"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by abhimanyu1234 on 2008-10-06
Hi... i am new to linux... i want to use freegate(windows proxy program) in ubuntu ... i use wine for it but it doesnot work can someone pls tell me how configure it right ...pls help

---

### Post by aquamammal on 2009-03-25
Same problem Here. I live in Beijng, so dudes, please help a dude out. They block the shitte out of stuff here, chavvy scum.

THanks.

---

### Post by BkkBonanza on 2009-03-25
How does using a proxy on your machine help you out in China? Wouldn't the proxy need to be outside China? 

The easiest way for you to proxy out of your machine to bypass local filtering is to use SSH in socks mode. It's real easy in Ubuntu and you don't need to install any program that's not already there by default. But you do need a ssh server runnig outside the filter (China?). And it so happens there are some pretty cheap ways to do that. 

For example, you could get the cheapest vps account at vpslink.com ($8/mo) or even cheaper a $4/mo. ssh proxy account at santrex.com. I have my own vps because I use it for hosting my sites and the ssh is just a bonus. Point is - to get around filtering you need something outside to filtered network to talk to. There's probably even free ways to do this.

Then you open a console and type, ssh -D 8080 [email]user@xxx.yyy[/email] with your userid and ip/domain name. SSH will contact the ssh server at that ip and connect. It will need your password or key and then it will start a socks proxy on that machine. 

Now just tell Firefox/Thunderbird (whatever, even skype works) to use SOCKS 5 proxy at localhost:8080 - you would have to do this anyway no matter what proxy you use. But also you can do it from System->Prefs->Netowrk Proxy in Ubuntu. If FF is set right it will pick it up.

And you're go. Now all requests get secure enrypted and go into the tunnel and come out at your remote server where they get routed out from there to wherever. Finally, be sure to set the config option in FF to tell it to route DNS queries through the proxy too because it doesn't by default.

There's a nice little gui tool to automate this all too. I think it's gSTM. See Synaptic. I use it and makes it only a couple clicks to start the proxy. Very cool.

Cheers.

---

### Post by fishfillet on 2010-01-02
> **abhimanyu1234 said:**
> Hi... i am new to linux... i want to use freegate(windows proxy program) in ubuntu ... i use wine for it but it doesnot work can someone pls tell me how configure it right ...pls help

Simply copy mfc32.dll file from a working Windows XP installation and then copy it to the .wine folder (inside the system and system32 folders) inside your home folder.

Freegate will then work with wine

---

### Post by Knowsnothing on 2010-11-04
Rock!

Thanks bunches :P

---

