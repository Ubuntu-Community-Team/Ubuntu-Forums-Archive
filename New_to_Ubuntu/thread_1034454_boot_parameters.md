---
title: "boot parameters?"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by foolman89 on 2009-01-08
So i just finished up installing ubuntu on my computer, but when it came time to finally try it out, my screen went black, with "Input signal out of range" illuminating the screen. I went through the forums and some one directed me to try adding this to the boot parameters "linux vga=771"

Now i have no clue what this does, or what it did. But i now ubuntu loaded up and i am writing this thread from firefox off ubuntu XD. 

I wanted to ask what does that boot parameter do?

---

### Post by mikewhatever on 2009-01-08
Here's the link. [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by scorp123 on 2009-01-08
> **foolman89 said:**
> "linux vga=771" ... Now i have no clue what this does, or what it did. This sets the graphics mode of the framebuffer. For some stupid reasons Ubuntu will sometimes default to a mode that is way too high for certain PC's and/or screens.

Lengthy discussion here:

"HOWTO: Change bootup and console resolution"
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

---

