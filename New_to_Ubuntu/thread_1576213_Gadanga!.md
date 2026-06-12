---
title: "Gadanga!"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Vard66 on 2010-09-16
Hello, Ubuntu Forums.

I've been on the forum for a couple of days now, browsing about, having a look and a (mostly confused) read of a lot of threads, but I figured it was about time to pop on and make the first post.

My name is Chris, I'm 21 and UK based, and for all intents and purposes, I'm utterly, entirely new to Linux. I had a play around with some Ubunut v5.10 discs I was given a long, long time ago, but I've forgotten anything I might've learned back then. :p

I'm setting out to explore the world of Ubuntu for a handful of reasons really. Firstly, something to do, as I'm unemployed. Secondly because most of my computers are falling to bits around me and (as previously mentioned) being unemployed means I'm a bit short of money for new bits, so I'm looking to make the best of what I've got. I find the concept of a non profit motivated OS delightfully refreshing, and I have a couple of friends who have been using it for a while, and recommend it.
I'm also not a mad fan of Vista or 7, and, while I do love XP, I've only got a finite number of days more that I'll be allowed to use it before being forced into submission, so I figure if I've learned enough about Ubuntu to be able to get what I need working, and I like it enough by then, it might prove to be a viable alternative to blind submission into an OS I never liked to begin with anyway.

So basically, I'm not relying on it for anything, I'm not hanging any great hopes on it, it's a bit of an experiment and a learning exercise, on a spare laptop for the moment.

Didn't realise until this point, however, quite how much learning there'd be.

I was just reading Psychocat's introduction articles, and noting that I have just jumped straight in at the deep end and then become befuddled.


Anyway. I'm waffling.

I've had 10.04 installed on an old Medion MIM2120 I had kicking around for a couple of days now, and have had some confusions, which I'm hoping someone here can help me with.

I've spent the last couple of days since registering browsing and searching to see if I could find any threads of similar ilk, but I've not found any that are close enough to answer my questions. Or perhaps it's that I'm not understanding enough of what I'm reading to recognise that it is close enough. I don't know.

Initially I had some difficulties with wired connection (I cannot find drivers compatible with my WLAN card, but I'll get to that in a moment), which a friend suggested could be DNS issues, muttered something about my Router handing out the DNS, and pointed me in the direction of the IPv4 and IPv6 settings for the wired connection Auto eth0.

I figured I could just p*ss about with it for a while and try some different combinations of ip's and gateways and netmasks until I found it working, going on the same settings I gave to my XBox to connect (yes, yes I am that much a noob to this, that I'm using guesswork as the first option just to see),

So, going on the figures of
*IP:192.168.1.36* (plucked randomly out of thin air)
*Netmask:255.255.255.0*
*Gateway:192.168.1.1*

I've been mucking about with it for a couple of days.

I got a fairly quick success with this, though it then took me a couple more attempts to remember what the hell I did that worked. So I'll try to recollect what happened.

initial settings:

*IPv4: Automatic (DHCP)*, DHCP client ID box blank.
*IVp6: Ignore*

What I found worked, was;

*IPv4: Automatic (DHCP) Addresses only*
*DNS servers: 192.168.1.1*
*IPv6: Automatic*

That got me connected, much to my surprise and joy. I felt all smart and brilliant, having figured it out (and I use the term losely, being that it was all trial and error).

So, great, browsed for a couple of hours, then switched the lappy off.

Switched it back on a couple of hours later again, and found that it wouldn't connect.
Checked all the Auto eth0 settings, particularly those I'd changed, and found that nothing had changed since I last looked.

In frustration, I tried reverting it to what it was to begin with;

*IPv4: Automatic (DHCP)*, DHCP client ID box blank.
*IVp6: Ignore*

And tried that. Perversely that now worked, and I was once more able to browse.

*Edit*

Forgot to mention a moment ago when I posted. The friend who pointed out that it's probably DNS issues when I initially quizzed him on connecting Ubuntu to a wired ethernet, also muttered something a minute ago about resolv.conf possibly being the route of my Ubuntu's craving for variety on the DNS settings. Googled it, and got a load of pretty gobbledegook technical answers that I couldn't make head nor tail of, but I just thought I'd mention that in case it helped anyone with... er... well, helping me.

