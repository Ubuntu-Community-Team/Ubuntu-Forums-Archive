---
title: "mtink - how do you add a printer?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by PaulWhipp on 2009-05-06
I've been using ubuntu for almost a year now and its been a few months since I've had to turn on a windows PC.

Today my CX4700 printer stopped printing and, knowing that it was out of ink, I looked to see how I could find out which ink cartridge needed replacing.

I found the utility mtink easily enough with google but it does not support the epson CX4700 so I had to use my old Windows install to check the ink cartridge levels.

Does anyone know how to add a printer to mtink?

---

### Post by Didius Falco on 2009-05-06
**mtink** has been out of development for a while now. Did you install it (it's available in the repositories in Synaptic, BTW - I'd always recommend using them whenever possible) and try it out? It may workwith it, just that printer wouldn't be listed because it came out after development stopped.

I know that lots of people with Epson printers are still using it now...

Here is a link to a thread I was in recently that should simply matters for you. We certainly had to wrestle it to the ground and beat it with sticks until an actual user of it turned up. Please note that I don't think I'm quite as useless as this thread may make me appear to be. :)

[http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink](http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink)


If it doesn't work, you could have a look at **escputil**, which is also in Synaptic.

Good luck...

Regards,

Didius

---

### Post by PaulWhipp on 2009-05-07
Thanks Didius, I did install it from synaptic. Treating the CX4700 as a CX3200 seems to work OK. 

Using escputil works too but I had to use mtink to find the printer port as the raw device - definitely not user friendly.

Do you know how I can get the raw device for a named (or the default printer)?

---

