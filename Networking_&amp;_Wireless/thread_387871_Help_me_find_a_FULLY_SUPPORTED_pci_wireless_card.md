---
title: "Help me find a FULLY SUPPORTED pci wireless card"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by tj.milligan on 2007-03-18
I need your help. [BEGIN RANT] I have a Linksucks rt2561/rt61-based pci wireless card that has been problematic in linux from the day I bought it. I realize that ratech and serialmonkey offer drivers, but I want a real wireless card w/ a chipset that is not a nightmare and JUST WORKS! BTW, even when I have gotten it to work (only in Edgy, never Feisty), it would break every time I updated the kernel :\ [END RANT] 

Sooooo, can anyone suggest a wireless desktop pci card that DOES work in Edgy AND Feisty out of the box? Does work = Native driver that I don't have to depmod, modprobe, blacklist, etc AND which allows WPA connection natively thru NetworkManger. For instance, I have the following in my notebook: Integrated Intel PRO/Wireless 2200BG (802.11b/g), using ipw2200 according to dmesg | less. I've never had trouble w/ this chip.

I know there's a sticky on "supported cards" but I'd like to hear from real ppl who are happy w/ their no-nonsense wireless pci cards. 

BIG THANKS in advance!!! Newegg links a plus :D

Cheers,
Terry

---

### Post by tj.milligan on 2007-03-18
Bump. 

I didn't specifically mention this, but I certainly want to avoid ndiswrapper solutions as well :)

---

