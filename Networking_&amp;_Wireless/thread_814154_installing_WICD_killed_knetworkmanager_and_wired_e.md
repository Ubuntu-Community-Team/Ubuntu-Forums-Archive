---
title: "installing WICD killed knetworkmanager and wired ethernet"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by ihatethetv on 2008-05-31
Hope this isn't too much of a repost, I quickly tried looking but couldn't find anything.

I installed wicd and it removed knetworkmanager.  Now my eth3 (the wired ethernet card, an nvidia which was working with knm before) is disabled.  It doesn't show up in ifconfig.  

When I go to the kubuntu Networks Settings, it shows that interface disabled.  Enabling it via the button causes it to go green for a split second then become disabled again.  

I suspected wicd was running and disabling it, so I removed that....but that didn't do anything.  

Now I'm offline on that machine.  Can someone point me to a more forceful way of enabling eth3?

Thanks,
Glen

---

### Post by Ayuthia on 2008-05-31
> **ihatethetv said:**
> Hope this isn't too much of a repost, I quickly tried looking but couldn't find anything.

I installed wicd and it removed knetworkmanager.  Now my eth3 (the wired ethernet card, an nvidia which was working with knm before) is disabled.  It doesn't show up in ifconfig.  

When I go to the kubuntu Networks Settings, it shows that interface disabled.  Enabling it via the button causes it to go green for a split second then become disabled again.  

I suspected wicd was running and disabling it, so I removed that....but that didn't do anything.  

Now I'm offline on that machine.  Can someone point me to a more forceful way of enabling eth3?

Thanks,
Glen

Have you tried doing the following:
```
sudo /etc/init.d/wicd stop
sudo ifconfig eth3 up
```

---

### Post by imdano on 2008-05-31
Running ```
sudo ifconfig eth3 up
```should work.  Wicd isn't actually disabling it though, it just didn't enable it, which KNetworkManager did when it was installed.  Right now wicd defaults to eth0 as the wired interface (I'm working on making this behavior better), so going into preferences and changing it to eth3 would probably make everything work normally.

---

