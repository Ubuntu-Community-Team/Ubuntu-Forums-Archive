---
title: "Web browsing - strange behaviour.. Please help"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by syscode on 2008-07-10
Am new, very new, to ubuntu... Installed ubuntu 8.04 last night and this
problem wouldn't go..

All seems well in terms of internet connection, IM chat is fine, DNS and
ping are fine -
apart from firefox only able to connect with a few sites..

I can get google.com for example - but not ubuntu.com. I am able to got
connected with: diamondcard.us (ekiga), and the bbc (front page and weather
- but not news..)

After a bit of a search on the ubuntu help site, it seemed that maybe my
problem was solvable by adding the line 
net.ipv4.tcp_default_window_scaling = 0
to etc/sysctl.conf

I added the line to the top of the file - but it didn't make any
difference.

Any idea what may cause this behaviour and how to fix it..?

Not sure if relevant:

The machine is dual boot.
Internet connection is via ethernet cable to a router.


Many thanks!

(I really like ubuntu - please help kick XP off my box..)


This is a rewarding/update on a post from yesterday:
[http://ubuntuforums.org/showthread.php?t=854842](http://ubuntuforums.org/showthread.php?t=854842)

---

### Post by ModelM on 2008-07-10
On the sites you cannot reach, are you getting a 404 error or what?

Are you connecting via ppp dialup, or are you connecting through a wired/wireless network card to a DSL or cable modem?

---

### Post by syscode on 2008-07-10
Good points, ModelM.

Yes, I forgot to mention that the connection is an ethernet cable to a router.

The browser keeps trying to load the sites.. I haven't noticed any 404s, but either timed out messages, or that it just keeps trying to load..

---

### Post by ModelM on 2008-07-10
The first thing I'd try is a different browser, and I mean *really* different. I'd try an ascii browser. I think w3m is included in the stock install, or you could install links or, my favorite, lynx.

Lynx has no scripting, java, flash, or any other foo-foo. It's just a browser. If it can load a site your other browser can't, that's a pretty good clue...

---

### Post by superprash2003 on 2008-07-10
ping the sites which arent loading and get the site's ip and enter the ip  in firefox or whatever browser you use.. and if the webpage opens, then it could be a dns issue . so you could try changing to opendns servers . their ips are 208.67.222.222 and 208.67.220.220 .. if you still face problems, then you could try changing MTU values

---

### Post by syscode on 2008-07-11
ModelM thanks for the suggestion.

I tried to load lynx, but had to download it via the app installer - but that showed that it couldn't connect to server. Same case happend with epiphany.

Therefore I conclude that despite the fact I can ping sites and see my DNS details, something IS more fundamentaly wrong with my internet connection on ubuntu..

Indeed, going to network tools / devices / ethernet interface (eth0) / configure - gave me "the interface doesnot exist Check that it is correctly typed and that it is correctly supported by your system"..

So Maybe its my Ethernet interface?

I searched for possible solutions here, got:
[http://ubuntuforums.org/showthread.php?t=843406&highlight=interface+doesnot+exist+ethernet&page=2](http://ubuntuforums.org/showthread.php?t=843406&highlight=interface+doesnot+exist+ethernet&page=2) as the nearest possible problem to main.

However, since ipconfig on XP shows:
Dhcp Enabled. . . . . . . . . . . : Yes
It seems I am not on a bridged mode..

superprash2003, Thanks! - per above, and that attempting to use ip didn't bring sites up, maybe its another indicator I need to know whats wrong with the detection of my ethernet cable..

BTW, what is MTU..?


Hope someone can help, though maybe I should really open another, new issue.. 

Cheers!

---

### Post by superprash2003 on 2008-07-11
regarding MTU, you could try this [http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html](http://prash-babu.blogspot.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by syscode on 2008-07-11
The tutorial looks promising, superprash2003 - thanks!

Only thing is that interfaces document is empty..(!!)

I did the ifconfig and know the system looks for eth0.

Should I just type in that document:
 iface eth0 inet dhcp
mtu 1492
???

Thanks!

---

### Post by syscode on 2008-07-11
OOOOOps!!! Sorry.. I did a typo..

Wrote gedit etc/network/ instead of gedit **/**etc/network/

Will try this fix idea now..

---

### Post by syscode on 2008-07-11
OK.. I have now tried all the MTU number options, and no joy..

In case its of any relevance, my interfaces file looks like:
auto lo
iface lo inet loopback
iface eth0 inet dhcp
mtu 1452
auto eth0

Maybe its something else to do with Ethernet interface error I get..?

---

### Post by ModelM on 2008-07-11
Please post the contents of your

/etc/resolv.conf

file.

---

### Post by syscode on 2008-07-11
ModelM, the contents are:
search lan
nameserver 192.168.1.254

Also, I have tried to get help on the IRC channel.. Was asked to get the following information and was told it showed everything is OK.. (Just in case it is needed to assess what is going on wrong on my ubuntu installation..)

Inforamation for sudo dhclient eth0, is  @ [http://paste.ubuntu.com/26670/](http://paste.ubuntu.com/26670/)

Inforamation for ifconfig; route -n is @ [http://paste.ubuntu.com/26672/](http://paste.ubuntu.com/26672/)

Inforamation for ifconfig eth0; route -n  is @ [http://paste.ubuntu.com/26673/](http://paste.ubuntu.com/26673/)

Many thanks for looking into that!

I hope something solves the network connection, because I really don't want to give up on ubuntu on my pc.

---

### Post by ModelM on 2008-07-11
In the file

/etc/dhcp3/dhclient.conf

add the line:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

just below line 18 or so. The placement isn't critical, pick a spot where you can find it again easily, spaced out with a couple of blank lines.

You'll need to be root for this so the command in a terminal would be:

sudo gedit /etc/dhcp3/dhclient.conf

after the job is complete, reboot & check your /etc/resolv.conf again. it should have changed & included the two numbers in the line above. And, as an added bonus, things should work. I hope...

---

### Post by syscode on 2008-07-11
Thanks ModelM.

I have done as you said, and indeed resolv.conf has changed to:

search lan
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.1.254

However, I am still unable to browse... :(

Shame its so hard..

---

### Post by ModelM on 2008-07-11
Let's rewind a bit. Tell us again what *does* work. I think I may have an idea...

---

### Post by syscode on 2008-07-11
OK, ModelM. Lets rewind...

I can do:

* Ping.

* Tracerout. (Though its **very** slow..)

* Browse via firefox google.com and bbc.co.uk (but not the news site, e.g. news.bbc.co.uk).

* Connecting to the router, it shows the name of the router in the title of the web page - but nothing else.

* It shows a DNS.

Hope this gives a better idea of the problem..

Thanks!

---

### Post by ModelM on 2008-07-11
What brand/model router is it?

---

### Post by syscode on 2008-07-11
The router is o2 wirelessbox manufactured by thomson telecom.

I see from this post [http://ubuntuforums.org/showthread.php?t=787271&highlight=thomson+router](http://ubuntuforums.org/showthread.php?t=787271&highlight=thomson+router) - that the router can connect fine..

Wish I could get to worry about the security, like the above guy with o2 router..

---

### Post by ModelM on 2008-07-11
If you can ping by name then DNS is most likely not the culprit. Can you successfully ping the sites which are unreachable in the browser?

And, while we're pinging, what are your ping times to, say, google.com?

And I think you said that synaptic does *not* work, is that correct?

Also, make sure that all firefox plugins and addons are disabled 'till we get this sorted.

---

### Post by syscode on 2008-07-11
Thanks ModelM for keeping up with this!

Yes, I can ping sites that can not be browsed.

Its an avarage of 109ms to ping google.com

Synaptic can not download apps to install.

Yes, all plugins and addons are disabled on firefox.

Thanks!

---

### Post by ModelM on 2008-07-11
Okay, now pick a site you cannot reach in the browser, how about news.bbc.co.uk - and what is your ping time for that?

---

### Post by syscode on 2008-07-11
news.bbc.co.uk is 18.77ms

Hummm... Just noticed that it is also the case that some sites are not pinged at all.. like independent.co.uk...

---

### Post by ModelM on 2008-07-11
Did I get it right that you said that when you type in the address of the router in order to connect to it, that you get an incomplete web page, with the router name & nothing else?

And, in a terminal type:

w3m news.bbc.co.uk

and lets see what happens...

---

### Post by syscode on 2008-07-11
Thanks ModelM! 

OK..

news.bbc.co.uk gives - contacted, waiting for reply.

google.com - a very quick splurge of letters, something about cookies from what I managed to read, and then - contacted, waiting for reply.


bbc.co.uk - the text version of bbc.co.uk homepage comes up fine. If I try browse from the links - I get "contacted, waiting for reply."

---

### Post by ModelM on 2008-07-11
It's really beginning to look like something is blocking/diverting some, but not all, of the http traffic.

Tell us again what happens when you try to connect to the router...

---

### Post by syscode on 2008-07-11
Hummm... Is there some sort of firewall operating hidden all on its own by default?

When I try the router, it takes a while, and then I see the name of the router on the title page. It keeps doing the motions as if trying to load the page - but it doesn't time out..

Hope this is a bit clearer..

---

### Post by ModelM on 2008-07-11
Just to make sure I'm looking at the correct pictures here, you get the blue band with O2 & the bubbles, but none of the rest?

---

### Post by syscode on 2008-07-11
Not entirely sure what you mean.. If you refer to the ISP, its [http://broadband.o2.co.uk/home/packages.jsp](http://broadband.o2.co.uk/home/packages.jsp) I am on the standard package..

---

### Post by ModelM on 2008-07-11
If you are unable to even connect to your router, I'd reset it. You'll need a paper clip or similar tool. On the back, near the word "reset" you should find a small hole. Press the tool into this hole 'till you feel a slight, mechanical "click". Hold the tool in place 'till you see the power light go red, then release.

This should reset the router and maybe put us back in business...

---

### Post by syscode on 2008-07-11
OK.. Have done a reset - but I am afraid its no joy, ModelM. Doesnt make any difference...

---

### Post by ModelM on 2008-07-11
If you still cannot connect to the router after a reset this narrows the possibilities considerably. I'm guessing that you are connecting via wireless, correct?

If you are connecting via wireless, disconnect the power from the router and try a few tests again. This is to ensure that you are, indeed, connecting to your router and not another one nearby. Try to connect to the router again with it unplugged.

---

### Post by syscode on 2008-07-11
I am using an ethernet cable.. Am not wirelessly connected.. I have  turned the router off and on..

---

### Post by ModelM on 2008-07-11
You are connected to the router by cable & cannot properly communicate to/from the router via http even after a router reset. I think your router is defective. I'm out of ideas other than to give a call to the folks at O2.

Sorry I wasn't able to help you, mate.

---

### Post by syscode on 2008-07-11
Well.. Thanks for trying!!

I did call o2 broadband a fair few times - but they don't support linux. only macs and windows.. So had to give that up as well..


You've been very kind, ModelM - THANKS, and all the best!!

---

