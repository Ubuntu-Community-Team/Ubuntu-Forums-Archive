---
title: "SiS Driver - amd64 architecture"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by jackmackenzie on 2009-04-08
Hi everybody

I've acquired a new laptop upon which I have been inflicting my low-level knowledge of Ubuntu with some success, however the one thing I can't seem to get an answer for is how to sort out the driver for my graphics card. Brilliantly enough, it's the least supported one - the

 SIS MIRAGE 3+

I have Ubuntu Intrepid installed in the amd64 (i86_64) form, there are solutions for Hardy amd64, and Intrepid i386, but I can't find anything for SiS, on Intrepid, amd64 architecture.

Any help would be massively appreciated! I've looked around at 'binaries' and 'source code' and stuff like that but tried everything that didn't look too daunting and now I'm just a bit confused.

Thank you all!

---

### Post by Hospadar on 2009-04-08
Word on the street ([this street]("https://help.ubuntu.com/community/Video")) is that the binary drivers from the manufacturer are outdated and not to be used.

Does video not work at all out of the box for you? or are you just trying to get some 3d acceleration?  if the latter, then you might just be SoL

Edit:
[this]("http://www.winischhofer.eu/linuxsisvga.shtml") is the website of the guy who develops the SIS driver for linux, you might find some helpful info there.  Also just in general, if you need to know more about xorg.conf and whatnot, check the community docs in my sig, they have quite a wealth of information

---

### Post by jackmackenzie on 2009-04-08
Video works, I can see what I'm doing if that's what you mean, but the resolution is set to a maximum of 800x600 which is completely impractical. And also, yes I am after some 3d acceleration and it seems like on i386 people were having some luck there, but no joy on amd64 that I could find. Any ideas?

EDIT: Didn't see your edit. I'll check it out.

---

