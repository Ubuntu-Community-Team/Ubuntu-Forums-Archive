---
title: "Sound has suddenly stopped working"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by danmpem on 2009-01-11
I'm running a Dell Dimension 4600 Pent 4, 2.4 GHz, 1GB RAM with Ubuntu 8.10.  I was having some trouble with my Adobe Flash Player after installing several other video players.  After I uninstalled Gnash my flash worked again, but now my sound doesn't work at all.  I reinstalled my sound modules and made sure I had all the ALSA packages from Synaptic.  I've gone through the Ubuntu Sound Troubleshooting and I think I did it all correctly but now I don't have anything.  What else can I be doing?

Thanks!

---

### Post by danmpem on 2009-01-11
Oh, yeah, and not a newb but I'm not experienced enough to be anything else, so please bear with me.

---

### Post by femfatel on 2009-01-11
Are your speakers on? And are they plugged in(might have kicked a wire with your foot like have in the past)

---

### Post by danmpem on 2009-01-11
Yeah, I checked that already.  The wires are good.  It's definitely a software/driver problem that was created from all the massive installing/uninstalling I was doing with the movie players trying to troubleshoot my flash player.

---

### Post by danmpem on 2009-01-16
Now it's just getting weird.  I put a fresh installation of Ubuntu in, but it's still not working.  Ubuntu recognizes the sound card, but nothing is coming out through speakers or headphones when running the sound tests.  I put the card in another computer and it works fine.  I don't think the problem is with my PCI ports because I have an ethernet card in one of them and it's working fine.  If anyone has any suggestions, they would be much appreciated.

Thanks!

---

### Post by fenian on 2009-01-16
In the sound prefrences have you tried switching from autodetect to alsa?

---

### Post by danmpem on 2009-01-16
> **fenian said:**
> In the sound prefrences have you tried switching from autodetect to alsa?

Yeah I did.  Didn't get anything from changing the sound devices.

---

### Post by talsemgeest on 2009-01-16
> **danmpem said:**
> Yeah I did.  Didn't get anything from changing the sound devices.
With all the sound devices you have tried, have you gone to the volume mixers to make sure that the volume is on full? Even though it might look like it is on full from the volume control applet, it can still be off. I was going to suggest installing "ubuntu-desktop" to make sure you haven't removed anything you need, but if it still happens on a live cd I doubt it would fix your problem.

---

### Post by danmpem on 2009-01-17
> **talsemgeest said:**
> With all the sound devices you have tried, have you gone to the volume mixers to make sure that the volume is on full? Even though it might look like it is on full from the volume control applet, it can still be off. I was going to suggest installing "ubuntu-desktop" to make sure you haven't removed anything you need, but if it still happens on a live cd I doubt it would fix your problem.

Hmmm, I already checked the volume mixers (that one sent me on a wild goose chase a couple of years back and I've never missed it since), but I'm definitely going to try the live cd.  Thanks.

---

### Post by talsemgeest on 2009-01-17
> **danmpem said:**
> Hmmm, I already checked the volume mixers (that one sent me on a wild goose chase a couple of years back and I've never missed it since), but I'm definitely going to try the live cd.  Thanks.
Ok, good luck! ;)

---

### Post by AmandaKerik on 2009-01-18
> **danmpem said:**
> Now it's just getting weird.  I put a fresh installation of Ubuntu in, but it's still not working.  Ubuntu recognizes the sound card, but nothing is coming out through speakers or headphones when running the sound tests.  I put the card in another computer and it works fine.  I don't think the problem is with my PCI ports because I have an ethernet card in one of them and it's working fine.  If anyone has any suggestions, they would be much appreciated.

Thanks!

This sounds exactly like what happened to me after I torrented the newest version - my computer suddenly forgot that I had a sound card, and even claimed it didn't exist!

What finally got my sound back? Using the older kernel, of all things. I've become a bit suspicious of the torrent I got, so I'm going to check the checksum of it (makes sure it hasn't been tampered with).

I hope your solution comes soon!

---

### Post by talsemgeest on 2009-01-18
> **AmandaKerik said:**
> This sounds exactly like what happened to me after I torrented the newest version - my computer suddenly forgot that I had a sound card, and even claimed it didn't exist!

What finally got my sound back? Using the older kernel, of all things. I've become a bit suspicious of the torrent I got, so I'm going to check the checksum of it (makes sure it hasn't been tampered with).

I hope your solution comes soon!
Torrents can not be tampered with, otherwise it piece is discarded as corrupted. Torrents come with checksums so that they come in with even better accuracy than http downloads.

---

