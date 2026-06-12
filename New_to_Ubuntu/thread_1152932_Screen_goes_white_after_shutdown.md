---
title: "Screen goes white after shutdown"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by argie on 2009-05-08
I have a Dell XPS M1330 with an Nvidia 8400M GS and have the proprietary drivers installed using the Restricted Drivers Manager. This is a fresh install of Ubuntu 9.04 64-bit.

Sometimes when I shutdown, the whole shutdown process completes (the splash screen progress bar goes to nothing) and then the screen goes black. Immediately after it goes black it flashes and comes back white. The laptop still draws power in this state, and I can hear the fans still whir if I lean in. If I let it stay in this state, eventually some streaks develop on the white screen, and after a while it sort of forms a little fuzzy rectangle in the center that's differently coloured (a bit greyish).

I know that the screen is alright and that the graphics card is alright because this only happens when shutting down Ubuntu and not when playing games in Vista or Ubuntu or when browsing on either operating system.

Does anyone know what the problem is?

---

### Post by argie on 2009-05-08
Alright, I noticed that this blank white screen would show up every time I shut down, but would sometimes disappear. However, it would never appear when shutting down from recovery mode. Apparently, usplash is the problem. I removed 'splash' from my /boot/grub/menu.lst entry and the problem has apparently gone away. I can shut down in peace. However, I no longer have any splash screen.

---

### Post by pveurshout on 2009-08-30
Hey,

I've been experiencing the exact same problem. After spending a full afternoon searching for a solution (without results) I decided it couldn't be anything but a bug in the nVidia drivers so they'll hopefully solve it sometime in the future. For now, removing splash from menu.lst did the trick, although once in a while the system still hangs at shut down (but with a black screen instead, so it shouldn't damage anything). Anyway, thanks! :)

---

