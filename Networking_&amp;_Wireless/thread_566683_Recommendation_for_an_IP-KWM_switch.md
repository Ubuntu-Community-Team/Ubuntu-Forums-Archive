---
title: "Recommendation for an IP-KWM switch"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by npumcrisz on 2007-10-03
[B]Please no software IP-KVM switch  but hardware only. 
[/B]

I need a single unit and not multi-unit IP-kvm switch to controll a small but growing data center. It's presently equipped with 3 laptops, 3 workstations and 5 1u servers. The servers are and shall be in another room and the laptops, workstations in different rooms. 

Presently connected by KVM switch but the hassle is getting to me. I am the sole IT guy for now.

Servers are presently OS X server and Windows server but hope to add Ubuntu, FreeBSD, OpenBSD and Solaris. 

1 or no local node would be okay. Prefer to work remotely ie via LAN

---

### Post by PilotJLR on 2007-10-03
Avocent DSR's are best.
Raritan Dominion KX is good too, and a little less expensive.

But KVM over IP is pricey no matter how you look at it.

---

### Post by npumcrisz on 2007-10-03
> **PilotJLR said:**
> Avocent DSR's are best.
Raritan Dominion KX is good too, and a little less expensive.

But KVM over IP is pricey no matter how you look at it.

Please confirm, the above recomendation are 2 unit equipments. That is one to connect to the servers. The second connects the first unit to the remote / local user. 

My original post was I wanted a single unit and not a multi unit.

---

### Post by PilotJLR on 2007-10-04
I have absolutely no idea what you just said. "Single unit" and "multi unit" is kinda made-up terminology, so can you clarify or elaborate?

Both boxes I mentioned are standalone appliances, which (to me) makes them "single units". Do you mean you want to add IP reach to an existing analog KVM?

---

### Post by npumcrisz on 2007-10-11
> **PilotJLR said:**
> I have absolutely no idea what you just said. "Single unit" and "multi unit" is kinda made-up terminology, so can you clarify or elaborate?

Both boxes I mentioned are standalone appliances, which (to me) makes them "single units". Do you mean you want to add IP reach to an existing analog KVM?

One device only, that is one equipment /box /unit. 

Scenario 1: With a single unit IP-KVM switch: 
[LIST=1]
[*]Connect host computers to the IP-KVM box using a 3-in-1 cable or a KVM cable.
[*]Connect monitor, keyboard and mouse directly to IP-KVM box for Local Administrator. 
[*]Connect IP-KVM directly to Remote Administrator's computer via Ethernet.
[*] There must be no additional device between the IP-KVM box and the host computers.
[*] There must be no additional device between the IP-KVM box and the Remote Administrator's computer.
[/LIST]

Scenario 2: With a two unit IP-KVM  switch: 
[LIST=1]
[*]Connect host computers to the first unit of the IP-KVM switch configuration using a 3-in-1 cable or a KVM cable.
[*]Connect first unit to second unit of the IP-KVM switch configuration. Since first unit has no ethernet or modem interface.
[*]Connect monitor, keyboard and mouse to either first or second unit for Local Administrator. 
[*]Connect second unit of the IP-KVM switch configuration directly to Remote Administrator's computer via Ethernet. Since second unit has ethernet or modem interface.
[/LIST]

 NB the first and second unit are always sold together and are most often of the same brand. The first unit unless recommended by manufacturer is purchased from the same manufacturer of first unit. You can't connect any kvm switch to the second unit of this configuration type

The recommendation from you uses scenario 2 but I'm looking for 1.

---

### Post by volkswagner on 2007-10-11
Is $1500.00 in the budget.  

