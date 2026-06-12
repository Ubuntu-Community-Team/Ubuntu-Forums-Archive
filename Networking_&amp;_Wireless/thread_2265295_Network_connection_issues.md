---
title: "Network connection issues"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by fzaman2 on 2015-02-14
Hi,

Really new to the command line interface and having issues with the machine connecting to the internet.  All of my other machines can connect no problem so I am pretty sure the problem lies with my settings on the ubuntu box.  During install it said it could not find DHCP server so I manually configured the settings with all of the info from my wireless router.  I also added DNS servers 8.8.8.8 and 8.8.4.4 to the list for good measure...still no joy.  

[ATTACH=CONFIG]259962[/ATTACH]

Above is a pic of the readout of what I have when I run ifconfig -a

Sorry for not pasting directly, but I am using a web interface on my mac and can't get it to copy.

Any help would be appreciated...This is driving me nuts

---

### Post by steeldriver on 2015-02-14
Can you break down what you mean by "issues with the machine connecting to the internet"? Can you:

- ping another machine on the LAN by its numeric IP address but not...
- ping an external host e.g. 8.8.8.8 by its numeric IP but not...
- ping an external host by name e.g. google.com but not...
- etc.

Is your LAN address range really 192.168.**8**.0/255?  also you mention a wireless router but the populated interface (em1) looks more like an onboard ethernet interface.

---

### Post by fzaman2 on 2015-02-14
I am unable to ping anything including the router at 192.168.8.1 or 8.8.8.8 or google.com. 

 Yes that is what the routers ip range is set up as. Kind of annoying but at the same time didn't want to bother changing it. 

I have a wired connection from server  to the wireless access point/router. 

There are actually 4 network ports built into the motherboard and I have connections to two of them. This was based on a blog I was reading on how to build the server with this particular board.

---

### Post by steeldriver on 2015-02-14
sorry I don't have experience with running multiple interface setups, however you should probably start by looking at the routing table entries e.g.

```

ip route list

```

---

### Post by fzaman2 on 2015-02-14
Thanks for the suggestion. I'm guessing it's probably something simple but I don't know what

---

### Post by fzaman2 on 2015-02-14
So figured out what was wrong...had the network cable only hooked up to the IMPI port and needed a second cable to work.  When I plugged it in, it wasn't getting any activity, so went to BIOS and messed w/ that for a bit and was able to find where to activate the various network ports.

Thanks for the help

---

