---
title: "Wireless nm-applet"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-03-01
Okay, this is seriously starting to annoy me,

For whatever reason, nm-applet will not show up in the notification area unlesss I'm already connected to a wireless network.

I can see 10 wireless networks around me, but the little bars in the notification area wouldn't show up until I manually configured a wireless network to connect to.

Why is this?  Shouldn't it just show up and then let me pick one of the networks?  Any way to fix this? 

It's done this to me on two different laptops for the last kajillion distro upgrades and nothing ever changes.  Be nice if instead of making ubuntu prettier they would fix some the stuff that really mattters.

---

### Post by Xiong Chiamiov on 2009-03-01
Is nm-applet running?
```

ps aux | grep nm-applet

```
You should see two lines (one will be the grep).

---

### Post by thtrgremlin on 2009-03-01
If it is not setup to load by default, you can add it to startup programs by going to System -> Preferences -> Sessions. You can also check there to see if it is already in there, but I am going to assume that it is not.

---

### Post by CryptiniteDemon on 2009-03-04
it's already in the session manager.

The point I'm making is that if nm-applet doesn't detect a network that I've set up manually, the thing never shows up in the notification area.

If it does detect one of them, then it shows up and I can pick from any of the other networks in the area.

---

### Post by CryptiniteDemon on 2009-03-28
I'm still having this problem, any ideas?

---

