---
title: "Firesheep and firewalls"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by loungedaddy on 2010-10-25
Is a firewall program, like Firestarter, helpful at all in protecting against something like Firesheep? 

That plug-in has me kinda nervous, and for the time being, I am going to be using coffee shops that all me to use a wired connection to get online. Yikes!

---

### Post by ivarn on 2010-10-25
Heh lol. No, a firewall protects you against hackers (people that breaks into your computer to mess it up).
Don't worry.

---

### Post by The Cog on 2010-10-25
A firewall will not help. That plugin just sniffs your connection to the web site. It doesn't talk directly to your PC at all. You just need to be careful about having your connections overheard.

---

### Post by Paqman on 2010-10-25
No, Firesheep is a packet sniffer apparently. It takes a peek in the actual packets of data whizzing back and forth between your machine and your wifi access point. Installing a firewall on your machine won't help if you're sending out all the packets unencrypted.

---

### Post by OldDinosaur on 2010-10-25
Firesheep is, it seems, a sniffer that takes advantage of some SSL issues that social networks have. What they are I have not (yet) been able to determine. Nor what type of defenses the users of the social networks might be able to implement on their own. It appears that the creator of Firesheep is trying to drive these social networks to better security practices by making widely available a way to breach the security. I'd like to slap him, personally.

---

### Post by oldos2er on 2010-10-25
Firestarter is not a firewall, it's only a configuration program for iptables.

---

