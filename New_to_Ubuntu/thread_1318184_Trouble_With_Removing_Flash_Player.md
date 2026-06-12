---
title: "Trouble With Removing Flash Player"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Xorg.conF on 2009-11-07
I had a fresh install of 9.10-64 and the first thing I do is what I always do with a fresh install and that is to install ubuntu restricted extras from add/remove.  Anyway, I want to completely remove any trace of the old flash player it put into firefox so I can install the flash player 10 64 bit from adobe.

I've tried:  

sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree

But none of these are installed?

I'm relatively new to linux even though I've been using it for a while, so I'm not sure what to do.  I know there are multiple directories with files associated with the libflashplayer.so that need to be removed. 

Thanks for any help that's given.

---

### Post by 101011010010 on 2009-11-07
Hello there.
Have you tried opening Synaptic and typing in "flash" ? 
This should show you anything that's left, you can also uninstall them with Synaptic. The Adobe Flash Player plugin installer should be removed as well.
I hope this helps.

---

### Post by Xorg.conF on 2009-11-07
Yeah thanks that seemed to have done the trick.  Restricted Extras actually installed Flash Player 10 but for 32bit systems...No wonder I wasn't able to remove it with commands, it was a new package I never tried to remove before.  

Thanks for the help!

---

