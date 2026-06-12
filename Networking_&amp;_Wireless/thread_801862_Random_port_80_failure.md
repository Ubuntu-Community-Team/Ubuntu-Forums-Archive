---
title: "Random port 80 failure"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by ncosens on 2008-05-21
On average of once every 2 to 6 days now my router has a failure to relay data on port 80.  The other ports seem to work, but I haven't fully tested that.  All I know is that some MMOs and the IM services I use still work.  Anyway I can treat the problem by rebooting the router which is rather inconvenient.  Does anyone know what could cause the problem and is there a way to permanently fix it?

My router is Buffalo Airstation WHR-G54S with original firmware.

---

### Post by nixscripter on 2008-05-21
It looks like there is a problem where the connection table in the router can be filled if you have too many connections:

[http://www.wirelessforums.org/network-troubleshooting/buffalo-ip_conntrack-table-full-dropping-packet-42496.html](http://www.wirelessforums.org/network-troubleshooting/buffalo-ip_conntrack-table-full-dropping-packet-42496.html)

Do the logs show a similar message? What else do you have running on that machine (or on the network)?

---

### Post by ncosens on 2008-05-24
I'm not getting anything in the logs when it happens.  Just the standard dhcp login/logout and ack requests.

If it helps I'll give my network setup:

We have Verizon's EVDO broadband internet which is recieved on a PCMCIA card.  This is in a desktop computer we otherwise wouldn't use via a PCMCIA to PCI adapter.  Then we enable connection sharing in Windows using a static IP on the network card.  I then point the router to it as the internet gateway.  And bingo, shared internet for my house.

Computers on the network are mine physical (duel boot WinXP and Ubuntu separate hdd though), and 2 identical Toshiba laptops with WinXP MCE Wi-Fi.

---

### Post by nixscripter on 2008-05-26
In that case, I would make a few simple suggestions for when you can afford to be offline for a while:

1. Try putting the PCMIA card into one of the laptops directly, assuming one has an open slot. Perhaps that adapter isn't working as well as it should.

2. See if you can use the device with Ubuntu. Not that I don't trust windows (*cough cough* ;-) ), but perhaps sharing is doing something funny. There are some (admittedly not tested by me) instructions here: 

[http://www.linux.com/feature/52729?theme=print](http://www.linux.com/feature/52729?theme=print)

3. Are you sure nothing else is being dropped, or is web browsing simply what you do the most? Try something else like a long, drawn out bit torrent transfer and see if the drops occur. I would never suggest getting something illegal ;-), so here is a 3.6 GB Ubuntu install DVD for a test:

[http://torrent.ubuntu.com/releases/feisty/release/dvd/ubuntu-7.04-dvd-i386.iso.torrent](http://torrent.ubuntu.com/releases/feisty/release/dvd/ubuntu-7.04-dvd-i386.iso.torrent)

Azureus is a bit torrent client which can be installed from the Synaptic package manager.

Hope this helps.

---

### Post by ncosens on 2008-05-27
I don't need to test it from the laptops because it's not the gateway that's causing the issue.  I have tested that by connecting my computer to the gateway directly with a crossover cable during one of the failures and the internet works just fine shared.

Back before I canceled my subscription I could still play World of Warcraft when a failure occurred.  Now I play the free Last Chaos which works much better with the high latency native to EVDO.  Or maybe it's a bug in Windows internet connection sharing.

Also I can't test it with a large file download because my ISP limits me to 5 GB per month :mad:   stupid Verizon, charging $60 per month for 5 GB

It doesn't help that because of the type of internet I have (EVDO) the cell towers kick the card off the network every 23 hours 55 minutes or so.  Yet sometimes it disconnects after 3 hours and sometimes 3 days.  But that's a bandwidth conservation issue addressed at the tower and server level.

I have followed those instructions (from a different source though) before when I had both PuppyLinux and Damn Small Linux on the gateway.  One issue though is that they are for the PC5740 and I have the PC5750.  Strangely the PC5750 is made by Audiovox for Verizon but has the same chipset as the Pantec PX-500 for Sprint.  And both companies (Audiovox and Pantec) are owned by Korea based Curitel Communications, Inc.  The PC5750 includes the newest EVDO revision as the PC5740 is 2 years older (estimated).  So I don't know if the commands are different or not.  I am very temped to go try and see if I can get it to work on Linux.

It is possible that this issue may be resolved within the next few months by one of two ways.  The first being an investment in one of the routers that have a PCMCIA slot built in.  The second being a different type of internet service.  Not sure what the tech is called but it works by beaming the data between satellite dishes pointed at each other over a few miles distance.  Supposedly the throughput is somewhere around 1 to 6 Mbps duplex.

Oh, the PC5740 has the product ID of 3701 while the PC5750 is 3702

---

### Post by nixscripter on 2008-05-28
I'm sorry to hear about your --- er, bureaucratic restrictions.

I can only suggest that, given what I know about such cards, the instructions will probably work. The reason is that that driver being used is nothing more than a USB-to-serisl converter driver. This suggests to me that the card is just implementing the serial interface (like a normal modem) over the USB protocol. If I were a device manufacturer, that would be the wisest move so that drivers wouldn't have to be rewritten. Assuming you change the product ID to 3702, which is just which card the driver looks for, it should be the same.

As for internet service, I am assuming you can't buy cable or DSL, since they would otherwise be far cheaper than the kind of pipe you are paying for now. Satellite internet, gotten nowadays through many satellite TV companies (e.g. Dish Network), has good bandwidth, but very high latency. All the data must travel (at the speed of light) from your house, to an oribiting sattelite, around to a few more, and then back to Earth at their routers. At 23,000 miles each way, the latency is over 500 ms for a round trip. Not good for games, fine for web browsing.

---

