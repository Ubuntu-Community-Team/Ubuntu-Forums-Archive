---
title: "Can't connect to WPA wireless"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by gantww on 2011-05-27
I've put Kubuntu on my laptop and it works like a champ in just about everything....but....

I can't connect to any wireless network with WPA (haven't tried any wide open or WEP networks, so the issue may not be WPA auth) unless I am standing less than 10 feet away from the router. Given that I'm headed to the parents' house for the weekend and given that the router for their house is in their bedroom, I was wondering if the community could help me diagnose what the issue is. I don't think dad would appreciate me coming into his room at 2:00 in the morning because I need to get on the wifi. Here are some other relevant facts.
1) After connecting to the network, I can walk away to a reasonable distance and work normally. It appears to only be an issue when I am first trying to get access.
2) If I log off and back on, my network access will still be up.
3) When I scan for networks, it only finds the ones whose routers are 10 feet or less away from my computer.
4) This did work on Windows when it was installed on the machine, so it seems to be a software problem instead of a hardware one.

Anybody wanna take a crack at what the issue could be? I've come up with the following candidates. How do I prove or disprove these? Or is there something more obvious that I'm missing?
1) Maybe it can only find certain channels when it is close enough to have high signal strength.
2) Maybe there is a power saving setting on the card that is keeping it from pushing out a strong enough signal for the router to talk back (although I've tried on several different brands).
3) Maybe there is a setting somewhere that tells the card a minimal signal strength to require before attempting to connect to a network.

Any thoughts?

---

### Post by mishathegoat on 2011-05-31
This is gonna sound like a weird question but have you tried connecting *while your laptop is charging?* I've had horrible WiFi issues when using Ubuntu on my Macbook Pro. When disconnected from a power source Ubuntu went into a sort of "power saving" mode and the performance of my wireless card dropped **drastically.**

You could also try fiddling with wicd-gtk as an alternative to networkmanager. You may get some better performance.

Try:

```
sudo apt-get install wicd-gtk

sudo killall nm-applet

sudo wicd-gtk
```

---

