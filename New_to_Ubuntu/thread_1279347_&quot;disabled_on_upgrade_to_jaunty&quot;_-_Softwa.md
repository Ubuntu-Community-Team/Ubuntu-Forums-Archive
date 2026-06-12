---
title: "&quot;disabled on upgrade to jaunty&quot; - Software Sources"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-09-30
I've updated to 9.04 (from intrepid) and some of my software sources seem to have been disabled. Could someone tell me why that is and what software sources I need?

I've just run 'Computer Janitor' and there seems to be a heck of a lot of stuff there that I thought should be useful. When I look at the detail for these ones, it tells me that the reason Janitor thinks the package can be removed is because it can't find it supported in one of my software sources.

Here's what I've got in my sources:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner (this is enabled)
[http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock (this was disabled)
[http://ppa.launchpad.net/sargentd/ppa/ubuntu](http://ppa.launchpad.net/sargentd/ppa/ubuntu) jaunty main (this was disabled)
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free (there's a comment saying it was disabled on upgrade to jaunty, but it's ticked as being enabled)
[http://winff.org/ubuntu](http://winff.org/ubuntu) jaunty universe (there's a comment saying it was disabled on upgrade to jaunty, but it's ticked as being enabled)

If anyone has any great ideas on which software sources I should get and/or enable and/or delete, I'd much appreciate hearing from you.

Cheers

---

### Post by Temposs on 2009-09-30
You can enable any or all of those, probably. All but the first one are third party repositories that you've added yourself. If you enable them and none of them cause errors when you refresh, then they should be fine.

---

### Post by dearingj on 2009-09-30
Ubuntu automatically disables third-party repositories on upgrade, since they're not controlled by Canonical and could cause problems during upgrade, and they may not yet support the new version of Ubuntu.

I see that both the cairo-dock.org and ppa.launchpad.net/sargentd repositories support Jaunty, so I'd suggest re-enabling them. You can check repositories yourself by either:

-entering their url into your web browser and attempting to navigate to the dists/jaunty folder - if the jaunty folder exists and is not empty, then Jaunty is supported.

-The best way to check for support is of course just to go to wherever you first found the repository's info (probably the project's main site, e.g. cairo-dock.org) and see what they say there.

---

### Post by Roger Allott on 2009-09-30
> **dearingj said:**
> Ubuntu automatically disables third-party repositories on upgrade, since they're not controlled by Canonical and could cause problems during upgrade, and they may not yet support the new version of Ubuntu.
Ah, that makes sense!

> **dearingj said:**
> I see that both the cairo-dock.org and ppa.launchpad.net/sargentd repositories support Jaunty, so I'd suggest re-enabling them. You can check repositories yourself by either:

-entering their url into your web browser and attempting to navigate to the dists/jaunty folder - if the jaunty folder exists and is not empty, then Jaunty is supported.

-The best way to check for support is of course just to go to wherever you first found the repository's info (probably the project's main site, e.g. cairo-dock.org) and see what they say there.
Thanks for that. I seem to have resolved issues with cairo-dock now, but launchpad is still throwing up an error.

When I click OK on Software Sources, I get the following message:
```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 106A92EF1E5F9737
```

I've visited launchpad.net to see what I should be doing, but there's nothing obvious there to help me. Any ideas?

---

### Post by Roger Allott on 2009-09-30
This thread can now end as I've looked at Synaptic and the only things from that launchpad repository was monkeystudio, which I haven't installed and I can't see me needing it either.

---

### Post by dearingj on 2009-09-30
Glad to see you've got everything working :)

For future reference, by you or anyone else who stumbles upon this with the same error message:
Any time you get an error stating that "signatures couldn't be verified because the public key is not available" regarding a PPA on launchpad.net, just follow the steps on [this]("https://help.launchpad.net/Packaging/PPA/InstallingSoftware") page under "Adding the PPA's key to Ubuntu". The key ID to use is the one specified in the error message.

---

