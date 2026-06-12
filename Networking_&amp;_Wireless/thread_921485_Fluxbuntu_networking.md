---
title: "Fluxbuntu networking"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Duncan79 on 2008-09-16
Hi. This is my first post here but I've been a linux user for a little over a year now. I'm quite confident with NDISwrapper and setting up my wireless network, the problem is, I have taken a liking to fluxbuntu for it's fluxbox WM. The thing is, my standard eth0 connection is not working. It works fine in *Ubuntu, it's just that fluxbuntu won't recognise it. I need eth0 to download NDISwrapper to set up my WiFi. I could grab the deb, but I see no package installer in fluxbuntu.

Any suggestions?

---

### Post by snowpine on 2008-09-16
Hi Duncan, 
Interesting, I set up a couple of systems with Fluxbuntu, and I never had problems with wired internet (though I had the usual problems with wireless, which I solved with ndiswrapper, just as you are. I also installed wicd network manager out of personal preference).

I would recommend copying the ndiswrapper .deb over using CD or USB stick. You can install debs from the command line using:

```
dpkg -i filename.deb
```

---

### Post by Duncan79 on 2008-09-17
Thanks for the help. Is there a seperate .deb for NDISwrapper-common and NDISwrapper-utils? I've only ever retrieved NDIS from synaptic and never installed as a .deb. I found NDIS through a google search as a .deb but there is only the one package. Would all dependencies be included in that package?

---

