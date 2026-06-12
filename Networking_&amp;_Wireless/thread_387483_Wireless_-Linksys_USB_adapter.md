---
title: "Wireless -Linksys USB adapter"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by W@LT on 2007-03-18
Hi

I have just loaded Ubuntu onto a second PC which is on a Wirelless Network

The PC uses a Linksys USB Network Adapter - WUSB11

When booting into Ubuntu the set up does not recognise the adapter!!

Has anybody any idea how I get a driver for this?

Thanks

W@LT

---

### Post by gradedcheese on 2007-03-18
what "version" (ex: 2.6) does it say on this Linksys dongle?  It seems that the version number [has a lot to do with]("http://www.google.com/search?hl=en&q=WUSB11+linux&btnG=Google+Search") what you'll have to install to get support for this thing because Linksys changed chipsets at least once or twice without changing the model name.

Hint: in a terminal, run:

```

sudo lsusb -v

```

...to see if the chipset used in this thing shows up.  Otherwise, just look at the device's casing and find a label with a version number.

---

### Post by W@LT on 2007-03-19
OK... Ubuntu is now recognizing the adapter and it shows a list of wireless networks within range..

I have selected my one and it asks me for the Pass phrase or key

I enter this but it still will not connect

I am getting desperate now!!! :confused: 

W@LT

---

### Post by gradedcheese on 2007-03-19
Did you select the right type of the key? (ie: 64 or 128 bit, etc)

---

### Post by W@LT on 2007-03-20
I have tried every permutation...

The wireless router has WEP enabled and normally when I connect to any other of the many PC's I have here I just enter the Key (5F52616B26) and they connect..

Maybe there is something else I need to enable...

---

### Post by Vegetarianrage on 2007-03-20
I'm having the same problem that you started with. How did you go from "ubuntu doesn't recognize it" to having a list of available networks? I am fiddling with ndiswrapper with little luck. I have edgy and an amd64.

---

### Post by W@LT on 2007-03-22
To be honest I upgraded my Ubuntu to Kubuntu.... for some reason the wireless adapter started to be recognized!!

I used the Wireless Manager option in KUBUNTU & I was able to enter the WEP Key and all works fine...

Thanks for all your help

W@LT

---

