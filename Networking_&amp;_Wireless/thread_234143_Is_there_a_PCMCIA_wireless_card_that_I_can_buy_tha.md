---
title: "Is there a PCMCIA wireless card that I can buy that will &quot;just work&quot;??"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by Carbonfish on 2006-08-11
Hi everybody,

I am *really* trying to remain optimistic about getting wireless networking to work on my IBM ThinkPad T23 running Dapper, but I have tried to configure the no-name card that shipped with the laptop when I bought it used, and now I spent several hours trying to get a Netgear card to work to no avail. I downloaded ndiswrapper through Synaptic but haven't run it yet as I am not presently where there is an open network. The frustrating thing is, that with both the Taiwanese no-name card and the Netgear card, my machine "sees" the cards enough to show them in the network panel, and if I try to activate the wireless card (it shows up as eth1) it says that it is active and even gives me signal strength etc., but won't connect to the internet.

Rather frustrating.

So here is how tired I am of dealing with this... Can anyone out there suggest a wireless card (PCMCIA type) that I can go out and purchase tomorrow at my local Fry's Electronics or wherever, that will plug in to my ThinkPad and be immediately supported by Ubuntu? I don't care at this point how much the thing costs, I just need to be able to connect to any open network, any time I want to, without having to re-configure everytime I restart my computer (it is a laptop after all). I have high-speed connections at work (both wireless and ethernet), but don't want to spend the rest of my life at the place I work on my own time so that I can use my laptop just because I can plug it in to the ethernet connection there.

I have read the wiki's, I have been living on these forums trying to get this thing working, and so far I have had a few successes. For instance, I can now play DVD's, and I am able to stream most of the web content that I can on my Mac. Java still needs work, but I'm working on it...

But I *really* need this wireless connectivity!!

Any suggestions? I will go out tomorrow and buy whatever card will "just work"

Thanks for letting me rant a little, and most of all

Thanks for your help.

Kent

---

### Post by Titus A Duxass on 2006-08-11
I have a linksys wpc11 ver4 (I think, I cannot check because it is at home, I am not)it uses the RTL8180 and WOTB.

---

### Post by Carbonfish on 2006-08-11
Thanks for your reply. Do you have to do any sort of "configuration dance" or anything when you are switching from a wireless network to a hard-wired ethernet connection or anything? I can't help but think that I must be making this harder than it is. I am used to a system that prioritizes the net connections aotumatically, but I don't mind having to go in and change which one I am using manually, but I would think that the process should be pretty straightforward. I just can't seem to make all of the pieces come together.

Thanks again for your help,

Kent

---

### Post by Titus A Duxass on 2006-08-11
Switching from wireless to hardwire or vice versa can be a pain, I tend to use my laptop only with wireless for that reason.

There is probably a thread about it on the forum.

For NetGear I found the best solution was to return them in exchange for Linksys products.

---

### Post by Carbonfish on 2006-08-11
Yeah, thanks for feeling my pain. I wouldn't mind just using the wireless connection exclusively *if i could just get the damned thing to work*! Ha, ha.

The Netgear card would have been a gift if I had been able to get it to work, so i can't really go and trade it in an a Linksys card. But the up-side of that is I'm not out anything for the Netgear card. I'll just give it back and but the Linksys tomorrow.

So you recommend the wpc 11? Or is there anything else I should know? I am usually a Mac guy, and this is my first run-in with the PCMCIA world, so I'll take all the recommendations that I can get.  ;) 

Thanks again,

Kent

---

### Post by Titus A Duxass on 2006-08-11
If you can get a WPC11 ver 4 got for it, mine worked with my T20 thinkpad and works with my JVC XP3210de mini note.

In breezy you needed to run the card with NDISWRAPPER but it was perfectly stable.

In Dapper it runs without NDISWRAPPER, just configure it through System => Administration (I always run with a fixed IP).

Then edit you /etc/networking/intefaces files so that all entries for eth0 are replaced with wlan0 and add the line auto wlan0.

If you still have problems try disabling the on-board ethernet card through BIOS.

---

### Post by Carbonfish on 2006-08-11
Thanks for your help Titus (great handle, by the way).

Man, am I really going to have to *disable* my internal ethernet card? Possibly in the BIOS? That might be a "deal-breaker". If I can't easily switch from one network connection to another what's the point of supporting more than one type of connection? If the ethernet has to be disabled for the wireless to work I may have to seek out a distro that has more flexibility/compatibility, which is a shame as I really like Ubuntu so far. I mean, you would think that the developers would look around and see what works. For instance, on my Mac if I have  an ethernet cable plugged in, it works. If my wireless card is turned on and the ethernet cable is plugged in the machine doesn't care, it defaults to the ethernet connection (unless I intentionally go in and change the order). If I unplug the ethernet connection, it defaults to the Airport card, and if I shut that off I can always plug in a phone jack and use the internal modem. What's so earth-shattering about having a networking hierarchy whereby the OS and the hardware agree on what order to attempt a network connection?

