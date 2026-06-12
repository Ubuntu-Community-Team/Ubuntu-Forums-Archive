---
title: "Upgraded to edgy, can't reach internet  ;("
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by turbojugend_gr on 2006-10-09
Well here's the short story, I installed edgy beta today, but I couldn't reach the web or the repos in no way (static,dchp, both could ping to the eth0 and the router but when asked to ping for e.g. [www.google.com](www.google.com) I keep getting "can't reach network")

Later in the day, I decided to try with todays build of ubuntu, I did things became a little better, now I still can ping my lan and router and when I try [www.google.com](www.google.com) I get nothing, it keeps w8ing for response. In firefox also it keeps w8ing for the sites to respond. Note that this is only with static Ip, dchp behaves as with the beta edgy.

Pleas help me as I am stuck in winxp for the moment, which is unsuable and ugly (snif I miss my beryl....)

---

### Post by mips on 2006-10-09
You should try the Edgy forum seeing it is beta.

---

### Post by turbojugend_gr on 2006-10-09
> **mips said:**
> You should try the Edgy forum seeing it is beta.

Oh I didn't see that, after the facelift of this forums ,i thought it was removed-depreciated as I couldn't find. I did now but it's too late.

Here is what I did for those that might be interested: "sudo gedit /etc/network/interfaces" and there I edited the static IP section by adding "gateway *router's_ip*". I stumbled upon this in lauchpad, I hoe it is usefull to others too.

---

