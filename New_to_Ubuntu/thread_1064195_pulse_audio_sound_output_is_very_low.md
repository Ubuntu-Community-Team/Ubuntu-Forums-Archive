---
title: "pulse audio sound output is very low"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by nubix on 2009-02-08
i think the title pretty much asked the question, even with the sound bar all the way up i get barely hearable sound from the pulse audio device chooser applet. please help. in previous installations (8.10) doing absolutly nothing different i have managed to screw around fix the problem with shear luck, bit not this time around.
any help would be appreciated!!

---

### Post by drs305 on 2009-02-08
You mention the sound bar (singular). If you have the speaker icon on your panel, double-click and see if you have access to multiple sliders. 'Master' and 'PCM' are the ones I have to adjust. 

If you don't see the icon, right click on the panel, Add to Panel, Volume Control.

If you aren't using PulseAudio, you can also run the following to see if you have multiple sliders:
```

alsamixer &

```

---

### Post by nubix on 2009-02-08
there were discrepancies with the device being used for audio output with many programs including the system volume control. i fixed it myself im sorry to have bothered you! :D i was just so frustrated!!!! :(

---

### Post by nubix on 2009-02-08
but please explain to me the difference between alsa oss and pulse audio exc....
because i have absolutely no knowledge in this part of the linux universe, it could help with future problems.

---

