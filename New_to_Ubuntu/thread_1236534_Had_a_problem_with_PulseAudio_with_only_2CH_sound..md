---
title: "Had a problem with PulseAudio with only 2CH sound."
date: 2009-08-10
forum: New to Ubuntu
---

### Post by xanmalone on 2009-08-10
Basically ever since i first installed Ubuntu 8.10 and later upgraded to 9.04 Jaunty I've had issues with my Realtek 7.1 card only playing sound in 2CH mode / Front. Absolutely no sound from center, rear or the subwoffer.

Now, over time I've tried many tutorials, tools and other miscellaneous things to get my full 5.1 sound back. Nothing worked.

Now I've found a tool paconfig which i hoped would fix my issues. Tried it out, set 5.1CH and edited the /home/user/.pulse/default.pa with a added "channels=6" to the config. 

This did nothing pretty much, even gave a horrible stuttering effect which didn't end unless i pressed stop and play again. This happened only the first time after boot and never again until restarting the system.

Now, tried reverting back all the files that i've modified overtime and redoing the paconfig and readding that line above. So except for paconfig, everything was unmodified by any other tutorials you might find on google.

Still didn't work. So i decided to delete the default.pa file under the home folder to see what would happen.

I'm guessing right now it started using the default.pa file under the /etc/pulse/ directory. 

--

So, basically the first thing that happened was me trying to play a MP3 to see if the Audio was still even working with the rough basic configuration specified in the /etc/pulse directory. 

To my surprise, it works. Center, Front, Rear, Subwoffer. Everything works like a charm now. You can compare it directly to the sound quality with the Realtek HD 7.1 drivers on Windows

I don't have a clue right now if deleting the default.pa file under the home directory would cause any problems in the future. But right now i'm pretty happy with the sound finally working like it should.

My next step is to do a fresh install, and trying to trace what i did wrong. I'm having a hard time believing that deleting a file that i suppose was there since the beggining was forcing only the Front Speakers. 

Might have been the upgrade to 9.04? Who knows. But i'm pretty curious how it's working right now.

--

Sorry for the long post.

---

