---
title: "Wierd Question about Printer sharing"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-09-28
Well,
In sequence to the wierd quesitions I have been asking
of late , here is another one..

At my place , one of the Windows systems is connected to a printer.
and is also connected to the LAN.
we have lots of Ubuntu systems here that are also connected to the same
LAN..

What my question is...
We want to make one of the Ubuntu box be the server for all requests to
print from other Ubuntu boxes . And it shud then forward the request to the Windows  printer and print the doc.

Is this possible..we want to do it to reduce the Windows box from overloading

forgive me if its not clear..

---

### Post by kidders on 2006-09-28
Hi there,

I don't quite follow the logic behind your question :-( If the Windows box winds up printing your documents anyway, how does relaying the data via a Ubuntu box help with load issues?

---

### Post by hellmet on 2006-09-28
ask my boss:mrgreen: thats the reason I said it was wierd tho
I have no clue as to how to do it btw..do u have any?

---

### Post by kidders on 2006-09-29
Not off the top of my head :-( I'm not sure that the Windows sharing protocols support any nice load balancing features, like CUPS does, for example.

The smartest (most flexible) solution would be to plug the printer into a Linux box and share it that way.

---

### Post by hellmet on 2006-09-29
ok..we'll discuss that issue tho..
thnks for the help

---