[http://www.blackbox.com/Catalog/Detail.aspx?cid=537,604,541&mid=5125]("http://www.blackbox.com/Catalog/Detail.aspx?cid=537,604,541&mid=5125")

Your method one seems to increase the price about three fold.  

Blackbox has quality stuff.

---

### Post by tech9 on 2007-10-11
> **npumcrisz said:**
> [B]Please no software IP-KVM switch  but hardware only. 
[/B]

I need a single unit and not multi-unit IP-kvm switch to controll a small but growing data center. It's presently equipped with 3 laptops, 3 workstations and 5 1u servers. The servers are and shall be in another room and the laptops, workstations in different rooms. 

Presently connected by KVM switch but the hassle is getting to me. I am the sole IT guy for now.

Servers are presently OS X server and Windows server but hope to add Ubuntu, FreeBSD, OpenBSD and Solaris. 

1 or no local node would be okay. Prefer to work remotely ie via LAN

IP-KVM are not cheap... good luck

---

### Post by PilotJLR on 2007-10-11
> **npumcrisz said:**
> One device only, that is one equipment /box /unit. 

Scenario 1: With a single unit IP-KVM switch: 
[LIST=1]
[*]Connect host computers to the IP-KVM box using a 3-in-1 cable or a KVM cable.
[*]Connect monitor, keyboard and mouse directly to IP-KVM box for Local Administrator. 
[*]Connect IP-KVM directly to Remote Administrator's computer via Ethernet.
[*] There must be no additional device between the IP-KVM box and the host computers.
[*] There must be no additional device between the IP-KVM box and the Remote Administrator's computer.
[/LIST]

Scenario 2: With a two unit IP-KVM  switch: 
[LIST=1]
[*]Connect host computers to the first unit of the IP-KVM switch configuration using a 3-in-1 cable or a KVM cable.
[*]Connect first unit to second unit of the IP-KVM switch configuration. Since first unit has no ethernet or modem interface.
[*]Connect monitor, keyboard and mouse to either first or second unit for Local Administrator. 
[*]Connect second unit of the IP-KVM switch configuration directly to Remote Administrator's computer via Ethernet. Since second unit has ethernet or modem interface.
[/LIST]

 NB the first and second unit are always sold together and are most often of the same brand. The first unit unless recommended by manufacturer is purchased from the same manufacturer of first unit. You can't connect any kvm switch to the second unit of this configuration type

The recommendation from you uses scenario 2 but I'm looking for 1.


No, both of my recommendations are stand-alone appliances. I have used both of them this week at work, so trust me on this and read the links again.  ;-)

Both are IP-KVM's... both use cat5 to dongles at the server ports (as do all IP KVM's), and both have 1 local user and X remote users.

Price-wise, though... yeah, you're looking at several thousand dollars. They are still fairly expensive. If you can get management cards with console licenses for the servers, that is often cheaper. For example, iLo on HP servers can effectively become an IP KVM if you add a console license key.

---

### Post by npumcrisz on 2007-10-12
> **volkswagner said:**
> Is $1500.00 in the budget.  

[http://www.blackbox.com/Catalog/Detail.aspx?cid=537,604,541&mid=5125]("http://www.blackbox.com/Catalog/Detail.aspx?cid=537,604,541&mid=5125")

Your method one seems to increase the price about three fold.  

Blackbox has quality stuff.

Yes $1500 in budget. For $1500 the blackbox  can't handle the number of servers I want.

---

### Post by npumcrisz on 2007-10-12
> **PilotJLR said:**
> No, both of my recommendations are stand-alone appliances. I have used both of them this week at work, so trust me on this and read the links again.  ;-)

Both are IP-KVM's... both use cat5 to dongles at the server ports (as do all IP KVM's), and both have 1 local user and X remote users.

Price-wise, though... yeah, you're looking at several thousand dollars. They are still fairly expensive. If you can get management cards with console licenses for the servers, that is often cheaper. For example, iLo on HP servers can effectively become an IP KVM if you add a console license key.


I had to download the user manual for your recommendations to agree with you. :cool:

PS check hxxp://www.rackmountmart.com there are listed IP-KVM for approximately $500- $1500. Mark you not extenders. These can handle 8 to 32 servers using RJ45 or DB-15. 

My question are these ip-kvm on rackmountmart for real? :confused:

---

### Post by PilotJLR on 2007-10-12
I would be very wary of that... I personally haven't seen these before, but their website has no support section, and the user manual for the KVM is mostly just how to physically install the thing. IP KVM's are basically servers, so they need a lot more detailed information on the interface and software components. You'll probably get what you pay for on this one!

---

### Post by npumcrisz on 2007-10-13
Already suspiciuos of the deal. Tnanks for your input.

---

### Post by mchaggis on 2008-03-27
I have another idea to keep the cost down and was wondering what peoples thoughts where....

I have seen the following:
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=244499&CatId=598](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=244499&CatId=598)

It is a IP-KVM for a single machine, in that it will only allow you to KVM over network to a single machine.

My requirements are that I need to be able to do this on 4 machines, but certainly do not have the finances available to throw hundreds of pounds at it, so I was thinking...

If I purchased (dusted off) a standard KVM unit with the standard 1x 3cable input and 4x 3cable outputs, could I then connect the above product to the input ports and make it networked?

As this would mean the total cost would be under 100pounds?

---

### Post by PilotJLR on 2008-03-29
Woah there!

That link is merely a dongle... yes, they do cost that much. That part is 100% useless unless the other end is attached to a Raritan KVM over IP.

---

### Post by PilotJLR on 2008-03-29
The cheapest 1 port KVM over IP I would ever use is actually a PCI card:
[http://www.raritan.com/products/embeddedproducts/ericg4/](http://www.raritan.com/products/embeddedproducts/ericg4/)

It's basically like a 3rd party version of iLo Advanced. Of course, each server would need this. Times 4 servers, this is cheaper than a KVM-over-IP appliance switch.

---

