---
title: "USB Connection works but Ethernet Connection doesn't"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by steven8 on 2007-04-04
Okay, I have a Toshiba cable modem which works via a usb connection in Dapper, but not in Edgy or Feisty.    Everyone says, "Ditch the USB, go Ethernet.".  I have submitted a bug report about the USB issue, but nothing has been happening.  

I couldn't use ethernet on my old computer, because I did not have a free PCI slot.  I now have a new computer, though, with a free PCI slot, so I decided to go and buy an ethernet cable, to go with an ethernet card I have, hoping to hedge my bets on the Upcoming Feisty  release.

However. . .I can't get the ethernet connection to work.  I have the connections enabled on Eth1 and eth2 for onboard.  I set it as the default gateway, and under network tools, it shows as receiving and transmitting.  Yet, it can't find a website.  Firefox can't use it, and Lookup or Ping under the network tools can't find anything.

I have been told ethernet is WAY better for connecting to the internet than USB, so I would like to give it a try.  Not to mention wanting to upgrade to Feisty when it comes out.

Actually I have both an onboard VIA Rhine II ethernet port and a D-Link cards which is supported right out of the box, per the documents.  Neither works for me.

OnBoard LAN is enabled in the BIOS and PCI is enabled as well.

Any thoughts would be greatly appreciated.  Thanks.

---

### Post by steven8 on 2007-04-06
I have been chastised for bumping a thread too often, so I waited until this had dipped down to page six.

I have gone over the how to's of setting up Ethernet, and by all means, it seems as though it should be working, yet no go.  See my above post and let me know if any of you good folks can think of anything I am not seeing.

Thanks.

---

### Post by DapperMe17 on 2007-04-06
Ubuntu should auto-recognize your ethernet in "Network Settings".

You'll want to only enable one of the "eth" (eth0 or eth1) connections & set to obtain DHCP automatically(if that's your choice). You should disable the other connections.


Should be as easy as that.

---

### Post by steven8 on 2007-04-06
> **DapperMe17 said:**
> Ubuntu should auto-recognize your ethernet in "Network Settings".

You'll want to only enable one of the "eth" (eth0 or eth1) connections & set to obtain DHCP automatically(if that's your choice). You should disable the other connections.


Should be as easy as that.


That is what I would think, too.  I thought that is just what I had done.  I will revisit this in the morning and see what happens.  I'll report back.

Thanks.

---

### Post by steven8 on 2007-04-06
No go.  Dapper does recognize both potential ethernet connections.  Onboard and PCI card.  I plugged into the PCI Card (D-LInk, as said before), which in Device manager is called eth1.  I disabled eth2 (the onboard), and set eth1 to DHCP.  Still cannot ping or find any domains, via network tools or firefox.  The USB connection works just fine, as you see, because I am surfing via it.

I'm not sure what else to do.

---

### Post by spd106 on 2007-04-06
So are you receiving an IP address from the modem/router? Can you navigate to the router's web page? The instruction manual should be able to tell you the address.

---

### Post by steven8 on 2007-04-06
I can't get to it via ethernet, but I went to the d-link webpage for it.  I have searched all the docs I could find, but no ip address is given.  It is a DFE-530TX+ 10/100 Ethernet Adapter, RTL8139 Ethernet, which, according to the d-link site is all correct.  What I am now guessing, is that it doesn't want to work with my toshiba cable modem.

---

### Post by steven8 on 2007-04-06
Question.  Since I now have an ethernet card hooked to an external cable modem, should Ubuntu see both devices in the Device manager, or just the ethernet card?

---

### Post by spd106 on 2007-04-07
Just the ethernet card.

When it's plugged in the USB, is there an option to switch to ethernet mode or any diagnostic utilities to run? I don't think my BT voyager automatically switched, though that was several years ago now.

---

### Post by steven8 on 2007-04-07
> **spd106 said:**
> Just the ethernet card.

When it's plugged in the USB, is there an option to switch to ethernet mode or any diagnostic utilities to run? I don't think my BT voyager automatically switched, though that was several years ago now.

When it is hooked into the USB, it comes up as eth0, under Networking.  In Network Tools, it pings and lookup and everything just fine.  I do not know of any other tools or an option to switch to ethernet.  Not sure where I'd find such a thing if there were.  

Funny thing is, when the USB is out, and the ethernet cable is in, it doesn't automatically come up as eth0, it stays as eth1.  Even though eth0 disappears when the usb is out.  Doesn't that seem odd?

---

