---
title: "Accessing freenode Via SSL or hide IP?"
date: 2011-08-05
forum: New to Ubuntu
---

### Post by honeybear on 2011-08-05
Hello,

Freenode is not so secured since it leaves your hostname/ip visible and so on. 

Then how to make it, with which linux software?, such as accessing freenode Via SSL or hide IP?

Cheers

---

### Post by bodhi.zazen on 2011-08-05
Most people use cloaks. 

If that is not sufficient , see [http://freenode.net/faq.shtml#sslaccess](http://freenode.net/faq.shtml#sslaccess) or ask on #freenode

---

### Post by honeybear on 2011-08-05
> **bodhi.zazen said:**
> Most people use cloaks. 
**(1) **
If that is not sufficient , see [http://freenode.net/faq.shtml#sslaccess](http://freenode.net/faq.shtml#sslaccess) or ask on #freenode
This is complicated.
[http://freenode.net/irc_servers.shtml#tor](http://freenode.net/irc_servers.shtml#tor)

**(2) **
How to use cloaks in a simple manner after doing:

```
    /network add -nick <nick> -realname <realname> freenode
    /server add -auto -ssl_verify -ssl_capath /etc/ssl/certs -network freenode chat.freenode.net 7000
    /save
```


both methods are very complicated: [http://freenode.net/faq.shtml#cloaks](http://freenode.net/faq.shtml#cloaks)

**(3) **
How to check if my ip is hidden? 
I tried 
> /dns myipaddress 
but it does not give anything


**(4) **
This solution is also too complicated:
> 


**(5) Another way, also too complicated **
Situation - you want to connect to irc server XYZ.com on port 6667

as root :
1) apt-get install polipo tor
   - now you should have installed (among others also) commands : polipo, tor, torify
   - all you need is default settings
2) run  : /etc/init.d/polipo start
3) run  : /etc/init.d/tor start
4) run  : socat TCP4-LISTEN:4242,fork SOCKS4A:localhost:XYZ.com:6667,socksport=9050 
4) run  : torify irssi

voila.... now you have irssi, if you look at the list of connected users on the channel (/who) you should see an unusual ("torred") address of you ;-) Enjoy !
Beware, some IRC servers detects TOR servers and refuse to connect you (in fact, it is not a detection of the TOR server, it's just TOR network is not usually used for, let's say "politically correct" behavior, hence the server can get ban for flooding or something similar, so it is breaking of the rules and not the fact, that it is a TOR server, or it has anything to do with onion routing).



**(6) The alternative using Tor, also complicated**
> 

sudo aptitude install tor irssi screen

All necessary dependencies will be resolved, and the daemons started. Now pull up a terminal and type:

screen torify irssi

You will have the default irssi screen staring you in the face waiting for a command. Normally at this point, you would type /connect irc.freenode.net or something similar. However, irc.freenode.net is not a hidden url, and thus will not take you to the hidden service. Because Tor is looking a localhost as a proxy, Freenode will tell you that you are banned from the server. The IP that Freenode will show, as it should, will be 127.0.0.1. So, there must be another way to connect. There is, and you have to use the hidden service.

Currently, the url to the hidden service on Freenode is mejokbp2brhw4omd.onion. So, you could type that in your irssi prompt, and connect. However, that url, if you ask me, is somewhat a pain to type let alone recall. There is an easier way. First, detach the screen by typing ctrl+a d. Back in the terminal:

sudo vim /etc/tor/torrc

&#8230;and add mapaddress 10.40.40.40 mejokbp2brhw4omd.onion anywhere in the file (I added it to the very top). Restart tor.

sudo /etc/init.d/tor restart

That IP address is a little easier to recall and type, so from here, reattach your screen with screen -r and now you can type /connect 10.40.40.40 at the irssi prompt. However, this is still more of a pain than I would like. Luckily, irssi is the single most configurable IRC client out there. We can add a shortcut to point to that address. In the irssi client:

/server add -auto -network freenode 10.40.40.40 6667

Now, when pulling up irssi, you will automatically connect. If for any reason you get disconnected, /server freenode will connect you to the hidden service. If your nick is registered with NickServ and you need to identify, then something like this might be a bit more appropriate:

/server add -auto -network freenode 10.40.40.40 6667 (password) (nick)

Now just connect:

/server freenode

Now that you are connected, you can join channels as normal, and move about with ease. In a channel, run a /whois nick (substituting for your nick), and you will see something similar to i=aaron@gateway/tor/x-ef387c8e0932dd32. That last string being a random encrypted string of characters showing your exit Tor node. This is a hell of a lot better than n=aaron@aaron.fttp.xmission.com or something else more revealing. Also, klines (kicks and bans) are much more difficult as they can now only be based on nick. As we all know, changing a nick is easy, and there is an infinite amount combinations. However, this doesn&#8217;t mean that network staff can&#8217;t handle the situation.

The only thing you may notice is lag. Because we are now connected to 3 Tor nodes plus a random Freenode server, we are going to have some latency problems. This is normal with Tor. Generally, I have an average of 5 seconds lag. This can be a little annoying, especially when in a meeting on a channel.

One problem. Now that you are connected via Tor to the Freenode hidden service, channels like to block Tor users because of abuse. I don&#8217;t like this, because the honest people that just want to stay anonymous (the large majority of users), are punished because of the few who enjoy abuse and trolling. It was a shock to me to find #ubuntu and #ubuntuforums block tor users. Here, I wanted to join two channels to help where I could, and I was blocked.

---

### Post by bodhi.zazen on 2011-08-05
OK, well I guess you have answered your own question, it is too much hassle for you.

FYI you can get a cloak if you are an Ubuntu member.

[https://wiki.ubuntu.com/Membership](https://wiki.ubuntu.com/Membership)

[https://wiki.ubuntu.com/IRC/Cloaks](https://wiki.ubuntu.com/IRC/Cloaks)

Otherwise pick one of the options you have cited.

As this is not really an Ubuntu support question, and as your question if asked and answered, I am going to close this thread now.

If you have further questions, ask on #freenode.

---

