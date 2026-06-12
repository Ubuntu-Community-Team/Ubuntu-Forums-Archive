---
title: "internet sharing xp and dapper"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by lime4x4 on 2007-01-06
My brother in law wants to install dapper on a spare computer.He currently has a xp box that connects to the internet thru a dial up modem.I need to have the dapper box use the xp internet connection. How is this possible thru dapper?

---

### Post by kebes on 2007-01-06
In Windows XP there is something called Internet Connection Sharing (ICS) which allows one computer to provide a DHCP and NAT gateway to some other computer(s). So basically the XP machine would have the dial-up modem hooked up to the phone line, and then you run an ethernet cable* between the Windows XP ethernet jack and the Ubuntu machine's ethernet jack. (Obviously both computers need ethernet cards!)

On the Ubuntu end setting up the network should be trivial. It will auto-probe DHCP and get network access (assuming that Windows is serving it up properly).

So I think the hardest part will be getting Windows ICS working. It's been a long time since I've set up one of those, but I believe it's fairly straight forward.


*One thing to worry about: ethernet cables come in the "cross-over" and "straight through". Normally ethernet cables are "straight through" since they are designed to hook up from a computer to a router. However a direct computer-to-computer connection requires a "cross-over" cable. (Some modern ethernet cards will automatically switch mode if you use the wrong kind of cable, but with other cards you need to make sure you're using the right kind!)

I hope that helps...

---