### Post by Windows Nerd on 2010-10-25
Not to mention that public WIFI can always be sniffed if it is unencrypted data with a man-in-the middle attack. Or if someone has a WIFI pinapple: [http://revision3.com/hak5/pineapples](http://revision3.com/hak5/pineapples)

---

### Post by The Cog on 2010-10-26
> **OldDinosaur said:**
> Firesheep is, it seems, a sniffer that takes advantage of some SSL issues that social networks have. What they are I have not (yet) been able to determine.
I think the issue is that they only use SSL for the initial login dialog where the username/password is exchanged. After that, these sites set a session cookie that identifies that particular login and then revert to unencrypted http for the rest of the session. Firesheep listens to the unencrypted http conversation to get the cookie after the login is complete, which it then uses to impersonate the real user.

---

### Post by 3rdalbum on 2010-10-26
A firewall stops incoming connection requests from reaching your running programs that might be listening for those connections.

Firewall don't have any concept of "good or bad", just whether you are allowing this port number or not.

So no, a firewall does not stop any attack like Firesheep. It's not relevant.

---

### Post by Elycian on 2010-10-26
Alright, so lets stop saying "no a firewall won't help you" and come up with some productive ways the OP can actually protect themselves from this firefox extension.

... I got nothing...

---

### Post by Weevil on 2010-10-26
> **OldDinosaur said:**
> I'd like to slap him, personally.

I'd like to hug him, personally. After playing around with this I'm really glad I have the HTTPS Everywhere plugin installed and am one step closer to finally closing my leaky hotmail accounts forever.

---

### Post by Windows Nerd on 2010-10-26
It seems that someone has found a simple fix:
[http://techcrunch.com/2010/10/25/firesheep/](http://techcrunch.com/2010/10/25/firesheep/)

Just Use HTTPS everywhere, and/or noscript. The former encrypts your session, whilst the latter stops the Firesheep script from running on your computer.

I confirmed the latter workaround with my brother: I have noscript on and it prevents him from pulling my data over our wifi.

---

### Post by Weevil on 2010-10-26
HTTPS Everywhere can only do that on sites that support https. NoScript cannot stop FireSheep from sniffing cookies.

---

### Post by wordymusic on 2010-10-26
To defend against firesheep, the accepted fix for Windows firefox users is Force-TLS (firefox extension). I'm using it and it appears to be working fine, which is to say that when I use it I can't detect my own logins on firesheep onthe same or a different computer. 

There's a theoretical solution for windows Chrome called KB SSL Enforcer but I've been using it and it doesn't appear to be a functional solution. Hopefully it'll grow some extended functionality now that firesheep is making news. 

I believe that firesheep, TLS, and KB do not work on *nix. However, firesheep can of course still pick up unencrypted data sent from a *nix machine. Does anyone know if this is true? 

Also, y'all should join the effort to get firesheep working on linux. See below.
```
git pull -v [http://github.com/codebutler/firesheep.git](http://github.com/codebutler/firesheep.git)
```

Update: firesheep is working for linux, although there's no "plug and play" of it yet. Check out the comments here for how-to and code. 
[http://github.com/codebutler/firesheep/pull/31](http://github.com/codebutler/firesheep/pull/31)

---

### Post by heyandy889 on 2010-10-27
Hi.

I am a teacher for a college class called First Year Seminar. 1 of my students is slick with computers, but the other 18 students are average computer users. I am wondering if I should warn them about Firesheep.

We have a campus-wide wireless network. I am pretty sure it is an unsecured, unencrypted wireless network. I hope my students already know not to do online banking on a public Wi-Fi network, but should I also caution them against using facebook, Amazon, and twitter?

---

### Post by wordymusic on 2010-10-27
> **heyandy889 said:**
> I am wondering if I should warn them about Firesheep.

We have a campus-wide wireless network. I am pretty sure it is an unsecured, unencrypted wireless network. I hope my students already know not to do online banking on a public Wi-Fi network, but should I also caution them against using facebook, Amazon, and twitter?

Yes, definitely warn them. Even the "slick" one. "Slick" doesn't always equate to guru, lol. 

Don't caution them to not use facebook, etc on public wifi; that's silly and probably counterproductive. But DO caution them to use SSH at all times when they are logging into something, especially when logging in on university/public wifi. 

To this end, they can use these two firefox plugins to force SSH in their browsing sessions. 
[https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)
[https://addons.mozilla.org/en-US/firefox/addon/12714/](https://addons.mozilla.org/en-US/firefox/addon/12714/)

---

### Post by mathgeek2000 on 2010-10-27
> **wordymusic said:**
> To defend against firesheep, the accepted fix for Windows firefox users is Force-TLS (firefox extension). I'm using it and it appears to be working fine, which is to say that when I use it I can't detect my own logins on firesheep onthe same or a different computer. 

Some of what I've read indicates there could be a sniffer somewhere outside of the immediate wireless network (Free Unencrypted WiFi). Thus an end-to-end SSL encryption is necessary to ensure encryption.

For example A Tor user could install firesheep and look at sessions going through his exit node. Recommended Defences: HTTPS Everywhere by the [EFF]("http://www.eff.org"). or Force-TLS, as you say.
 
I've had some success, and some failure with Force-TLS. Toastmasters Club Websites provided by Freetoasthost are http: by default, (no encryption) and they seem to work well with Force-TLS, but my Comcast based web mail fails when I use Force-TLS.

---

### Post by jtarin on 2010-10-27
While not the ultimate fix using a VPN will go further than anything stated so far.

---

### Post by remoryl on 2010-10-28
> **wordymusic said:**
> Yes, definitely warn them. Even the "slick" one. "Slick" doesn't always equate to guru, lol. 

Don't caution them to not use facebook, etc on public wifi; that's silly and probably counterproductive. But DO caution them to use SSH at all times when they are logging into something, especially when logging in on university/public wifi. 

To this end, they can use these two firefox plugins to force SSH in their browsing sessions. 
[https://www.eff.org/https-everywhere](https://www.eff.org/https-everywhere)
[https://addons.mozilla.org/en-US/firefox/addon/12714/](https://addons.mozilla.org/en-US/firefox/addon/12714/)

You don't know what you're talking about and you're giving bad advice.

You're talking about SSL, not SSH.  

@heyandy889, your University should have a Security Office with engineers that could talk about this with your class, or make it part of your incoming student orientation.

---

### Post by wordymusic on 2010-10-28
> **remoryl said:**
> You don't know what you're talking about and you're giving bad advice.

You're talking about SSL, not SSH.  

@heyandy889, your University should have a Security Office with engineers that could talk about this with your class, or make it part of your incoming student orientation.

Sorry about that typo, dude. I don't know about the Security Office, though... link to example?

---

### Post by mcduck on 2010-10-28
> **Windows Nerd said:**
> It seems that someone has found a simple fix:
[http://techcrunch.com/2010/10/25/firesheep/](http://techcrunch.com/2010/10/25/firesheep/)

Just Use HTTPS everywhere, and/or noscript. The former encrypts your session, whilst the latter stops the Firesheep script from running on your computer.

I confirmed the latter workaround with my brother: I have noscript on and it prevents him from pulling my data over our wifi.

Actually using noscript has nothing to do with this. The script never runs on (or accesses in any way) the target user's computer. It just listen to the traffic between that computer and the access point.

Using HTTPS whenever possible is a valid point, though, and paying attention to what you do on public networks is definitely a good idea as well.

And no, Firesheep isn't the only way to do this, packet sniffers have existed for ages (and you'll even find some from the Ubuntu repositories). It's just the first one made to look so simple and easy that even non-tech persons will realize how vulnerable their data can be on a public network.

---

### Post by endotherm on 2010-10-28
> **Elycian said:**
> Alright, so lets stop saying "no a firewall won't help you" and come up with some productive ways the OP can actually protect themselves from this firefox extension.

... I got nothing...
there isn't one. thats the point. it's FBs fault, not the ops.
the only think you can do to defeat it, is the tunnel from the public network to a private one, and do your browsing through the tunnel. 
tor would work, or an ssh relay/vpn, or a proxy that uses ssl client side.

---

### Post by heyandy889 on 2010-10-28
Thank you for the responses!

My university has an "Office of Information Technology," who run the computer labs. They might be a good resource for educating about safe browsing on unsecured Wi-Fi.

I'm considering doing a demonstration of the Firesheep app in class. :twisted: It would wow and amaze the students, while demonstrating the risk of using facebook, amazon, twitter, on our wireless network. 

I haven't actually been able to "sniff the packets" from another computer, though; only my own.

---

### Post by Bone Down on 2010-11-01
Give this episode of security now a listen this covers Firesheep in a way that many will grasp.

> [Firesheep]("http://www.grc.com/securitynow.htm")

After catching up with a very busy week of security-related news and events, Steve and Leo celebrate the game-changing creation and release of "Firesheep", an add-on for the Firefox web browser which makes online web session hijacking as easy as it could possibly be. This WILL change the world for the better.
[32 MB]("http://media.grc.com/sn/sn-272.mp3")	[8.1 MB]("http://media.grc.com/sn/sn-272-lq.mp3")

---

### Post by waynefoutz on 2010-11-01
I was listening to a syndicated computer radio show over the weekend on this subject. The host of the show had an interesting idea that solves this problem. If the host of the network wants his or her network to remain open, simply enable WPA, and put the password in the name of the SSID. For instance "john's coffee pswd coffee" This gives users the freedom to log on, and have WPA enabled so they don't have to worry about Firesheep.

---

### Post by endotherm on 2010-11-02
> **waynefoutz said:**
> I was listening to a syndicated computer radio show over the weekend on this subject. The host of the show had an interesting idea that solves this problem. If the host of the network wants his or her network to remain open, simply enable WPA, and put the password in the name of the SSID. For instance "john's coffee pswd coffee" This gives users the freedom to log on, and have WPA enabled so they don't have to worry about Firesheep.
how would that solve the problem? if you have the password, you can sniff the local traffic, so whether it;s open or locked down, if the firesheep user is on the network, it should work fine.

---

### Post by waynefoutz on 2010-11-02
> **endotherm said:**
> how would that solve the problem? if you have the password, you can sniff the local traffic, so whether it;s open or locked down, if the firesheep user is on the network, it should work fine.

Firesheep doesn't work over a wpa encrypted network. Only an open one.

---

### Post by mcduck on 2010-11-05
> **waynefoutz said:**
> Firesheep doesn't work over a wpa encrypted network. Only an open one.
On the other hand that's just a minor slowdown, if the user is already able to access the network.

Combine two tools, like Firesheep and Aircrack, and the problem returns.

[http://wifinetnews.com/archives/2010/11/can_wpa_protect_against_firesheep_on_same_network.html]("http://wifinetnews.com/archives/2010/11/can_wpa_protect_against_firesheep_on_same_network.html")

---

### Post by qstraza on 2010-11-12
Wifi is like a HUB. HUB does not know on which port is your PC, so it sends package to all PC connected to the HUB.

But your NIC filters the packages and accepts only packets that are addressed for you. You can put your NIC in promiscuous mode. In this case your NIC won't filter any packages, but you will be able to see all the traffic.

The same scenario happens on WIFI. WIFI router does not know where your laptop is, since there are no ports, so they send it to all in range. But normally, if a package is addressed to you, only you will get it, cuz of NIC filtering. But if you put your card into promiscuous mode, you are able to get all the traffic which is being send around on that specific wifi network.


So what firesheep is doing is very easy. It puts a NIC into promiscuous mode and sniffs the traffic, when interesting cookie comes, it gives you the link to the cookies source with cookie saved.

Same thing can be achieved with any other packet sniffing software, for example wireshark. Just filter port 80, so you will get less traffic, wait for right packet, check the content, save the cookie in Firefox and visit the page. Voila.

Open Wifi are stupid. Well they are not stupid, people are, if they think they are safe.

Best defence? VPN is the only solution.

---

### Post by Weevil on 2010-12-07
> **heyandy889 said:**
> 
... I hope my students already know not to do online banking on a public Wi-Fi network, but should I also caution them against using facebook, Amazon, and twitter?

This advise is a hackers best friend :) Don't use facebook, Amazon and twitter and then everyone is safe! I suggest educating your students about how stuff like this works and they will figure out what's safe and what not.

---

