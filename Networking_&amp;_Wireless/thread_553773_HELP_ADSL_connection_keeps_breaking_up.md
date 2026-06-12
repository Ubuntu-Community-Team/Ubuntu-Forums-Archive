---
title: "HELP: ADSL connection keeps breaking up"
date: 2007-09-18
forum: Networking &amp; Wireless
---

### Post by Udibuntu on 2007-09-18
Hey Guys,

I apologize for bumping an issue much debated, but I'd appreciate your help in fixing this:

My Ubuntu Feisty 64bit keeps breaking up my ADSL connection.

Wireless connection works just fine (surprisingly...), but wired connection keeps disconnecting without notice.

I must poff and pon to resume connection, sometimes even pppoeconf.

I tried both DHCP and roaming enable, both work but disconnect abruptly.

I'm new to Ubuntu (worked with Fedora 4 and loved it [I'm old...])

Is there a fix?

Cheers,

Udi

---

### Post by mips on 2007-09-18
Ethernet or USB ?

If ethernet then you have a router which is in bridged mode. I would put it into routed mode and get rid of the pppoe stuff.

---

### Post by Udibuntu on 2007-09-18
Cheers mate, I indeed use eth router.

I don't know how to fiddle with the router, though, or even if my ISP  can or will still provide the service.

Udi

---

### Post by mips on 2007-09-18
Tell me the following:

1. Exact make and model of router
2. Who is your ISP with a link to their website

and I will try and help.

---

### Post by Udibuntu on 2007-09-18
Cheers Mips, I've contacted their support center. Will update after they callback.

---

### Post by mips on 2007-09-18
> **Udibuntu said:**
> Cheers Mips, I've contacted their support center. Will update after they callback.

Why do that ? You mention the word 'linux' and they will say that they don't support it and it does not work. Typical ISP response...

---

### Post by Udibuntu on 2007-09-18
Oh so true....

They said I need to escalate this to a "senior support rep" who "knows about Linux".

I need to talk to them tomorrow, when this legendary rep is on duty...

I'm logging off now, will update tomorrow.

Thanks mips for your help.

Udi

---

### Post by damansandhu on 2007-09-18
mine router is also is in bridge mode , and its not working , i dont know why , internet gets connected but no website opens . when i put it in pppoe mode , then it works but i need bridge mode.

---

### Post by Udibuntu on 2007-09-19
Gee Guys, what can I say - the rep DID know what he was talking about (AFAICS)..

The disconnection occurred (so it seems) each time the ADSL modem changed IP vs my laptop, not related to the ADSL connection to the ISP (according to the rep...)

We solved the problem in an indirect way - we took my connection off the DHCP mode and into Static IP mode.

Since my "router" is a very poor performance type we didn't change any of its settings as to not put any more load on it, and there were really no apparent need to do so.

I hope this solution can be used by others with the same problem, or at the least give an option to check and rule out.

Again, thank you guys for trying to help.

I'm off to the next challenge - making my Ubuntu Feisty 64bit cope with Flash :(

Cheers,

Udi

---

