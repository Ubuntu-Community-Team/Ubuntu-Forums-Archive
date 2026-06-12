---
title: "How to install Additional Driver when the background is all black?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by beew on 2011-08-03
I was testing Ubuntu on someone's old machine and came across a strange problem. She has a laptop with a Nvidia 6500 card.  I tested it with a Ubuntu installation in a usb drive (a full install as oppose to a live usb with persistence so I can install graphic driver and update kernels if needed) 

I booted into Ubuntu 11.04 with no problem, even Unity works (the nouveau 3d driver has been activated) as I was greeted by the Unity dock and the cube was working (I activated it earlier), the only problem was  the colour was all wrong (so the wall paper was black instead of purple and the skype icon was orange instead of blue) I figured I needed to install the proprietary graph driver, so I started Additional Drivers and let it do its work.  

But the dialogue boxes from Additional drivers are all black so I couldn't read anything on it. In the end I kind of cheated by booting instead into a Xubuntu usb and fired up jockey, there the colour was still wrong but somehow the Additional Drivers box was readable and I could find out which nvidia package was needed, so I booted back into Ubuntu and installed the driver from Synaptic.

It worked in the end but it was kind of cheating. Is there a better way to do that if that happens in the future.

---

