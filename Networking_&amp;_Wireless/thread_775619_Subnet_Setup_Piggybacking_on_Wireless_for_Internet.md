---
title: "Subnet Setup: Piggybacking on Wireless for Internet"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Phoenix Rising on 2008-04-30
I have an interesting need here, and being somewhat of a networking newbie, was hoping you guys could help explain to me first if this is possible, and if so, how it would work.

**Setup**
One Mac OS X computer, one custom-built Ubuntu 8.04 system.  Both currently connect to the internet via 802.11g.

**Need**
I need to connect the PC and the Mac via WIRED ethernet connection to exchange large files back and forth, but I can't hard-wire them both into the router because it's just physically impossible - I'd have to run cable through a house that I don't own.

**My idea...**
Would something like the following work?

1.  Set up a second router in my office room.  Plug the PC and the Mac into the router via ethernet.
2.  Tell the router (how do I do this?) to use the existing wireless connection for internet for all clients connected to it.
3.  Tell the computers (how do I do this?) to use the first router that they're hard-wired to for internet and for exchanging files.

Here's some not-so-elite ascii art to explain what I'm getting at.

Mac (hard wired) ====> local wireless router
Ubuntu (hard wired) => local wireless router

Local wireless router -----> (wireless) ----> existing wireless router

Mac (transfers files) ====> local router <==== ubuntu
Mac and Ubuntu for internet =====> local router ----> wireless router

Internet signal ----> Wireless router -----> local router =====> Mac/Ubuntu

Hope that makes sense.  Please let me know if further clarification is needed.  Transmitting 10gb+ files over wirelss takes WAY TOO LONG, but I can't wire the damn thing because of the sheer physical distance between the router and the computers.

---

### Post by SpaceTeddy on 2008-04-30
Simple solution:
i'd wire them temporarily, move the files, and then unwire them again... you loose internet for that short period of time. But that should not be a problem for copying some files... 
The reason i suggest this, because the setup you are asking for is not trivial to do.

complex solution:
ok, that off my chest, i think i know what you want (as i said, i **think** i know). Regard your wireless connection as your ISP. It does not matter that it is a router somewhere else - for now, that Accesspoint both computer connect to **is your ISP**.

that off my chest, follow this [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874") to setup your ubuntu box to become a gateway for the Mac OS X (make sure you get the network interfaces right). This way, all traffic from the Mac will go through the ubuntu box when they are wired (thus making copying between the two fast) while the Mac can still be in the internet through the Ubuntu box. 
If the cable is removes, the mac can still use the Wifi directly as can the ubuntu.

One sidenote - make sure the wired connection between the two computers is not in the same IP subnet as the wifi hands out. If they are the same, the setup will not work ! **so make sure they are different.**

if something fails, just ask :)

---

### Post by Viper Daimao on 2008-04-30
have you thought of just hooking them directly to each other with a [crossover]("http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10232&cs_id=1023202&p_id=2375&seq=1&format=2") ethernet cable? I've only done that with 2 windows machines, but would that work for you?

---