Anyone who can shed some light on this, that'd be greatly appreciated; especially if it helps me fix it! :)


My other issue is that I can't seem to find a driver to let Ubuntu register my WLAN card.

I gather this is a fairly common issue, partly from threads I'm browsing on here, and partly from the way my friend chuckled when I mentioned it, and simply said 'yeah, good luck with that'.

I have googled various combinations of the Laptop's model number and 'Ubuntu' and 'WLAN' and 'Driver' and come up with jack all except XP compatible drivers.

I came across the lspci command in undecim's newb guide, and have come up with a result for the WLAN card's type, so I can tell you that, folks, but not much more.

The result was

*Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC*

Again, any help or explanations offered towards this would be greatly appreciated, and with much thanks.

Right.

Now that I've posted this, so that I won't be deemed another bot or spammer and removed, I'm going to go back to browsing and trying to decipher!

Please excuse me if I'm a little slow in responding; any time I have this forum open I also find I've a tendancy to have another ten tabs or more open with threads of possible interest, so I'm a little preoccupied, even if it is on the same subject topic.


Hello, thanks, and please excuse my colossal noobish tendencies. :oops:


Vard.

---

### Post by sandyd on 2010-09-16
> **Vard66 said:**
> Hello, Ubuntu Forums.

I've been on the forum for a couple of days now, browsing about, having a look and a (mostly confused) read of a lot of threads, but I figured it was about time to pop on and make the first post.

My name is Chris, I'm 21 and UK based, and for all intents and purposes, I'm utterly, entirely new to Linux. I had a play around with some Ubunut v5.10 discs I was given a long, long time ago, but I've forgotten anything I might've learned back then. :p

I'm setting out to explore the world of Ubuntu for a handful of reasons really. Firstly, something to do, as I'm unemployed. Secondly because most of my computers are falling to bits around me and (as previously mentioned) being unemployed means I'm a bit short of money for new bits, so I'm looking to make the best of what I've got. I find the concept of a non profit motivated OS delightfully refreshing, and I have a couple of friends who have been using it for a while, and recommend it.
I'm also not a mad fan of Vista or 7, and, while I do love XP, I've only got a finite number of days more that I'll be allowed to use it before being forced into submission, so I figure if I've learned enough about Ubuntu to be able to get what I need working, and I like it enough by then, it might prove to be a viable alternative to blind submission into an OS I never liked to begin with anyway.

So basically, I'm not relying on it for anything, I'm not hanging any great hopes on it, it's a bit of an experiment and a learning exercise, on a spare laptop for the moment.

Didn't realise until this point, however, quite how much learning there'd be.

I was just reading Psychocat's introduction articles, and noting that I have just jumped straight in at the deep end and then become befuddled.


Anyway. I'm waffling.

I've had 10.04 installed on an old Medion MIM2120 I had kicking around for a couple of days now, and have had some confusions, which I'm hoping someone here can help me with.

I've spent the last couple of days since registering browsing and searching to see if I could find any threads of similar ilk, but I've not found any that are close enough to answer my questions. Or perhaps it's that I'm not understanding enough of what I'm reading to recognise that it is close enough. I don't know.

Initially I had some difficulties with wired connection (I cannot find drivers compatible with my WLAN card, but I'll get to that in a moment), which a friend suggested could be DNS issues, muttered something about my Router handing out the DNS, and pointed me in the direction of the IPv4 and IPv6 settings for the wired connection Auto eth0.

I figured I could just p*ss about with it for a while and try some different combinations of ip's and gateways and netmasks until I found it working, going on the same settings I gave to my XBox to connect (yes, yes I am that much a noob to this, that I'm using guesswork as the first option just to see),

So, going on the figures of
*IP:192.168.1.36* (plucked randomly out of thin air)
*Netmask:255.255.255.0*
*Gateway:192.168.1.1*

I've been mucking about with it for a couple of days.

I got a fairly quick success with this, though it then took me a couple more attempts to remember what the hell I did that worked. So I'll try to recollect what happened.

initial settings:

*IPv4: Automatic (DHCP)*, DHCP client ID box blank.
*IVp6: Ignore*

What I found worked, was;

*IPv4: Automatic (DHCP) Addresses only*
*DNS servers: 192.168.1.1*
*IPv6: Automatic*

