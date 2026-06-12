---
title: "Server disrupts router when connected to network (via Ethernet)"
date: 2015-02-04
forum: Networking &amp; Wireless
---

### Post by Anthony_De_La_Rosa on 2015-02-04
Hey guys,

I have a weird issue with my setup. I have a server running lubuntu and connecting it to router (netgear WNDR4300) cuts off internet access and wifi. I'm still able to access any other device connected via ethernet but I'm completely disconnected from the internet.  Once I disconnect the server, internet comes back and works great.  I've tried setting up a static IP, flushed eth0, removed and re-added default gateway using "route", used "mii-tool" to change the negotiation from 1000base to 100base and none of these worked. Don't know what else to try.

---

### Post by SeijiSensei on 2015-02-04
Sounds like bad hardware to me.  Did you try using a different Ethernet cable?  If you have a spare network card, drop that in the box and see if that helps.

---

### Post by Anthony_De_La_Rosa on 2015-02-04
Thanks for the quick reply. Yea, I've used a different ethernet cable but no dice.  Unfortunately, I don't have a spare network card. I want to exhaust all my other options before I buy a network card that I didn't need.

---

### Post by oldos2er on 2015-02-04
Moved to Networking & Wireless.

---

### Post by Anthony_De_La_Rosa on 2015-02-07
Friend of mine let me borrow his NIC card and no dice. Entire network loses internet access whenever the server is connected to the network.

---

### Post by steeldriver on 2015-02-07
Could it be an address conflict? are you sure the server isn't stealing the gateway IP? sorry to ask, but since you haven't posted any actual ifconfig or routing information it's not clear

---

### Post by Anthony_De_La_Rosa on 2015-02-07
Here's a screenshot of both commands: [https://www.dropbox.com/s/9izb4dxnb40zm9o/networkDiag.png?dl=0](https://www.dropbox.com/s/9izb4dxnb40zm9o/networkDiag.png?dl=0)

---

### Post by steeldriver on 2015-02-07
Right, but what do other clients on the LAN think their gateway is?

---

### Post by Anthony_De_La_Rosa on 2015-02-07
the other clients use 192.168.0.1 as their gateway

---

### Post by Anthony_De_La_Rosa on 2015-02-21
bump

---

### Post by Anthony_De_La_Rosa on 2015-03-04
bump

---

### Post by Anthony_De_La_Rosa on 2015-04-08
bump

---

### Post by michi1983 on 2015-04-08
have you tried another computer on that exact same port of the router? 
and if that also doesn't work have you tried another port on the router?

---

### Post by Anthony_De_La_Rosa on 2015-04-25
> **michi1983 said:**
> have you tried another computer on that exact same port of the router? 
and if that also doesn't work have you tried another port on the router?

Yea, I've tried other PCs on the same port and tried the PC in question on a different port of the router with no luck.

---

### Post by michi1983 on 2015-04-25
So other pcs create the same 'failure'?
I would exchange the router then.

---

### Post by Anthony_De_La_Rosa on 2015-04-25
> **michi1983 said:**
> So other pcs create the same 'failure'?
I would exchange the router then.

Sorry, let me clarify. The other PCs work fine on all ports.

---

### Post by michi1983 on 2015-04-25
Okay, so two more things you can test.
Boot a live linux on your system with CD or USB pen drive.
If the problem persists, it's likely that your NIC is damaged.
You could then try a USB NIC adapter to verify if everything works.

---

### Post by Anthony_De_La_Rosa on 2015-05-09
> **michi1983 said:**
> Okay, so two more things you can test.
Boot a live linux on your system with CD or USB pen drive.
If the problem persists, it's likely that your NIC is damaged.
You could then try a USB NIC adapter to verify if everything works.

I finally got around to test it with the live usb.  it seems to be running fine while on the Live USB. no issues with the router while in LIVE USB. This leads me to believe that there's some setting somewhere in my installation that is wrong.

---

