---
title: "Losing connection"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by ortwein on 2008-04-04
Here is my situation:

I have a DSL connection through Embarq.  In order to use bit torrent I have to bridge my modem.  This works fine, and I no longer lose my connection.

But...

My employer recently issued laptops to all employees.  Thus I purchased a Linksys WRT54G wireless broadband router.  Now my wifi connection won't work when the modem is bridged.  I'm sure this is simply a matter of changing a few settings in my modem...but I don't know how.

I'm a complete novice at this, and would greatly appreciate some a very simple walkthru on how to get both computers (my desktop and my laptop) fully functional and capable of using torrents.

Mark

P.S.  I'm using Kubuntu (Hardy Heron)

---

### Post by anjilslaire on 2008-04-04
Why must you bridge anything to use bittorrent? It simply uses its own ports like any other...
I have that router. Plug your DSL modem into the WAN port, and plug your desktop into the LAN side.  Out of the box, the Linksys will auto-detect most everything for you.

Also, if I were you, I'd change the SSID and enable MAC filtering plus WPA for your wireless, btw

---

### Post by ortwein on 2008-04-04
The reason I bridged my modem (prior to getting the laptop) is that I'd lose my connection anytime I would try to use bittorrent.  This is an issue with my modem--a Zyxel 660r. 

What information can I supply you about my setup that might be helpful in diagnosing my issue?

Mark

---

### Post by anjilslaire on 2008-04-04
After a quich google check, I've found this, among others:
[http://kb.earthlink.net/case.asp?article=69205](http://kb.earthlink.net/case.asp?article=69205)
> 
 Zyxel 660R-61 - How to Configure Router for Bridge Mode

In order to configure your router for a home network, you will need to configure it for Bridge Mode. 

It seems to me this may not neceesary now that you have the linksys. Unbridge your modem, and put the Linksys on it, via the Linksys WAN port. Your modem now has 1 device conected to it
Now, place your PC onto the router via one of the LAN ports. Your Modem still only sees 1 device, the router. This is normal.
Log into your modem, and disable any wifi function it may have. You don't want it interfereing with the wireless signal your router provides.

Your Linksys should now manage all PCs connected to it, wired or wireless, and no further bridging should be necessary.

EDIT:
this thread may help also, as I'm not familar with this modem: [http://www.tipidpc.com/viewtopic.php?tid=135091]("http://www.tipidpc.com/viewtopic.php?tid=135091")

---

