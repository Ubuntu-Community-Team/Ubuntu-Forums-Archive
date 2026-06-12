---
title: "Can't Keep an IP Address?"
date: 2013-10-09
forum: Networking &amp; Wireless
---

### Post by NorthBridge4839 on 2013-10-09
My ISP gives out these awful little Router/modem combos. The webpage when you connect to it (192.168.0.1) gives you the modem info but then has a separate page for the gateway. The wireless built into this little pile of crap doesn't work so we had to extend our network with a cheap little Belkin wireless router. I just hooked the Belkin up to the modem/router combo going from ethernet port 1 to ethernet port 1 on each and set it as a Access Point and turned off the firewall and whatnot. So now the only thing handling DHCP should be the router/modem combo. However, the DHCP server in the modem will usually assign me x.x.0.13 if it responds at all. And then it will randomly become unresponsive and I check my IP and it reverts to as if it never got a lease (169.x.x.x). Then I sit there trying to reconnect and reconnect until DHCP finally assigns me the same x.x.x.13 address and it'll work again for a little while.

Now for some reason it'll work for day or two at a time and then it'll fight me on giving me an IP. Like last night, my friend came over to use his laptop and he tried to log on. The DHCP would not give him an address. And then I stopped using my computer for a minute, it gave him my x.x.x.13 address and then my computer stopped working.

And on top of all that, the static IP setup on the router/modem page doesn't work so none of the settings stick.

Any ideas?
Would UPnP mess with any of this for any reason?

---

### Post by scbingham on 2013-10-10
You haven't mentioned the make & model of your modem/router, which makes it difficult for people to help you check any settings etc.
If the DHCP server in the modem/router is behaving as you describe, it sounds as if it's faulty, ask your ISP for a replacement.
I'm guessing x.x.0.13 is actually 192.168.0.13. No need to keep it a secret.
I thought M$ Windows allocates ip addresses of 169.x.x.x if there's no dhcp detected.

Why not turn off DHCP in your router/modem & turn on DHCP in your Belkin router instead?

---

