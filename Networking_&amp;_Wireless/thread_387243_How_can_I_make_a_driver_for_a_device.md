---
title: "How can I make a driver for a device?"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by snowboard975 on 2007-03-18
Hi,
I bought a Wibro card that is a kind of 3G device sold in South Korea. 
It is a pcmcia card, has a model number called SPH-H1100, and manufactured by Samsung.
But the problem is that there is no Wibro driver for linux.

And I think I am almost the first person who started using this device in linux because the Wibro service has started quite recently.

I want to make its device driver for linux but don't know how.
Would you advice me any document that might help me?

---

### Post by teaker1s on 2007-03-18
Not an answer, just my thoughts:) 

Firstly you would need to either get data specs from manufacturer (not likely to happen) or you could load into windows and go about debuging/output and reverse engineering a driver.
I know the Ndiswrapper project works with wireless b/g windows drivers.
Possibly it may (slim chance) work with your card, or possibly the ndiswrapper project could advise you further.

hope that helps
Daniel

---

### Post by snowboard975 on 2007-03-19
Thanks a million, I think ndiswrapper can solve my problem. I'll try it and post its result here later.

---