### Post by steven8 on 2007-04-08
Well, I've reached a bit of a dead end.  I get the nice green light on the D-Link card to show it has an ethernet stream, but I can't get it to work.  I also get nice pretty lights on my onboard ethernet connection, but can't get it to work.  I also tried it in DreamLinux to see if it would work, and no soap.  Everything is enabled in my bios and in my OS, but I can't see the internet at all.  Quite a bummer, as I have no chance of ever upgrading beyond Dapper without an internet connection.  :(

---

### Post by spd106 on 2007-04-09
Have you tried setting a static address (say 192.168.1.5) then pointing firefox at 192.168.1.1, this is the most common default. Though some use 10.0.0.1 or 192.168.2.1.

It's a bit last grasp, but you might consider resetting to the factory defaults. Usually achieved via holding a reset button for 10 seconds.

These devices are usually configured to setup as a DHCP server by default. That should be enough to get you an address, then you just need to point a web browser at the default gateway.

---

### Post by steven8 on 2007-04-09
> **spd106 said:**
> Have you tried setting a static address (say 192.168.1.5) then pointing firefox at 192.168.1.1, this is the most common default. Though some use 10.0.0.1 or 192.168.2.1.

It's a bit last grasp, but you might consider resetting to the factory defaults. Usually achieved via holding a reset button for 10 seconds.

These devices are usually configured to setup as a DHCP server by default. That should be enough to get you an address, then you just need to point a web browser at the default gateway.

My machine is still on factory defaults, except I disabled the AC97 audio so I could use my sound card.  

I set it up as DHCP and when only one ethernet connection is enabled, it becomes the default gateway.  I have looked at about:config until my eyes are crossed trying to see if I'm missing anything, but I don't think so.  I tried disabling IPV6, but my networking thing says it uses the IPV6, so I re-enabled that.  Firefox is set for automatic internet connection, or whatever it's called.

I could try the static address.  I haven't tried that yet, because I had no idea what address to put in there.

A wild stab in the dark.  I bought an CATe patch cable.  Is that the correct thing to use?

---

### Post by spd106 on 2007-04-10
When I said reset I meant the router, sorry for the confusion.

A standard Cat 5e cable should work fine, I don't think you will need a crossover cable. Chances are it will work with either, though I'm sure the router's manual will tell you which to use.

---

### Post by steven8 on 2007-04-10
> **spd106 said:**
> When I said reset I meant the router, sorry for the confusion.

A standard Cat 5e cable should work fine, I don't think you will need a crossover cable. Chances are it will work with either, though I'm sure the router's manual will tell you which to use.

Ah, perhaps this is where we are crossing wires.  It is not a router but actually a modem.  It has no buttons of any kind on it.  Just lights to show power, data, etc.  According to all the info I can find on the Toshiba website, it should work the way I am doing things, but isn't.  I'll try the static IP numbers you suggested though.  It can't hurt!

I really appreciate all of your time and effort.  Thank you!

---

### Post by spd106 on 2007-04-10
Having read this [page]("http://www.toshiba.com/taisnpd/support/FAQ.html") I understand a bit more now. I looks like you will probably need a crossover cable or a hub.

This section also seems appropriate [http://www.toshiba.com/taisnpd/support/FAQ.html#twocomputers](http://www.toshiba.com/taisnpd/support/FAQ.html#twocomputers)

---

### Post by steven8 on 2007-04-10
> **spd106 said:**
> Having read this [page]("http://www.toshiba.com/taisnpd/support/FAQ.html") I understand a bit more now. I looks like you will probably need a crossover cable or a hub.

This section also seems appropriate [http://www.toshiba.com/taisnpd/support/FAQ.html#twocomputers](http://www.toshiba.com/taisnpd/support/FAQ.html#twocomputers)

I could exchange the cable I have for a crossover cable.  What is the difference between a patch cable and a crossover cable?  They look the same at the compusa site.

---

### Post by spd106 on 2007-04-10
It's called a crossover because some of the wires are crossed to allow the out pins from one nic to go the in pins of the other nic. You can probably find a better explanation via google.

You can make it yourself, but you would need a spare connector and wire crimper, it's rather tricky, unless you're used to threading eight needles in one go.

---

### Post by steven8 on 2007-04-10
> **spd106 said:**
> It's called a crossover because some of the wires are crossed to allow the out pins from one nic to go the in pins of the other nic. You can probably find a better explanation via google.

You can make it yourself, but you would need a spare connector and wire crimper, it's rather tricky, unless you're used to threading eight needles in one go.

These old eyes can hardly see to thread a needle anymore.  I think I'll just go pick up a cable and give it a go.  :)

---

### Post by steven8 on 2007-04-10
Nope.  Not a crossover cable.  Didn't even get data activity with it.  I had activity with the patch cable.  Oh well.  I can't afford to go get a hub right now, and I am stuck as to whether or not I'd need a hub or a router.  How would one know?  

Actually, if you think about it, I would need a hub or router and another cable.  Can't swing that right now, unless someone has a hub or router they'd like to trade for a nvidia mx 440 and an ati 9200 radeon card.  I'd trade both.  :)

---

### Post by steven8 on 2007-04-10
Okay, I went to the Toshiba site and it says I need to use a hub.  Anyone have a hub they'd like to trade for the two aforementioned video cards?  I'll pay to send the cards to you if you pay to send the hub to me.  Even up trade!

---

### Post by steven8 on 2007-04-10
> **steven8 said:**
> Okay, I went to the Toshiba site and it says I need to use a hub.  Anyone have a hub they'd like to trade for the two aforementioned video cards?  I'll pay to send the cards to you if you pay to send the hub to me.  Even up trade!

Maybe I shouldn't need a hub at all?  Read this fro mthe Toshiba FAQ's:

> **How to connect a cable modem to the PC?**

**[COLOR="Red"]Connect the 10BaseT Ethernet cable from your computer's network card to the 10BaseT connector on the cable modem's rear panel.[/COLOR]** [COLOR="Blue"]To connect more than one computer, place a hub in between the cable modem and the computers.[/COLOR] If your hub has an uplink port, connect the cable modem's uplink port (Ethernet port) to the hub using a straight 10BaseT Ethernet cable. If your hub does not have an uplink port, use an Ethernet crossover cable to connect the cable modem to one of the hub's ports. If you have an Ethernet hub, please refer to the instructions supplied with that product for more information. For the PCX1100U, a USB connection can be utilized. Simply connect the USB cable to you modem, and then to your PC, and run the driver CD included with your modem. For specific instructions, check out our Download Page.

It says you need a hub ONLY if you are doing more than one computer.  According to this, it should just hook up like my USB cable does.  Right to the ethernet card.  :(  Why the heck doesn't this thing work for me?

---

### Post by steven8 on 2007-04-15
I got it to work!!  I got another patch cable, unplugged the modem for a couple of seconds, plugged it back in. . .and it worked!!  Same principle as the router suggestion.  Thanks SPD106!

---

