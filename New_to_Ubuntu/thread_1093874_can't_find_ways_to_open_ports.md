---
title: "can't find ways to open ports"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by imparja2 on 2009-03-12
I've posted this before but couldn't load the thread I kept being redirected, so here it is again. I've now uninstalled firestarter.
I've installed firestarter and added rules to allow service to several of these ports but for some reason when I run tests to check if they're open they say they're all closed. Is there something wrong with the test or is firestarter the cause. please how can I determine what the problem is and then fix it step by step?

---

### Post by mcla0203 on 2009-03-12
Ubuntu doesn't block ports I thought.  Are you using a router?  If so does the router forward the port to the correct ip?

---

### Post by imparja2 on 2009-03-12
ok maybe not blocked but closed. I don't know what or how to access router settings. How would I be able to determine if my problem is with the router? How am I supposed to use the site you recommended?

---

### Post by sisco311 on 2009-03-12
> **imparja2 said:**
> ok maybe not blocked but definitely not open. I don't know what how to access router settings how I would I be able out if my problem is with the router.

What kind of server are you trying to setup?


To access your router open a web browser and enter the ip address of your router in the address bar of your browser.
step-by-step instructions: [http://portforward.com/]("http://portforward.com/")

---

### Post by imparja2 on 2009-03-12
I don't know because someone else put my computer together. but I'm sure I don't have an external router because I have a laptop. I must have a router if I have an ip address right?

---

### Post by bodhi.zazen on 2009-03-12
> **imparja2 said:**
> I don't know because someone else put my computer together. but I'm sure I don't have an external router because I have a laptop. I must have a router if I have an ip address right?

no , if you are directly connected to the internet your ip provider will give you an IP.

It would help if you were to describe what you are trying to do or what problem you are having that you feel you need to open a port.

---

### Post by Terry of Astoria on 2009-03-12
Well, are you on wireless or are you plugged in?
If you are plugged directly in to a cable modem or other Internet gateway, or if you are using ppp you are directly on the Internet. But if your computer is plugged in to a dsl router or is on wireless, you are behind a router. 
 For sure, [http://portforward.com/](http://portforward.com/) is a good source of info, as the post a bit earlier mentioned.
Look here on their web site 
[http://portforward.com/help/pfprogression.htm](http://portforward.com/help/pfprogression.htm)
There are lots of ways to set up your network. Please be aware of security.
[http://en.wikipedia.org/wiki/Network_security](http://en.wikipedia.org/wiki/Network_security)

---

### Post by imparja2 on 2009-03-12
I have an ethernet cord and my modem is inbuilt so I'm not using a router then. I'm trying to open ports to allow bittorrent to send me a download. When I test for to see if ports are open it says they're closed even after I uninstalled firestarter and tried to use the command 

sudo iptables- A INPUT- p tcp --dport (port number) -j ACCEPT

is it this the way to open ports or not?

Why in the test is it still saying the ports are closed?

---

### Post by ja660k on 2009-03-12
i have a simelar problem.

i have a router so my machine has a 192.168.0.14 address...
and i opened port 80 and 22 etc. on my router. and yet i cant type in my ip and my site will come up.

i have a dynamic ip... but in theory(my theory) i should be able to access it anyway? i just ahve to stay ontop of what my ip is when i reset modem?

attatched is the port forwarding thing.
what do i need on local machine to get web server running.
i have apache, mysql,php etc

---

### Post by Terry of Astoria on 2009-03-12
> **imparja2 said:**
> I have an ethernet cord and my modem is inbuilt so I'm not using a router then. 
Non Sequitur. Your facts are un-coordinated. If you have an ethernet cord, you are not using a real modem. A modem is a modulator-demodulator. Real modems are for dial-up Internet. You are referring to a cable-modem, which is not really a modem. Most cable-modems are not internal (Inbuilt?). Does your IP address start with 192. or 10. ? Because if it does, then you are behind a router. 
  And @ ja660k: want more information. Can't help without more info. As far as forwarding ports goes, forward requests to port 80 from the Internet to your apache server. That's the default port for web traffic.

---

### Post by Terry of Astoria on 2009-03-12
To test your web server you will need to access it from outside your network, from the Internet. Maybe try a proxy server or have a friend test it. If you try to access it from within, you may see the router configuration page of your router. You may be interested in looking at dyndns.org - also there are other services like them. You can run a program on your server to update your web site's DNS record with them periodically, so that your dynamic IP address can be used to host a static domain name.

---

### Post by imparja2 on 2009-03-12
Oh I'm so confused but I must not be behind a router my ip is 125.113.225.106 my computer says I have an in built modem whether I'm using it I don't know. I have a cable that goes into my computer and I think it's an ethernet it's definitely not wireless.

was the way I said the right way to open ports because I tried to open 80 that way then in the test it seemed to think it was still closed. 

so back to my original question is the test wrong? is there something wrong with the way I opened the ports:

sudo iptables- A INPUT- p tcp --dport 80 -j ACCEPT

and if not why are they still closed? afterall, I uninstalled firestarter.

thanks for the clarification:)

---

### Post by porchrat on 2009-03-12
> **imparja2 said:**
> Oh I'm so confused but I must not be behind a router my ip is 125.113.225.106 my computer says I have an in built modem whether I'm using it I don't know. I have a cable that goes into my computer and I think it's an ethernet it's definitely not wireless.

was the way I said the right way to open ports because I tried to open 80 that way then in the test it seemed to think it was still closed. 

so back to my original question is the test wrong? is there something wrong with the way I opened the ports:

sudo iptables- A INPUT- p tcp --dport 80 -j ACCEPT

and if not why are they still closed? afterall, I uninstalled firestarter.

thanks for the clarification:)

You can use iptables directly, but I was too lazy to bother to learn the commands so instead I installed ufw (uncomplicated firewall). It is a command-line application that is really easy to use and I can open ports with it no problem. You can set specific IP addresses to let through the port as well as whether it is UDP or TCP. It suits my needs just fine. It is a nice application to have.

If you're interested take a look [here]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html").

That way all you have to do to open a port would be to enter the command:
```
sudo ufw allow port <port#>
```

Where '<port#>' is the port you wish to open.

Don't know if it will help you, but it sure made my life easier.

Also you can use port scanner websites to find out whether or not you have a port open. I used to have a nice port scanning utility on Windows that you could use from another machine on a network (probably not a great help to you though), I forget the name though.

EDIT: Also you say a cable comes out of your computer. Where does that cable go? Into the wall? or into a router? (a router is a plastic box which should have a manufacturers name etc. on it and should also probably have the word 'router' on it somewhere, it's ports will probably be labelled with things like 'WAN', LAN1, LAN2' etc...sorry if this is too simplistic for you I just like to start as low down as possible when helping someone and work my way up)

---

### Post by bodhi.zazen on 2009-03-12
To be honest there are tow issues in this thread.

The first is you need to understand your hardware. A modem and an ethernet card are not the same thing. Opening ports is very different between a direct connection and a router.

So if you do not know your hardware, and you do not know if you are using a router, that is the first step, know your hardware.

Second we need to learn how to use a firewall and we need to know that your IP provider is not blocking peer-to-peer file sharing or torrents. Many IP providers do, so if that is the case it does not matter how you configure your computer the traffic is blocked by your internet provider.

So the next step is to contact your ip provider and see if they are blocking your peer-to-peer connections. While you are at it you can inquire about your connection.

Please do not hijack threads, it is considered rude. So, ja660k, start your own thread but make sure you also know your hardware.

Last if you are going to configure a firewall you will need to learn at least a little about how they work.

With iptables, order of the rules counts, so you can not simply append rules without knowing what the previous rules are :twisted:

I suggest you look at :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw") 

If you want a GUI I suggest you use either gufw or guarddog. Firestarter is no longer maintained and guarddog has more extensive built in help ;)

---