That got me connected, much to my surprise and joy. I felt all smart and brilliant, having figured it out (and I use the term losely, being that it was all trial and error).

So, great, browsed for a couple of hours, then switched the lappy off.

Switched it back on a couple of hours later again, and found that it wouldn't connect.
Checked all the Auto eth0 settings, particularly those I'd changed, and found that nothing had changed since I last looked.

In frustration, I tried reverting it to what it was to begin with;

*IPv4: Automatic (DHCP)*, DHCP client ID box blank.
*IVp6: Ignore*

And tried that. Perversely that now worked, and I was once more able to browse.

Anyone who can shed some light on this, that'd be greatly appreciated; especially if it helps me fix it! :)

[B]settings aren't permanant when you use the network manager GUI.
See -> [http://openubuntu.com/index.php/topic,230.0.html](http://openubuntu.com/index.php/topic,230.0.html)
[/B] 

My other issue is that I can't seem to find a driver to let Ubuntu register my WLAN card.

I gather this is a fairly common issue, partly from threads I'm browsing on here, and partly from the way my friend chuckled when I mentioned it, and simply said 'yeah, good luck with that'.

I have googled various combinations of the Laptop's model number and 'Ubuntu' and 'WLAN' and 'Driver' and come up with jack all except XP compatible drivers.

I came across the lspci command in undecim's newb guide, and have come up with a result for the WLAN card's type, so I can tell you that, folks, but not much more.

The result was

*Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC*
**Nope. doesn't work with ubuntu.**
Again, any help or explanations offered towards this would be greatly appreciated, and with much thanks.

Right.

Now that I've posted this, so that I won't be deemed another bot or spammer and removed, I'm going to go back to browsing and trying to decipher!

Please excuse me if I'm a little slow in responding; any time I have this forum open I also find I've a tendancy to have another ten tabs or more open with threads of possible interest, so I'm a little preoccupied, even if it is on the same subject topic.
**its ok ;)**

Hello, thanks, and please excuse my colossal noobish tendencies. :oops:
**well, were all like that in the begining right? :)**

Vard.
.

---

### Post by McTwitch on 2010-09-16
random guess work? That's all I do. If I screw something up too badly, I post something, and then get people who DON'T guess to help. Guessing is all part of the fun. Other than that, can't help though, sorry.

---

### Post by Vard66 on 2010-09-16
@ Sandy, I really, really hoped so when I was making that first post, otherwise I was going to be sitting here feeling even more uneducated than I was before.

:p

Thanks for the link, having a shufty now.

Also, I figured that would probably be the answer re: the WLAN card.

I'm sure I'll be able to dig up something else that IS compatible with it.

I'll do a bit of a search on here, it's bound to have been covered if WLAN compatibility is a fairly common issue.

---

### Post by migs73 on 2010-09-17
I can't find any drivers for your WLAN either. It might be worth investing in a USB one instead. I am sure you can get them for about a tenner nowadays. Check it is Linux compatable here first!!!
[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)

---

### Post by candtalan on 2010-09-17
Welcome! I am in Bracknell UK.


> **Vard66 said:**
> Hello, Ubuntu Forums.
Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC


In the pdf document:
[http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fwww.winbond-usa.com%2Fproducts%2Fwinbond_products%2Fpdfs%2FWLAN%2FW89C33DProdBrief_20050622.pdf&rct=j&q=driver%20Winbond%20Electronics%20Corp%20W89C33D%20802.11%20a%2Fb%2Fg%20BB%2FMAC&ei=4o-TTKHICpPP4AbNiu2ABA&usg=AFQjCNEw20Jx1EBoBCG_mBkHm882t2e08w&cad=rja](http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fwww.winbond-usa.com%2Fproducts%2Fwinbond_products%2Fpdfs%2FWLAN%2FW89C33DProdBrief_20050622.pdf&rct=j&q=driver%20Winbond%20Electronics%20Corp%20W89C33D%20802.11%20a%2Fb%2Fg%20BB%2FMAC&ei=4o-TTKHICpPP4AbNiu2ABA&usg=AFQjCNEw20Jx1EBoBCG_mBkHm882t2e08w&cad=rja)
there is a suggestion that the chip has drivers for 
Windows 2000, XP, XP 64-bit
Windows CE 5.0
Linux 2.4.x