I realize that Ubuntu must try to work with virtually every kind of hardware out there, but that shouldn't affect the development of a hierarchical hardware profile that would be the default for all platforms *until* they need tweaking.

I guess I just don't get it. 

I really don't want to have to go in to the terminal every time I take my laptop with me somewhere and want to connect to an open net, and I really don't want to have to "cripple" part of my machine's networking capability so that I can use another part of it (i.e. disabling the internal ethernet card to use the wireless).
I am not afraid to have to do some set-up and configuration to make Ubuntu play nice with my hardware, but I don't expect to have to do it routinely every time I start the damn thing up. Again, it is a laptop after all, and I don't expect to leave the thing on forever so that my settings don't disappear. *shrugs, sighs heavily* 

Is Ubuntu really that networking un-friendly and counter-intuitive, that it is not capable of finding and connecting to an open network without having to jump through progressively smaller hoops?

Or am I just missing something simple here??

I would *really* appreciate some feedback here as I enjoy being part of this community and would hate to dump Ubuntu just because I'm missing something that should be obvious. But that said, no matter how ethically justifiable it is to use OSS versus proprietary software, I still have work to get done and have to be able to take advantage of *all* of the capabilities of my hardware.

Advice?

TIA, and thanks again,

Kent

---

### Post by Carbonfish on 2006-08-11
Well, I've gone out and purchased a Linksys WPC54G Notebook Adapter, and I've searched the forums and found a couple of "how-to's" on how to get the thing configured. As soon as I can get to a place where I can use my ethernet connection (the only one that works as present) I'll go to the repositories and download everything that I need (supposedly) to make this work, and then see if it does. 

I guess that if this doesn't solve my wireless (and other) networking problems I'll have to move to another distro. 

Thanks for your time and suggestions Titus.

Kent

---

### Post by fkamp on 2006-08-11
First, a couple of disclaimers:

I am using a desktop
I am using a pci card.

Other than that, I think its safe to recommend a card with an Atheros chipset. I just installed Dapper on an older PII 450 and used a Belkin F5D7000 version 5000 pci wireless adapter. I was amazed to find it just worked out of the box with NO issues whatsoever! Nothing to configure or tweak! Both static and DHCP worked. I have not tried any encryption yet though. 

Hopefully you can find a pcmcia atheros based card as well.

HTH

---

### Post by Carbonfish on 2006-08-11
Thanks for the input fkamp, but I bought a different card already (see the post just above yours)

KC

---

### Post by sidlinux on 2006-08-12
If any of you are still in the market for a Ubuntu-compliant (dapper drake) pcmcia wireless card, I recommend you get the Dell TrueMobile 1150 or the D-Link DWL-650.  If you don't mind using the USB adapter by Linksys, it would be the WUSB11 ver 2.6.  They all work right out of the box.  You can also look at the compatibility list at the Ubuntu and see if you can find a card that meets your needs.  You can get the Linksys 802.11g 54Mbps cards (but make sure you check the compatibility list before you buy it).  They should work with ndiswrapper, but I recommend you go to [www.linuxant.com](www.linuxant.com) and try out the drivers for 30 days.  At least they are guaranteed to work and are more stable.  The only catch is you pay $19.99 for it and it could be a good return on your investment..  Don't get anything that has any enhancements such as speeding it up to 108Mbps or the MIMO ones since they don't work with anything at this time.

Please make sure you check the hardware compatibility list before you make a decision what to do.

Cheers,:-D 

Sidney

---

### Post by weekend warrior on 2006-08-12
Carbonfish, I also posted this in the T23 thread for you. Yes there **are** wireless cards that will "just work" straight out of the box. Any of the cards on this [list from the Free Software Foundation]("https://www.fsf.org/resources/hw/net/wireless/cards.html") will be fine. The key is getting a card with a supported chipset so be careful with version numbers since some card makers switch chips even in the same series of a particular model.

I have a [Belkin F5D7010]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=136500") that works splendidly, just plug it in and boot up - very simple, very easy.

HTH


Edit: another thing I should add as an FYI Carbonfish - this is not an issue specific to Ubuntu per se, Linux in general and therefore all distros suffer due to the number of card/chip makers that don't bother to provide open source drivers for their products.

