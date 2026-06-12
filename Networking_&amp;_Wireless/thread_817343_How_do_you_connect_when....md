---
title: "How do you connect when..."
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Affrikka on 2008-06-03
Okay so all of our computers run on a wireless network. When you run a wireless network you have 1 of 2 symbols on the bottom of your desktop (where the applications, places, systems, etc. are)
1. You have two monitors connected together and an X (which means your not connected)
or
2. Your signal strength bars.

I restarted my sisters computer one day and neither of the two symbols where there. I can't connect to the network the way I know how because the two monitors that you click on to connect aren't there, and the signal strength bars aren't there.

Is there something I can type in the console, or a switch I can switch somewhere to connect again? It's of real great importance I get the internet back on her computer, I was in the middle of something and I need the internet to finish it.

Thanks,


-Mathieu

---

### Post by TRApReGeTr on 2008-06-03
First you should try:

Bring your ethernet device down:
```
# ifconfig wlan0 down
```

Bring your ethernet device down:
```
# ifconfig wlan0 up
```

Bring your ethernet devices status:
```
# ifconfig -a
```


Replacing **wlan0** with whatever you've configured your card as. If you've already tried this maybe someone else can advise. Hope that works and good luck.

---

