---
title: "Something totally buggered my firefox"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by The_Proffessor on 2009-05-07
So I was experimenting with the 3D Cube desktop in the Compiz package. With 9.04's new fancy graphics my computer was kinda hiccuping a bit on that thrown in with the cube. So I open up a firefox window and tried to watch a video just to see how things worked. Then...things happened.

A window popped up saying I needed to install my flash plugin, which was odd because I already had it installed, but being a bit of a nub I said ok and just let it roll. In my rush I installed Swfdec SWF player instead of the adobe one I had already. Now anything flash related that comes up is completely messed up and won't play properly (youtube, and such included). All attempts to install the adobe plugin over it have yielded no results. 

Probably should have asked about this on the firefox boards in hindsight...or do you guys have any thoughs?

---

### Post by Didius Falco on 2009-05-07
Welcome!

Have you tried disabling that plugin in Firefox? You can find the pluguns from **Tools/Add-ons/Plugins**, then just disable that plugin and restart Firefox.

You could also go into **Synaptic** and uninstall  **swfdec-mozilla** or do it from a Terminal shell with ```
sudo apt-get remove swfdec-mozilla
```If that doesn't seem to have an effect, log out and back in.

I hope this helps...

Regards,

Didius

---

### Post by The_Proffessor on 2009-05-07
Couldn't figure out how to remove it in synaptec, but the terminal code worked and now all flash stuff plays perfectly. It was probably the two plugins trying to play over one another. 

Thanks so much. <3 you open source dudes

---

### Post by Didius Falco on 2009-05-07
Glad to help!! Mark this thread solved (see my sig for how) and go watch some videos or something. <G>

Regards,

Didius

---

