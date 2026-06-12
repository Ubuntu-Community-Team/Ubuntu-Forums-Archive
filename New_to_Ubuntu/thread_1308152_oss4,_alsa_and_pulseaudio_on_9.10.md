---
title: "oss4, alsa and pulseaudio on 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by nisaky on 2009-10-31
I have a problem. Or should i say problems, all connected with sound.

I made fresh install of 9.10 (no upgrade, i formated partition with 9.04) and all was good. Then i set things up and all was good. Until i tried to play two sounds at once (urban terror with mumble). Mumble had sound, urban terror didn't. So i tried to install oss4, as my brother has it on 9.04 and all works fine. I installed it, and got failing results. First i downloaded .deb packet from their site, but it gave me errors. Then i decided to compile it myself and it worked. At first i had no sound. Then, after setting up ossxmix i got sound in exaile, vlc, mplayer and mumble. More sounds at once too. Tried urban terror, it still doesn't work. 

Urban terror console says it uses alsa, and it was successful loading. Yet, i don't get any sound in it. I tried to install all things connected with alsa, still no sound. Not even when Urban terror is only running application. I tried to set sounds in gstreamer (gstreamer-properties) on alsa, pulseaudio and on oss. How can i fix that?



Another problem is strictly connected to oss4. When i first set up ossxmix i got noise in background. And i realized its up to microphone. When i make it quiet, i don't get noise, but i can't record sound anymore. How can i make noise disappear and still be able to talk? 

Sorry for long text, but that's how it is. Thanks for help!

My ossxmix in attachment.

---

### Post by nisaky on 2009-10-31
Nevermind, i did it. Problem was that Urban terror uses SDL, and i had SDL-alsa instead of sdl-oss. :) Finally, 4 hours of trying instead of 3 clicks...

---

### Post by whistlerspa on 2009-11-28
> **nisaky said:**
> Nevermind, i did it. Problem was that Urban terror uses SDL, and i had SDL-alsa instead of sdl-oss. :) Finally, 4 hours of trying instead of 3 clicks...


Thanks solved it for me too:p

But now no sound in Open Arena

---

