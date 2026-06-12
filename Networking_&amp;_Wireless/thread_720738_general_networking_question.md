---
title: "general networking question"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by calman on 2008-03-10
This doesn't have much to do with Ubuntu, but I don't want to make an account somewhere else, and it's a simple question most people probably know, I just have horrible experience with networking.  Here's what I want to do:

```

----cable tv cord-----cable modem>--------------------------wired computer  #1
                                 |
                                 ^-----wireless router>-----wireless laptop #1
                                                      ^-----wireless laptop #2


```
So basically, I'm splitting the ethernet that comes out of the cable modem, one of the split wires goes to a computer, the other goes to a wireless router.  I know there should be a router behind the wired computer, but it's complicated why I can't have one...Is this setup possible?  Are there any reasons why I shouldn't do this?  Thanks

---

### Post by ryanhaigh on 2008-03-10
I don't think you can split a single ethernet port over two PCs, does the cable modem have multiple ethernet ports? If you want the computers to be able to communicate you might need to disable dhcp on the router and use it as a simple switch so all IPs are assigned by the modem.

---

### Post by Whiffle on 2008-03-10
Why not connect the router to the modem, and connect the wired computer to the modem.

---

### Post by calman on 2008-03-10
OK, I thought I might have to do something with DHCP because I figured the IP assigned by the modem and the IP's assigned by the router would conflict.  And I was planning on splicing the ethernet cord (the modem only has 1 ethernet output).  That wouldn't work?

---

### Post by calman on 2008-03-10
> **Whiffle said:**
> Why not connect the router to the modem, and connect the wired computer to the modem.

Because of the way it's set up...it's complicated

---

### Post by Whiffle on 2008-03-10
Yeah I actually meant router instead of modem...

But, does this modem have a USB connectoin on it as well?  it might allow you to use both ethernet and usb.  Other than that I don't really see a way to do what you're trying to do, at least not without buying more hardware.

---

### Post by calman on 2008-03-10
What kind of hardware would I need?  Basically I was just hoping to find out if this would work, there aren't many other ways I can do it...and yes it does have a USB connection but I would much rather intercept the outgoing ethernet cord.

---

### Post by handydan918 on 2008-03-10
Well, that you can't do. Splicing into a utp cable won't work. 
Maybe you should give some detail on why you can't go modem>router>hosts.

---

### Post by calman on 2008-03-10
Alright, well, I can do modem > router > hosts and apparently I have to.  It's just that the way I have everything laid out in my basement it would be easier to do it this way.  I want the wireless router further from the modem.  Thanks for the help.

---

### Post by Eiríkr on 2008-03-10
If by "further" you mean physically, get a longer CAT5 cable for between the modem and router.  If instead you mean you want a computer in between the router and modem, you can buy a second network card for the in-between computer, and then connect modem -> in-between -> router -> other computers.  Then any traffic will have to go through the in-between before it hits the outside world.  This can be useful if you want to do traffic analysis or anything else fancy that your router doesn't support.  

Cheers,

Eiríkr

---

