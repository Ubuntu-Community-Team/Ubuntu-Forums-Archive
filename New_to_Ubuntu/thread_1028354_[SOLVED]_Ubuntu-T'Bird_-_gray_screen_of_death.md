---
title: "[SOLVED] Ubuntu-T'Bird - gray screen of death"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by Pappy1911 on 2009-01-02
Happy New year friends..
My Thunderbird is freezing quite often with the gray screen.
System log shows;

Jan  2 09:24:32 johnny1911-desktop pulseaudio[6152]: protocol-esound.c: pulsecore/protocol-esound.c: Failed to create sink input.

Closing TB with bottom tab and restarting helps for a while but it stalls later. Sometimes the whole screen is frozen and a hard re-boot is necessary.

Any help would be greatly appreciated. Thank you.

---

### Post by BenAshton24 on 2009-01-02
Well the error you posted is a sound error? so I'm guessing that when you received a message it tried to play a sound... failed... and because if this crashed... If you have set a custom sound for it to play.. try using the default and see if there is still an issue. if not simply disable the "Play sound" check box in Edit --> Preferences --> General  (Quick Fixes FTW XD)

Hope this helps

Ben

---

### Post by chrisod on 2009-01-02
Since it seems to be related to a problem with Pulse Audio, I would suggest turning off all audio notifications in Thunderbird as the easy workaround.

---

### Post by Pappy1911 on 2009-01-02
Thank you. I have disabled the sound and will see if that's the solution.

After all the hair-pulling, I hope the problem is gone...

---

