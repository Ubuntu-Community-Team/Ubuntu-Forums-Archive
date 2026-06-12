---
title: "What happened to the networking in dapper?"
date: 2006-07-26
forum: Networking &amp; Wireless
---

### Post by fragmental on 2006-07-26
I originally installed breezy on a different computer. It had no problem with networking after install.  Then I took that hard drive and stuck into a different computer.  Networking still worked without a hitch.

So, I upgraded to breezy and suddenly all I have is the loop back connection.  So I checked the modules, and the module(sis 900) seemed to be loaded.  I ran dhclient and sure enough, I have internet.  Is dhclient not being loaded by default or what?

Also, on a separate computer, the networking did load up by default, but I think that the network card wasn't being recognized for whatever reason, and it seemed to resolve itself whenever I moved the card(via rhine) to a different pci port.  However, I had to load the awe64 isa card module manually, but I had to do that with breezy too.

Two networking problems, in one day, with dapper, seems like a lot, though one of them may have been a hardware problem.

Edit: I just checked the system administration menu and found the networking settings.  I guess I just needed to set that up in there?

---

### Post by maddog39 on 2006-07-26
I had the same issue also, Breezy was alot easier to setup a network with. Dapper just lost it, dunno what happened.

---

### Post by ltolledo on 2006-07-27
Same problem with me, U5.1 BB's networking is better than U6.06 DD. So I'm sticking with U5.1 BB for the mean time until U6.06 DD's networking bug(s) gets a makeover.

I still have a pending thread here, maybe if some of the contributors here are able to troubleshoot the problem, then all of us with networking problems will be happier with U6.06.

....could it be that they're alreading working on the problem and incorporating it to U6.1?

---

### Post by meirbenezra on 2006-07-27
yeah I really cannot understand whats wrong with ubuntu after install. the whole network just worked fine with the live cd. well maybe there are some files that can be compared with the live cd and the intalled system so the differences can show sth? I dont know much about linux just a logic...

---

