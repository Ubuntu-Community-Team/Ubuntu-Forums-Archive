---
title: "make two routers &quot;talk&quot; wirelessly??"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by darkenedday on 2008-01-13
I just moved, and have 2 laptops, a mac, and a pc, sadly at the moment none of them are running linux at all, but this is mainly because I need the mac for cs3 and the pc's and laptops for family

I don't want to run wires all through this place, and I don't have a wireless adapter that works with my mac g4 cube with mac os 10.3 panther, I do however happen to have two wireless routers and airlink101 and a linsys, the linsys being the nwere of the two is natural set up now as the only router, bother wireless and wired, I would like to put the other upstairs with my mac and simply connect to the cube's ethernet password, I was wondering if it is possible to make the two routers "talk" to eachother wirelessly maybe with the airlink simply set up as some sort of wireless access point or hub?

if so how?

thanks in advance

---

### Post by jflaker on 2008-01-13
There are 2 ways of doing this

Run a single wire between the routers.....The secondary router's WAN/INTERNET port plugs into the PC ports on the primary router.

Get a repeater, AKA, A range extender.  The extender is a relay which allows you to extend the wireless range by placing the device closer to where a signal is needed but within range of your wireless access point.

The first option is the cheaper solution but leaves you with a wire across the house.  The second option is not as cheap but is very clean.

Good luck.

---

### Post by darkenedday on 2008-01-13
thanks for the advice but I think my question was misunderstood

I will, of course, run wires if I have to

the mac cube can not connect wirelessly, so the repeater is unhelpful, my signal strength for the laptops is fine, I simply am wondering if I can possible get the two routers to work together wirelessly then plug my mac in with a short wire to the airlink101 upstairs and use the itnernet connection from the linksys router downstairs

---

### Post by jflaker on 2008-01-13
Sorry, misunderstood

You are talking about a wireless bridge
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175234727910&packedargs=page%3DL_Product_C2%26sku%3D1175234727910&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2791028788B01](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175234727910&packedargs=page%3DL_Product_C2%26sku%3D1175234727910&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=2791028788B01)

Linksys was used as an example, but any wireless bridge SHOULD work.

This allows you to do what the wire between the two routers is doing but utilizing the wireless signal..

Hope this helps.

---

### Post by kevdog on 2008-01-13
If you can install dd-wrt on the linksys, you can actually make the linksys into a repeater/bridge, which will allow your clients to connect to the linksys router as a client, however in effect it is repeating the wireless signal from the 1st router that is actualy connected via a wire to the internet modem.  Its good if you need to rebroadcast your signal to a different part of the house -- ie main connection downstairs -- bad upstairs coverage -- put repeater/bridge upstairs - and then have good signal both upstairs and downstairs.

---

### Post by steeleyuk on 2008-01-13
If your routers support RIP (or another routing protocol) over wireless then you'd be able to do it. Though most home routers probably don't do it. I'd have a search around with your router model numbers to see if they support RIP over wireless.

---

