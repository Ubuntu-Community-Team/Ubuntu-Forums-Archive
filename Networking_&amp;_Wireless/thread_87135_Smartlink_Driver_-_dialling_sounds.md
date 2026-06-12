---
title: "Smartlink Driver - dialling sounds?"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by abovett on 2005-11-07
Hi

I just installed the smartlink modem driver on my laptop under Breezy using module-assist (seemed a **lot** easier than some of the methods I've seem on the Wiki!). It works, but I don't get any dialling sounds from the speakers, which I like as I sometimes use the laptop to debug other people's dial-up connections.

Does anyone know if it's possible to get the sound output to the speakers, and if so how?


By the way, for those interested, the steps I used to install the driver were:
```

# apt-get install sl-modem-daemon sl-modem-source
# apt-get install gcc-3.4
# module-assistant
```
Then follow through the steps PREPARE, UPDATE, etc. on the module-assistant "gui".

(I tried first time with gcc-4.0 and it failed - said it wanted gcc-3.4. Installed that as above and it worked).

Cheers

Andy B

---

### Post by az on 2005-11-07
Yes, module assistant rocks.  I think it was a little broken in Hoary, it was debian-specific.

The sound issue you describe with the sl-modem drivers is a known issue.  I think the only hope is to wait for the alsa intel modem driver to be more mature.  The newer versions of the proprietairy sl-modem drivers are licenced in a way that they cannot be redistributed.

Maybe you can go to the smartlink site and get the newer drivers there?  They may solve your problem.

---

### Post by abovett on 2005-11-07
Thanks for the quick answer.

The sound is a "nice-to-have" rather than a "must-have", and as the install went so nice and smooth with module-assist and the packaged drivers, I think I'll avoid going outside the apt repositories for now, thanks.

I _think_ I used drivers downloaded from smartlink last time I did this (under hoary) but it's a while back now and I can't really remember! (Must keep more notes on how i get things working).

I'm interested in what you say about the alsa Intel driver - I didn't realise that that might be an option. I take it from what you are saying that it isn't ready yet? If/when it is, how would I go about using it? Is it just a case of installing a different module using modprobe?

Thanks

Andy B

---