---

### Post by Carbonfish on 2006-08-12
Weekend Warrior,

Thanks so much! I responded to your post in the other thread and I'm on my way to go and get the Belkin right this minute.

I'll keep you posted (pun intended)  :grin: 

Thanks again,

Kent

---

### Post by schneo on 2006-08-12
> Is there a PCMCIA wireless card that I can buy that will "just work"??

I think it's very important to find a card which support also WPA.

If you take just WEP as the only protection proposed by Dapper it's like you have no protection at all. Google a little and you'll see how quick and easy it is to crack WEP without any knowledge.

Unfortunately WPA is not a priority for Canonical and you'll have to find the good card and tinker what's needed in a shell (I alreday lost few days with two cards but I've ordered a third one now ...).

Canonical says :
Ubuntu, Linux for Human beings

Without an "easy" WPA integration it's more like:
Ubuntu, "unprotected sex" for everyone
or 
Ubuntu, Unprotected Linux for everyone
(could give great pleasure but the consequences could be very sad)

](*,)

---

### Post by Xyus on 2006-08-12
Hi,

I can hardly (don't believe) that you just install ubuntu and from the first boot the card is fully detected? 

I've got a WiFi asus card and guess what, it ain't supported.. 

But I'm going to set up a test pc and buy a supported wifi card :) 

xyus

---

### Post by weekend warrior on 2006-08-12
For any of the Ralink 2500 based cards on the FSF list, encryption info including WPA setup can be found in [>> WiFiDocs]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500").

---

### Post by Carbonfish on 2006-08-12
Okay W W, I just got home from my local electronics mega-store with the Belkin F5D7010 and since I have no access to a wireless network that I know anything about (like the one at work), I am going to have to do "the grand experiment" at the local coffee shop that has an 'open network'. This should be a good real-world test, since that's really what I'm looking for, to be able to connect to open networks without any drama. 

Wish me luck!

Kent

---

### Post by weekend warrior on 2006-08-12
fingers are crossed... Hail Mary's are said... :wink:

---

### Post by Carbonfish on 2006-08-12
Hi everybody, and a happy Yahoo! to Weekend Warrior,

The card works, sort of... Ha, ha :roll: 

I am not sure what's going on with this network, but I have great signal strength and I went into the terminal and did an apt-get update and that went fine, I also downloaded and installed Opera just for fun, but when I try to open web pages in Firefox, the page starts to load and I even got as far as getting the boingboing logo and hopping girl, and then it just sits there. The odd thing about this is that it does exactly the same thing here if I am connected to their hard-wired ethernet connection (that they thoughtfully provide under the tables). 

I am typing this on my iBook from the same coffee shop using the same network, so I don't have a clue what's happening.

But it's a start! I can transmit and receive data so the card works on that level.

THIS JUST IN!!! Opera just loaded the page. It's a Firefox thing. Well, this I can *deal with*!

I will bring the forum up on the T23 and make a post from there (MAN! This is exciting!!).

KC

---

### Post by Carbonfish on 2006-08-12
Hey everybody look at ME! I'm typin' *WIRELESSLY!!*,and without any setup at all!!

Yep, that's right, Weekend Warrior is a pure genius and just saved me untold amounts of time and heartache. I am so happy I could split a seam!

For those of you just tuning in, I have had a terrible time trying to get wireless networking to work for me on my ThinkPad T23, but with the help of Weekend Warrior, who's name shall be made immortal in story and song, I am now typing this on the same machine that only hours ago was very close to dis-assembly.

I have made this offer to another helpful soul, and will make it again: W W, I owe you the biggest steak in Portland (which I happen to know is a whopper). Unless, of course your a vegetarian, in which case you can pick the restaurant. =D> =D> =D> :D 

Thanks again!

Kent Cline

---

### Post by weekend warrior on 2006-08-12
Hey hey! :D  I do know *that* feeling and it sure is excitingly good. Happy to see it "just work" for you - enjoy.

Next time I'm in the Rose City I'll take you up on that offer. :wink:

---

### Post by Carbonfish on 2006-08-12
You've got it. Send me a PM and I'll send you my E-mail address so that if you're ever coming this way you can let me know. I will definately make good on the offer!

Thanks again,

Kent

---

### Post by weekend warrior on 2006-08-13
Hehe, as I'm half way round the world from you, it may be some time before you'll have need to see that offer through.(hence the winky above) Thank you nonetheless. It's the thought that counts. :) 


If anyone else is looking for Ralink RT2500 based wireless cards - there's another, more complete list from the good folk at Ralink [here]("http://ralink.rapla.net/").

---

