---
title: "Latest sl-modem-daemon dependencies error??"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by awaldram on 2005-04-18
Hi,

I'm quite an experienced Linux User just come over from Debian

Have been using the preview releases without problems but now have the following  problem.

I am using the following package from a preview release.
sl-modem-daemon2.99ubuntu2
dependancy sl-modem-modules-new | sl-modem-source  :smile: 

I installed the Source to complete this depndancy (even though i don't need it)
but recently tried to update to the hoary release ubuntu4  :mad: 

it fails as the dependancy for this version is sl-modem-modules-new  and only this package that doesn't exist.  :-? 
I am using the alsa modem driver and therfore require nothing above kernel 2.6 for it to work.

I use the alsa driver as this alows sound from the sound card though you will not get dialing tones. :grin: 

Would it be possible for the dependancies to be corrected to reflect the true dependancies of this package i.e

kernel-image >= 2.6 | sl-modem-source

plus any packages for the sl- modules you choose to package. 

Sorry about all the smilies it's late and i'm playing :roll:

---

### Post by awaldram on 2005-04-22
Bump

anybody there???

---

### Post by az on 2005-04-22
Yes, that is a problem.  It should be fixed for Breezy, eh?

I had been asking the mailing list to include the daemon and modules packages in the ship seed.  That would mean that you would not need to download anything from another operating system just to get your modem driver working.  The dependancies for the two packages were even more screwed up before Hoary.

You should take this up with Ubuntu-motu (masters of the universe) (Crimson) so that the dependancies for the sl-modem-daemon are corrected.

Either through irc or email.  They are very nice.

---

