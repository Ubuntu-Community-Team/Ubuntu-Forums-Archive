---
title: "Sound card does not recognize headphones"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by lwalper on 2011-07-31
When I was running OS 10.04 I could plug my headphones into the jack and the internal speaker would be bypassed and sound would be played through the headphones as one would expect to happen.

Now, with 11.04 that is not happening. Now I need to plug the headphones in to the jack and restart the system before sound comes through the headphones. Is there a setting that needs to be modified to allow hot plugin of the headphones? I had always thought that was just a mechanical connection that bypassed the internal speakers when the headphones were plugged in -- guess not??

---

### Post by dalee on 2011-07-31
Hi,

This happens intermittently to me. But sometimes pulse stops altogether for me too. I'm not a big fan of pulse audio.

To test if it's a hardware problem or software, you can left click on the speaker icon and then select sound preferences. Select the output tab. At the bottom you can select connector drop down menu and set it to analog headphones. This should shut off the external speakers and feed the sound to the headphones.

dalee

---

### Post by Untold on 2011-07-31
Try running alsamixer and make sure the headphones are turned up all the way. Sometimes when I leave my headphones in, the externals seem to stop working.  I just open alsamixer and turn them up. Hope this helps.:D

---