### Post by SactoBob on 2007-03-18
Terry, I know just what you mean, and just what you want.
See this thread
[http://www.linuxquestions.org/questions/showthread.php?t=536898](http://www.linuxquestions.org/questions/showthread.php?t=536898)

for totally driverless, totally dependable wireless.  In fact, I'll post my rewrite of that post.  I have the Buffalo ethernet converter, which is a wireless bridge, works way better than any pci card because of its power.  It is $60 at Newegg
=================================================

Since manufacturers' support for Linux drivers is spotty, with some not cooperating at all, using wireless under Linux can be challenging.  Some wireless cards, such as Atheros with madwifi, work well with native drivers.  Others cards may work well with ndiswrapper while a number of cards are simply unsupported.

	A wireless bridge is a versatile and often overlooked solution to wireless headaches.  A bridge is a free standing unit with its own operating system and power supply.  You configure it with your browser.  It connects independently to your wireless LAN and supplies a wired connection to your &#8220;bridged&#8221; computer(s).  Some wireless routers can operate in bridge mode.  Bridges offer advantages and disadvantages over wireless cards.

**Advantages**

-  _Simplicity_: Since the wireless connection is handled entirely by the bridge, you don't need any wireless drivers. Connected computers see the bridge as a wired connection.

-  _Location_: The bridge can be located up to 100m away for convenience or reception.  It can be moved or transported and connected to another computer.

-  _Connectivity_: Bridges can provide multiple wired Ethernet ports for other computers.

-  _Performance_: High power units function well in challenging reception environments.

-  _Flexibility_: The wireless connection is independent of the OS to which it is connected, and is unaffected by changes or upgrades to the OS.  

**Disadvantages**

-  _Cost_: High performance dedicated bridges cost over $100.  However, less expensive routers, such as ZyXEL's P330W, Buffalo (some, e.g. Wireless Ethernet Converter), and Linksys (some with third-party firmware) can operate in Bridge Mode.

-  _Bulk_:  The unit requires its own power supply and has its own footprint, which can be as large as a typical router.

-  _Energy consumption_: Up to 400 mw for higher performance units.

	For a good review of Linux wireless options, See  [http://socallinuxexpo.com/scale5x/presentations/rex.odp](http://socallinuxexpo.com/scale5x/presentations/rex.odp)  (Open Office format).

	To view the specs, manual, etc. of a typical high performance bridge, see 
[http://www.netgate.com/product_info.php?cPath=32&products_id=361](http://www.netgate.com/product_info.php?cPath=32&products_id=361)

	To see a bridge configuration for the ZyXEL, see [http://gadgetaddict.wordpress.com/20...reless-bridge/](http://gadgetaddict.wordpress.com/20...reless-bridge/)

        A fine performing, $60 bridge (called a Wireless Ethernet Converter) [http://www.newegg.com/Product/Product.asp?Item=N82E16833162168](http://www.newegg.com/Product/Product.asp?Item=N82E16833162168)

---

### Post by tj.milligan on 2007-03-19
SactoBob, Thank you!

So this will work my Linksys WRT54G [sveasoft firmware] router, maintaining my QoS and such? And this will be compatible w/ my NFS and SAMBA shares? I see from your post (also took a look at the linuxquestions.org thread) you have included several good links; I'll have time to read these tomorrow during my lunch hour.

This looks very promising!!

---

### Post by SactoBob on 2007-03-19
Yes, I have two of them, the high performance Engenius from Netgate (great folks who first explained the advantages of the bridge) and the $60 Bufallo, which also works great and gives 4 wired outlets.  Look at some of the comments from Linux users at Newegg.

Yes, there should be no trouble linking to your wireless router - that is what they do.  Mine link to my Belkin Pre-N router.  The only difficullty would be in setup if you are a complete network novice.  E.g. the default address of the Buffalo is 1.1.1.1 so you have to temporarily set your computer to use another address on that same subnet (e.g. 1.1.1.2) in order to set up the router.  Once it is set up for your router, you can assign it a new ip address on your current subnet.  It takes all of 5 minutes max for everything.  It supports WEP and WPA.

Once it is setup for your router, you can plug it in and take it anywhere.  You will also probably notice a big performance increase if you get something high power like that Engenius or Buffalo.  The speeds that are advertised are theoretical max that drop off quickly with distance.  The high power units are faster in the real world, I think you will find.  At any rate, you will not worry about any drivers and your wireless headaches will be over.

---

### Post by tj.milligan on 2007-03-26
Problem solved. Just wanted to update this thread.

Per SactoBob's suggestion, I ordered the [BUFFALO WLI-TX4-G54HP Ethernet Port Wireless Converter]("http://www.newegg.com/Product/Product.asp?Item=N82E16833162168").

[With some help]("http://www.ubuntuforums.org/showthread.php?t=390711") I got it set up and I couldn't be happier. The wireless signal is converted to ethernet just like the name implies, and Ubuntu (as well as any other OS) treats the connection as a wired connection. Translation: NO HASSLES!

The Buffalo Converter is also super fast, and has 4 ports on the back. Well worth the $60. I don't have a busted wireless network driver every kernel update now!

---

### Post by SactoBob on 2007-03-27
I'm glad it worked out so well for you, but I was sure that it would.
I did some tests between that Buffalo bridge versus my wireless card in my laptop on my own home wireless network.

The bridge is very noticeably faster, even when the laptop is fairly close to the router.  When the range is increased, it becomes no contest, and that bridge will maintain a strong and fast connection  when my pcmcia card is weak and flaky.

It's too bad that more people don't consider this solution, since it gives better performance and more flexibility than a pci wireless card.  And as you say, you don't have to worry about drivers, multiple OS's, upgrades etc.  And since you get four outlets, the price is only $15 per connection if you look at it that way.

If portability is not an issue, the bridge just solves the wireless problem once and for all.

Bob

---

### Post by jazzman65 on 2007-05-05
Hi SactoBob,

I just you'd like to know that I followed your advice about using a Buffalo wireless bridge for my new desktop I just built and the bridge works like a charm!  My Buffalo router is upstairs in the 2nd floor and my new machine is in my basement and I've got tremendous wireless connectivity down here!  in fact, I didn't even have to get it working.  While Feisty was being installed in my new machine, I plugged in the bridge and it was off and running before the OS finished installing!  Anyway, I wanted to let you know how much I appreciated your suggestion and to let you know that someone benefited greatly from it!

Thanks,
jazzman65

---

### Post by SactoBob on 2007-08-13
Jazzman -
You're very welcome, and I am glad that you too have solved your Linux wireless headaches.  I haven't looked at this thread for awhile, but I see that a number of people have looked at it.  I'll give it another bump with this reply.

The bridge is just a great solution since it is high performance and independent of any operating system or upgrade.  For the best performance and the least hassle, it is hard to beat.
Bob

---

### Post by m9ke on 2007-08-17
Thanks for this!  I have only one PCI slot left in my box, and a brand new Linksys wireless router that I am pretty sure supports bridge mode.  Even better no driver hassles.  I am going to give this a try.

Thanks!
m9ke

---

### Post by Mike54 on 2007-10-01
SactoBob, I just wanted to thank you for this excellent product recommendation.

I printed out the instructions you had given tj.milligan in another thread and purchased a Buffalo converter.  I unplugged my dodgy LinkSys WUSB54GS adapter and plugged in the converter.  I walked across the room to get the instructions and before I got back, I saw a prompt telling me there were updates available for download.  I clicked on the prompt and started downloading.  What a painful installation that was, eh?

The only problem I have now is wondering what to do with these instructions I didn't need.  ;-)

---

### Post by joconnorwi on 2007-10-16
Wow! I just found this post! how great!

One question though, I just plug this baby into my desktop and It should find my home wireless network?

I have a Linksys WRT54G. 

I'm all excited now!

---

### Post by SactoBob on 2007-10-22
You still have to set things up for your network, I think, although Mike above didn't seem to need to.
I set mine up as per directions, but maybe you don't even need to do that??
I would think you would have to set up encryption etc.

The Buffalo comes with instructions, and here are some that I provided for Terry.
[http://ubuntuforums.org/showthread.php?t=390711](http://ubuntuforums.org/showthread.php?t=390711)

I don't know of an easier way to get wireless going (and keep it going) with Linux.
Bob

---

### Post by SactoBob on 2008-01-03
I needed to buy another wireless bridge, and when I looked for another Buffalo, I noticed that they were not available due to a lawsuit/injunction.

After some research, I purchased a Linksys Wireless G Game Adapter, which is just a wireless bridge.  It installed with virtually no effort and is working fine.  It cost about $60 but only has a single ethernet port.

For another way to use a wireless router as a bridge, see [http://ubuntuforums.org/showthread.php?t=572070](http://ubuntuforums.org/showthread.php?t=572070)

Lemonseed bought 2 routers, flashed them with 3rd party firmware, and set one of them up as a route for a great solution.

---

