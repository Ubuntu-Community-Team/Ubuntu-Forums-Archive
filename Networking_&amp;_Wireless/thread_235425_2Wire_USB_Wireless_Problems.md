---
title: "2Wire USB Wireless Problems"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by Cantwakeup89 on 2006-08-13
Hello, let is be known I am a total linux noob, saying it now so anyone calling me that in a reply looks redundant and stupid *grin* I've looked around all over these forums and used the search utility however I cannot find any help, whether it's there or not. I would love to use Ubuntu (I've installed on a partition of my HD) but one vital part of my computer stops working in Ubuntu, wireless internet :mad: Kinda a dealbreaker, and really unfortunate considering it's kinda the last roadblock from me switching over fully. 

I use a 2wire usb wireless adapter to connect to a 2wire modem, I've used Ubuntu on the computer hooked up to the actual modem, and it works great so I know it's my adapter.I couldn't find an actual model number or anything for it, however it's the adapter listed at the very bottom of the page at [http://www.2wire.com/?p=331](http://www.2wire.com/?p=331) . Any help would be greatly appreciated, and remember to explain everything fully, the console scares the sh*t out of me at the moment, LoL. THANKS!

---

### Post by stormblue on 2006-08-13
Can you open up the Command Line and type:

```
ifconfig
```

and then paste it back in here.


more than likely you're going to need to follow [this]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

---

### Post by cawill on 2006-08-13
I am new to Linux and have Ubuntu installed with the same problem. i have downloaded Ndiswrapper and need to find the correct driver to use. When i type lspci in the terminal it doesn't show my wireless adapter. Can anyone help please?

---

### Post by Cantwakeup89 on 2006-08-16
I apologize, I've been out of town since posting, and I'm on my home now, as soon as I get a chance I will do that for you and post the results, more than likely tomorrow. TY for the responce!

---

### Post by defconoii on 2008-02-25
Here is the 2wire usb howto:
[http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html](http://www.ubuntu-unleashed.com/2008/02/howto-setup-2wire-80211g-wireless-usb.html)

---

