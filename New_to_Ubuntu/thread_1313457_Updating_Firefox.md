---
title: "Updating Firefox?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Nottawa on 2009-11-03
I see that Firefox has a new version, 3.5 and I am running 3.0.15, which came with my Jaunty.  The update section I have is greyed out for updating the program.  How do I get the latest version and install it? Add/Remove programs doesn't do it.  If I get the latest version direct from Mozilla, how do I install it?  Or is there some reason why Canonical is holding back before making the update easily available

Thanks for the help/info.

---

### Post by snowpine on 2009-11-03
Ubuntu *never* automatically gives you a major update to any application. Most Ubuntu users will get FF 3.5 by updating to Karmic (where it is the default browser).

You can, however, easily install it in Jaunty with the following terminal command:

```
sudo apt-get install firefox-3.5
```

This will install 3.5, codenamed Shiretoko, alongside 3.0. 

There are other methods too, that's just the one I'm most familiar with. Good luck!

---

### Post by alphacrucis2 on 2009-11-03
> **Nottawa said:**
> I see that Firefox has a new version, 3.5 and I am running 3.0.15, which came with my Jaunty.  The update section I have is greyed out for updating the program.  How do I get the latest version and install it? Add/Remove programs doesn't do it.  If I get the latest version direct from Mozilla, how do I install it?  Or is there some reason why Canonical is holding back before making the update easily available

Thanks for the help/info.

I think Firefox 3.5 is in the Jaunty repos if you have a look in Synaptic. It installs FF 3.5 as a separate program it calls Shiretoko and leaves FF 3.015 alone. If you want to actually replace FF 3.0 in Jaunty you could do it this way:

[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")

Otherwise you could upgrade to Karmic but I would hold off on that for a couple of weeks if you are a beginner, as there are a few upgrade problems right now which should get sorted fairly quickly.

---

