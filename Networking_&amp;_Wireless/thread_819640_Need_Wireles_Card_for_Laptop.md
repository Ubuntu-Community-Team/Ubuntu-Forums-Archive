---
title: "Need Wireles Card for Laptop"
date: 2008-06-05
forum: Networking &amp; Wireless
---

### Post by Sugi on 2008-06-05
Can someone provide list of working wireless cards for laptops?  
I need something for a end user (something that will work out of the box).


Thank you,
Sugi

---

### Post by petzworld999 on 2008-06-05
My Linksys WUSB54GC works natively with the rt73usb driver.

---

### Post by Sugi on 2008-06-05
did it work out of the box?  or did you just need to install those drivers first???  are you on hardy?

---

### Post by petzworld999 on 2008-06-05
All I had to do was add "rt73usb" to my /etc/modules file. I am using Hardy. However, I was able to get it working in Gutsy with ndiswrapper, though it may not have been necessary.

```

sudo gedit /etc/modules

```

Just add "rt73usb" at the end and reboot.

---

### Post by Sugi on 2008-06-05
Any one else have wireless cards working out of the box?

---

### Post by mark2741 on 2008-06-05
The Netgear WG511T works without in Hardy perfectly. Just slide the pcmcia card in and then enable the restricted driver for it and reboot and it works. I went through 3 different wireless cards for my wife's laptop and none worked. I finally found some threads here that said the WG511T worked out of the box, so I took a chance and it works great.

Note - you have to get the WG511T (the T is important). Do a search on the forums for it and you'll see.

---

### Post by Sugi on 2008-06-05
I have the WG311 ( i think it's full model is WG311NA, but I could be wrong )  I can't get that silly card to work.   Thanks for the tip.

---

