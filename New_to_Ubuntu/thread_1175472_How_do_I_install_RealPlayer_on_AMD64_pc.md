---
title: "How do I install RealPlayer on AMD64 pc?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by bwallum on 2009-06-01
Hi

I would like to play audio from BBC iPlayer. It says that I need RealPlayer. How do I do that please?

---

### Post by drs305 on 2009-06-01
RealPlayer10 is available in the Medibuntu repository. To add Medibuntu and the key to your sources.list, if you don't have it already:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

Here is the supporting page:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by bwallum on 2009-06-03
Thanks for the steer, but having loaded medibuntu I can't find realplayer in the repos. I have tried the helix player and mozilla plugin but still no joy. Anything else I should be doing? I'm running AMD64 bit Jaunty.

---

### Post by drs305 on 2009-06-03
I have the following entry in /etc/apt/sources.list.d/medibuntu.list and my Synaptic offerings include realplayer 11. The repository is listed under the "Third-Party" tab in Synaptic or Software Sources if you have added it:
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free # Medibuntu - Ubuntu 9.04 "jaunty jackalope"


If that doesn't work, I retrieved this link directly from the Medibuntu site. It says it is for the 64-bit realplayer 11 .deb, even though the page still reflects version 10. 

[http://packages.medibuntu.org/jaunty/realplayer.html]("http://packages.medibuntu.org/jaunty/realplayer.html")

---

### Post by bwallum on 2009-06-03
WEIRD...I downloaded 11.0.0.2 as advised and tried to install it. Still no luck. Then I looked at the repositories again and there was RealPlayer 10. I installed it and can now run RealPlayer!

Thanks for all your help! Wouldn't it be good if government's ran as effectively as Ubuntu forums! We might even last for another century that way!

---

