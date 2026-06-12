---
title: "TRENDnet TEW423PI"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by nlavon on 2008-04-23
I am new to the Ubuntu community and have been racing to bone up on the system. Basically, I have an old Windows XP machine in the basement that practically died out due to a host of issues but it still boots and works using a P4 3 Ghz with 1GB memory, so it's worth trying to salvage. I want to put Ubuntu 7.10 on it and I had a question about the network card referenced above.

We have a LinkSys router at home for wireless that works fine with our family Windows XP machine and our laptops. I don't want to spend a fortune on my old machine (I told my wife this is a "hobby") and I saw that Circuit City carries the TRENDnet 54 Mbps Wireless G PCI adapter, TEW423PI, using the RTL 8185L chipset. The list on Ubuntu documentation said this card works using ndiswrapper. But that entry was made in 2005.

Now I went to Realtek and downloaded a Linux driver for kernel 2.6.22. [[http://tinyurl.com/2qvxlx]](http://tinyurl.com/2qvxlx]). 

The card is $25. So the question is, having this driver downloaded and copied, is it safe to get this card and assume it will work under Ubuntu 7.10?

Thanks for any help and I am grateful to be here.:)

Neal Lavon
Takoma Park, Maryland
USA

---

### Post by dstew on 2008-04-23
It looks like most people who get that chipset to work use ndiswrapper and the Windows driver. I couldn't find anyone who was successful with the Realtek driver and Feisty or Gutsy.

Cards with Atheros chipsets work pretty well, I have one.

---

### Post by nlavon on 2008-04-23
Thanks, that was helpful, I've been poring through the stuff on ndiswrapper.

Any hints on cards with the Atheros chipset you would recommend? I see Belkin makes a F5D7000 with such a chipset. They have a fairly cheap card through mail order. What kind do you have?

Again, thanks for the reply.

Neal Lavon
Takoma Park, MD
USA

---

