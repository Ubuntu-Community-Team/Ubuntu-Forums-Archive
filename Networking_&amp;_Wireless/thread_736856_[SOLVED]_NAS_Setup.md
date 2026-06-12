---
title: "[SOLVED] NAS Setup"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by 71fnRVVm on 2008-03-27
Hey everyone,

I've got a slowly growing network here, and I'm trying to add some NAS to it.

I bought a Linksys Network Storage System (two empty enclosures, plus two USB connectors), and hooked it up to the network.

The network looks like (as far as this matters):
DSL Modem -> 5-port Router -> 5-port Switch:  (1) network printer [works fine], (2) the NAS

Like I said, the printer works fine through the switch that sits on top of the router, but I can't figure out how to use the NAS.  Ubuntu didn't autorecognize the drives that I connected to it (two USB externals plugged in through the NAS system, both work fine when directly plugged into the computer).  I tried to add the IP address that the switch has through the Shared Folders -> Unix -> Add -> Specify by IP Address... but that didn't work.

Is there something I missed, or haven't done correctly?

Thanks

---

### Post by SpaceTeddy on 2008-03-27
shouldn't the nas itself pull an ip address from your local dhcp server (ok, if that was not understandle, sorry)

what any client in an IP based network does, it look for a server that will autoconfigure it. This is usually the DHCP server, and in most cases it will run on a router somewhere in your network. in your case most likely the 5-port-router.

when you plug the nas in, it should pull an ip address from that router. What you need to do is figure out what ip address got pulled and then connect to that one. Any nas should support the windows protocol - so once you have the IP of the device itself (not the one from the switch) you can go into your filebrowser and type
> smb://**IP-Address**
where you replace the IP-Address with the real ip and you should be able to access it. 

Also, maybe the thing needs to be configured. In this case, i would put my money on a web-configuration - i.e. open up a browser and put the ip of the device in. there should be a  configuration page comming up :)

hope this makes sense and there is something new in there

---

### Post by 71fnRVVm on 2008-03-29
No, that's what I'm saying.  The IP address is the router port... which is connected to a switch, that shares the IP for data transfer between printer and NAS.  Theoretically, this is feasible.

I tried going to the IP address itself, but it brought up the printer (it's a "network-ready" printer so that's a big feature for it)...

If you're still not following, I guess I can try and draw a picture of the setup.

Thanks

---

### Post by SpaceTeddy on 2008-03-29
can you give me a manufacturer and a model number of the nas you are using so i can have a look at the manual myself. i think that would be the best way of going about solving this... 
also, i really like pictures. Please draw one :)

---

### Post by Iowan on 2008-03-30
I guess a picture would help - if I read your text description correctly, the NAS and printer connect to the switch.  You didn't mention where the Ubuntu box connects - the switch or one of the other router ports.  Switches don't have an IP address.  Your description leads me to think the Ubuntu box is on a different router port - which suggests you may have some route tweaking to do in the router.
Or... you could try connecting the Ubuntu box to one of the switch ports.

---

### Post by 71fnRVVm on 2008-03-30
Because it's DSL and not Cable, I have to give IP addresses to items, aka why it's a router in the first place.  A switch on a single IP works for in-network data transfer, but I can't connect any computer to a port on that switch.  Follow?

A beautiful image of my network:  [http://www.kyle-brady.com/images/myNetwork.jpg](http://www.kyle-brady.com/images/myNetwork.jpg)

And, finally, it's a "Linksys NAS200 Network Attached Storage Enclosure"

Thanks

---

### Post by Iowan on 2008-03-30
> **brady.k said:**
> I tried going to the IP address itself, but it brought up the printer (it's a "network-ready" printer so that's a big feature for it)...... because the IP address is for the printer, not the switch - the NAS will have it's own IP address, either via DHCP from the router or static via it's configuration file.

Can you see the NAS from one of the other machines?

---

### Post by 71fnRVVm on 2008-03-30
a)  No it won't?  A switch does not create IP addresses.  The one IP address is for *all* items on the switch.

b)  No, but the only computer other than this one is the Vista box which doesn't do most of the things it should.  So I'm not considering that as sign.

---

### Post by Iowan on 2008-03-30
From a terminal,type **nmblookup -T '*'**

BTW, how did you originally set up the NAS - I found information [here]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5253992678B08") that mentions using the (Windows) SetupUtility.exe to select addressing mode, mirroring (raid), mapping, etc.

---

### Post by 71fnRVVm on 2008-03-31
All I got was my Ubuntu box... not even the Vista.

As for the setup, the manual indicated "plug and play".  I'll install the software on Vista and try and config it, so I'll be back later.

Thanks

---

### Post by Gina on 2008-03-31
> **Iowan said:**
> From a terminal,type [B]nmblookup -T '*'[/BThat's very useful info - thanks.  Enabled me to find the address of my new NAS drive (1TB WD My Book World Edition)

---

### Post by 71fnRVVm on 2008-04-03
Good call.  It had to be setup using a Windows machine.

It works now!  Thanks!

---

