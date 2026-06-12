---
title: "Wireless problems - painless solution."
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by r1d1 on 2007-08-14
My Belkin USB (RT2500) dongle worked OK in Dapper, intermittently in Edgy ( it was the luck of the draw, on booting up ) and didn't work at all in Feisty. This forced a downgrade back to Edgy, as my PC is two floors above my internet access point.

I solved the problem by buying a Belking 54G Gaming Adaptor - this was set up with my ESSID and security settings to conect to my WIFI modem router.

 I set it up using a windoze PC, using the supplied CD - if you don't have a windoze PC, take it round to a friend who does have, to enter the settings - it doesn't install on the PC, you just need to enter the WiFi network connection settings, which are saved into the adaptor ROM. I didn't try, but it may be possible to do the initial set-up from your Linux box.

The adaptor is then connected to the ethernet port on the Linux box, the machine booted up, and goodbye wireless woes forever ):P
The PC just sees the Adaptor as an ethernet connection.


I only bought the Belkin Adaptor because my modem/router is Belkin - other manufacturers may well produce a similar piece of equipment.

I hope this is helpful - perhaps not ideal for mobile users, but perfect at home, for me.

---

### Post by duffrecords on 2007-08-14
Very clever.  I used to do the same thing with Escient and ReQuest music servers when installing them in rooms with no ethernet hookup.

---

### Post by UNHOLYwoo on 2007-08-14
can you post exactly what belkin usb adapter you have? modle number and revision and all that...?

---

### Post by r1d1 on 2007-08-14
The Model Number is F5D7330uk.

 It also has  a label with "ver 2104uk" on it. I bought it from eBuyer in the UK, cost £42.54 inc tax & shipping.

I've had it for two weeks now, connects every time from boot up, running Feisty Ubuntu/Kubuntu depending on my mood. It plugs into two spare USB ports for it's power supply (or use included mains transformer). 

The data connection to the PC is via the ethernet connection, no data is transferred via the USB  connections they are purely a power source.

Hope this helps - it has saved me a lot of grief :)


(The USB adaptor I was previously using was the F5D7050 with the RT2500 chip - OK in Dapper, sometimes in Edgy, never in Feisty.)

---

### Post by bmartin on 2007-08-14
Funny you mention that... I just made [a HOWTO]("http://ubuntuforums.org/showthread.php?t=525833") for another user for the RT2500 chipset. Could you try it out and let me know if it works? There's a poll on that page (warning: it's a public poll). Maybe you'll have two working WiFi devices :KS It won't take long, as I wrote a script that does all the work for you.

---

### Post by pKp on 2007-08-14
That's great. I'll try it out soon as I get hold of one of those boxes. The end of wireless config problems...a dream come true :D

---

### Post by r1d1 on 2007-08-15
Good luck - let us know how it goes.

---

### Post by SactoBob on 2007-08-16
What you are using is a wireless bridge, which is IMO the best Linux wireless solution if portability is not an issue.  See [http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871) for info on wireless bridges and why they work so well for Linux.

Bob

---

### Post by r1d1 on 2007-08-16
Thanks for that link, Bob.

Yes, that is exactly what the Belkin Game Adaptor is, without claiming the fact - it is just advertised on the packaging as a means to connect an X-Box or Playstation to an existing Wifi network.

I finally got fed up playing around with Ndiswrapper, etc. and decided to go down the bridge route, so I could upgrade to Feisty
My current PC is a twin HDD dual boot windoze / Kubuntu PC. All my work is currently done in windoze - the only thing so far I don't like about Linux is  the lack of a Quicken equivalent.:-({|=

I have only been using Linux since March, and my current PC is just being used as a test-bed for my next machine, which will be a 100% linux box. I built my current PC myself three years ago, and will also build my next machine myself. 

Main  things I have learnt so far - no ATI graphics card, next time it'll be Nvidia
                                                    - the WiFi bridge is here for keeps, I'll just use a switch to give me a local wired sub-LAN. The Belkin USB dongle will find a good home on another family windoze box !

Quite why the use of a WiFi bridge is not being better promoted as the way to go, I don't know. It certainly make the whole shebang hassle free.\\:D/

Perhaps people just enjoy the challenge of trying to get WiFi working under the latest releases - me personally, I'd rather be up and running with Kubuntu Feisty.

Once again, thanks for the link - I think it should be made a sticky, for noobs like myself to find.

---

### Post by moron on 2007-08-16
Easy answer to why bridges are not pushed as the way to go is that for the most part they are:

- often impossible to actually find for sale anywhere
- most are old and so do not support WPA (WEP is dead)
- expensive

Since all current gaming systems have wireless options expect this situation to get worse.

Cheers

---

### Post by r1d1 on 2007-08-16
I agree with your first point - the only way I found out the capability of the piece of kit was a customer review on the eBuyer website - the customer described how he set up 4 linux Pc's to connect to the adaptor/bridge via a switch (giving in effect a wired sub-LAN), then to the rest of the network via WiFi.

This thing supports both WEP and WPA.

Yeah, things could get expensive and complicated, if you end up with trying to set up bridged routers to communicate with each other - on it's own this kit is around twice the price of a dongle.

Cheers.

---

### Post by SactoBob on 2007-08-16
You're welcome for the link.  I agree on you conclusions about the video and the bridge.
I also don't understand why they are not more widely  used.  You can get the Buffalo for about $60 and the Zyxel for less than that.  If you know what you want, they are easy to get and will support WPA, also support downloadable firmware updates for the future, and the increased performance and multiple lines are well worth the price IMO.

If everybody used a bridge, there would hardly be a post about wireless problems.

If you need to run Quicken, since you have a Win license, you could run Win in a virtual machine with VMWare - easy to do with Easyvmx if you have the hardware.  You could even run Ubuntu as a VM in your Win box (sacrilege).

Bob

---

