---
title: "How do I get and install 64bit flash player"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by bwallum on 2010-08-05
Had this nailed once with 10.0.x then Adobe Labs said 'watch this space' and I'm still watching.

What's the current best solution to run a flash player in 64 bit Lucid?

---

### Post by sylvainrb on 2010-08-05
```
sudo aptitude install ubuntu-restricted-extras
```

did the trick for me...

---

### Post by QIII on 2010-08-05
You don't.

Adobe support for the 64 bit native Linux Flash player has been pulled due to severe security flaws that were present in both the 32 bit and 64 bit versions.  The 32 bit version has been fixed.  The 64 bit version has not.  Although you can still find it here and there, I would not recommend using it.

The post above will help you install the 32 bit version with a 64 bit wrapper.

---

### Post by bwallum on 2010-08-07
Now up to speed with Adobe not doing 64bit and the beta they offered through AdobeLabs has been taken down due to security issues. Thanks for the steers.

I have now done a complete fresh install of 64bit Lucid and can get flash to work in BBC News video clips, no hassle, no setup, came with the install. I presume this is a 32bit flash player with a wrapper to run in 64bit.

....But.

I can't run BBC iPlayer. It just hangs when I try to watch a video stream of a past programme.

The pc is a Dell Inspiron 530 with integrated graphics and "82G33/G31" Intel chipset. the driver reported by lshw is "i915". The graphics are fine and graphics intensive applications such as Stellarium run brilliantly. i can even wobble my windows.

Any idea why I can't get iPlayer to run?

---

### Post by sylvainrb on 2010-08-07
I couldn't test the videos on BBC iPlayer since it is apparently restricted to the UK but the radio iPlayer worked fine (if there's any flash in it). Have you tried it?

I can't really help technically but all I can say is that sometimes I have ran into issues with flash videos on certain websites...

---

### Post by cascade9 on 2010-08-07
I cant be sure, as I dont like in the UK and I'm not going to try with proxies, etc, but it looks like iPlayer needs more than just flash- 

> BBC iPlayer Desktop is powered by Adobe Air (Adobe Integrated Runtime). When you install BBC iPlayer Desktop you also install the Adobe Air components. Air may already be installed on your computer as it is being used by many other applications. Find out more about Adobe Air [here]("http://www.adobe.com/products/air/").

Also, if you have a 64-bit Linux distribution, you should see [Adobe's advice ]("http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084")on what you may have to do[http://iplayerhelp.external.bbc.co.uk/help/download_programmes/desktop_linux](http://iplayerhelp.external.bbc.co.uk/help/download_programmes/desktop_linux)

---

### Post by corrytonapple on 2010-08-07
Try this:[ Flash Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") I use this myself.

---

