---
title: "wireless card problem"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by kmurry on 2008-06-01
I have a treadnet tew-621pc, and I can't find drivers for it to work on my laptop. Please Help!!!!!

---

### Post by gradedcheese on 2008-06-02
It would help to have an idea of what chipset is inside that card.  Please run this in a Terminal:

```

lspci | grep -i network

```

and post the output.

---

### Post by kmurry on 2008-06-02
OK, I ran it and here is what it says:


07.00.0  Network controller: Ralink Unknown device 0601


I hope this helps. I'm new at this so please be patient with me.

Thank you.

---

### Post by kmurry on 2008-06-03
can anybody help me with this?

---

### Post by gradedcheese on 2008-06-04
What version of Ubuntu are you running?  Looks like you have a Ralink chipset that is unsupported (at least in your version of the kernel).  Ralink support is usally ok, so perhaps a newer driver will solve this.

---

### Post by kmurry on 2008-06-04
> **gradedcheese said:**
> What version of Ubuntu are you running?  Looks like you have a Ralink chipset that is unsupported (at least in your version of the kernel).  Ralink support is usally ok, so perhaps a newer driver will solve this.

I got the newest version of ubuntu. I am also not sure where to get a driver that works, I'm such a newbe.

---

### Post by gradedcheese on 2008-06-05
Ok, I've read a bit more about your chipset:
- the 0601 is a Ralink RT2800 chipset, it's pretty new
- the open source Linux driver for Ralink devices doesn't support this chipset yet
- however ralink provides a vendor driver here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) (the first driver in that list should be the one, I think)

Can you post the output of running the following command?

```
uname -r
```

I can then build the driver for you and upload it here and you can try it out.

---

### Post by kmurry on 2008-06-05
> **gradedcheese said:**
> Ok, I've read a bit more about your chipset:
- the 0601 is a Ralink RT2800 chipset, it's pretty new
- the open source Linux driver for Ralink devices doesn't support this chipset yet
- however ralink provides a vendor driver here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) (the first driver in that list should be the one, I think)

Can you post the output of running the following command?

```
uname -r
```

I can then build the driver for you and upload it here and you can try it out.

  
Thanks for the info.  Here is that output:   2.6.24-17-generic

thanks again, I'll let you know if it works.

---

### Post by kmurry on 2008-06-05
how do you install the drivers?

---

### Post by gradedcheese on 2008-06-05
At this point, I don't think that there's an easily installable package so the idea is to download Ralink's source code (at that link I posted) and compile the driver.  I will do this for you a little later and then show you where to place the compiled file (driver).  At some point, this driver will get integrated into the shipping kernel and it will work out of the box.

If you have Internet access on that Ubuntu PC by other means, I'd go ahead and install updates (the latest kernel at this time is 2.6.24-18 ).

---

### Post by kmurry on 2008-06-06
> **gradedcheese said:**
> At this point, I don't think that there's an easily installable package so the idea is to download Ralink's source code (at that link I posted) and compile the driver.  I will do this for you a little later and then show you where to place the compiled file (driver).  At some point, this driver will get integrated into the shipping kernel and it will work out of the box.

If you have Internet access on that Ubuntu PC by other means, I'd go ahead and install updates (the latest kernel at this time is 2.6.24-18 ).



Where do you find it?

---

### Post by eldiabolosk on 2008-11-23
Did you have any luck with RT2800? I have an SMCWPCI-N2. Same chipset and strugling.

---

### Post by BastardNamban on 2009-05-06
I know I'm resurrecting this thread from the dead, but I wonder if Ralink indeed did release linux drivers for this yet. I'm thinking of picking one of these Trendlink TEW-621PCs on Newegg, and I want to confirm there are linux drivers available first too.
[HTML]http://www.ralinktech.com/ralink/Home/Support/Linux.html[/HTML]
Going there, there's a lot available, it seems. It looks like these guys are well supported in the linux community, and this page:
[HTML]http://www.fsf.org/resources/hw/net/wireless/cards.html[/HTML] seems to confirm that.

So can anyone confirm with the current site if the drivers for this card's chipset are indeed there? Noone ever wrote in the exact chipset it used, just that it was a 2800 series. Is what I would need there?

---

### Post by eldiabolosk on 2009-06-11
I recently installed a 64 bit Ubuntu 9.04 (Jaunty). Worked out of box. Did not need to install anything. Maybe I was lucky but worked.

Ed.

---