although I have no idea where they could be found. However, I wondered if you had yet considered to use the wrapper method of using Windows drivers for the wireless?

ndiswrapper  can generally make use of Windows drivers, although of course you need to obtain a copy of the Windows driver item.

mmm.
for Win 7
try here
[http://listing.driveragent.com/win7/pci/1050/0033/00000000](http://listing.driveragent.com/win7/pci/1050/0033/00000000)

or xp  here
[http://listing.driveragent.com/b/pci_print/1050/0033/00000000](http://listing.driveragent.com/b/pci_print/1050/0033/00000000)

Good luck
hth

---

### Post by sandyd on 2010-09-17
> **candtalan said:**
> Welcome! I am in Bracknell UK.




In the pdf document:
[http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fwww.winbond-usa.com%2Fproducts%2Fwinbond_products%2Fpdfs%2FWLAN%2FW89C33DProdBrief_20050622.pdf&rct=j&q=driver%20Winbond%20Electronics%20Corp%20W89C33D%20802.11%20a%2Fb%2Fg%20BB%2FMAC&ei=4o-TTKHICpPP4AbNiu2ABA&usg=AFQjCNEw20Jx1EBoBCG_mBkHm882t2e08w&cad=rja](http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fwww.winbond-usa.com%2Fproducts%2Fwinbond_products%2Fpdfs%2FWLAN%2FW89C33DProdBrief_20050622.pdf&rct=j&q=driver%20Winbond%20Electronics%20Corp%20W89C33D%20802.11%20a%2Fb%2Fg%20BB%2FMAC&ei=4o-TTKHICpPP4AbNiu2ABA&usg=AFQjCNEw20Jx1EBoBCG_mBkHm882t2e08w&cad=rja)
there is a suggestion that the chip has drivers for 
Windows 2000, XP, XP 64-bit
Windows CE 5.0
Linux 2.4.x

although I have no idea where they could be found. However, I wondered if you had yet considered to use the wrapper method of using Windows drivers for the wireless?

ndiswrapper  can generally make use of Windows drivers, although of course you need to obtain a copy of the Windows driver item.

mmm.
for Win 7
try here
[http://listing.driveragent.com/win7/pci/1050/0033/00000000](http://listing.driveragent.com/win7/pci/1050/0033/00000000)

or xp  here
[http://listing.driveragent.com/b/pci_print/1050/0033/00000000](http://listing.driveragent.com/b/pci_print/1050/0033/00000000)

Good luck
hth

only winxp drivers work with ndiswrapper

---

### Post by anewguy on 2010-09-17
+1 on ndiswrapper (and yes as mentioned above, XP drivers only).

What I would do:

[LIST]
[*]locate the Windows XP drivers for the adapter.  In particular, you need the .inf and .sys files.  Copy them to your desktop.
[*]With Ubuntu already booted, connect to the internet (if you need to manually do so)
[*]Start Synaptic Package Manager (System/Administration/Synaptic Package Manager)
[*]Search for ndis - it will automatically isolate entries as you type.  You should see ndisgtk, ndiswrapper common and ndiswrapper utilities - be sure to click each one and mark for installation.
[*]Click apply and wait for it all to finish.  
[*]Close out of Synaptic Package Manager
[*]ndisgtk that I had you install is a graphical front-end to ndiswrapper, it makes things much easier.  Start it via:[LIST]
[*]System/Administration/Windows Wireless Drivers
[/LIST]
[*]Click add (or new - don't remember which it has).
[*]Point it to the .inf file on your desktop and ok it
[*]Close ndisgtk
[*]Right-click on the network manager icon.  Be sure "Enable Wireless" is checked.
[*]Close network manager
[*]left-click on the network manager icon - you should see wireless now if the driver installed correctly
[/LIST]

Remember that if MAC filtering is being used on the router you will need to add the MAC to the allowed list on the router.

If you are using encryption, be sure to select the correct type and provide the correct password/passphrase when connecting via network manager.

If your router is set to not broadcast the network Id (Essid or SSID), you will have to manually set up the connection via network manager.

Let us know if you need ANY help with this or have ANY questions we really are here to try to help you and make ubuntu what you need it to be.

Dave ;)

---

