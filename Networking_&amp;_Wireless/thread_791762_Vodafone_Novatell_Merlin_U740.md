---
title: "Vodafone Novatell Merlin U740"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by gr@nt on 2008-05-12
Hi Guys,

Im beginning to loose hope on getting my 3g card to work, i have a vodafone novatell merlin u740 pcmcia card, i have read numerous forums, how-to's, etc on how to get this thing to work, none of them have helped me.

Could some one very clued up with ubuntu help me get this 3g pcmcia card to work, i will be really appreciative!!

Oh, and im running ubuntu 8.0.4.

Thanks everyone!!

Later

---

### Post by cmdekok on 2008-12-22
I don't know if this helps much but what I've seen is that if you use your card to connect via a VMware image of Windows, enter the pin, connect and then disconnect, then disable the card from the VMware image and try and connect again via Ubuntu 8.10 Network Manager it works!

Bit of a long work around but I could not find any other way of doing this.

---

### Post by cmdekok on 2008-12-22
Sorry, just saw you were on 8.04, try using the BetaVine software it worked for me on 8.04

[https://forge.betavine.net/frs/?group_id=12&release_id=200](https://forge.betavine.net/frs/?group_id=12&release_id=200)

---

### Post by cmdekok on 2009-01-15
I got a solution, remove the pin check on your SIM card. I just inserted my SIM into my Nokia N70, remove the pin check under phone and sim settings. Now if you insert the merlin u740 into ubuntu it connects!!! A friend of mine told me about this trick. So if you are not worried about the pin code then this is an easy work around.


Now just don't loose your 3G card :p

---

