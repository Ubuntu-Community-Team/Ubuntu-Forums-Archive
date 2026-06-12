---
title: "Happy pets sound wont dissapeer even after the internets been shut down"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by kitsuneclem on 2011-02-16
as thread Title says I cant seem to get rid of the happy pets sound

things I've tried

>  clearing private data, Trying to refresh InternetIs there any thing I can do? the game froze and i force quit the session now its stuck on a loop (the soundtrack that is)

Ps dont ask me to go bug Crowdstar about this they tend to play the "its your fault not ours" play like A LOT!

---

### Post by uRock on 2011-02-16
What are you talking about? Happy pets sound? Need more info in order to be helpful.

---

### Post by kitsuneclem on 2011-02-16
> **uRock said:**
> What are you talking about? Happy pets sound? Need more info in order to be helpful.
Happy pets the face book game by crowdstar
the music is still playing even though IM no longer on that net session
Prolly an issue with Mozzila and Ubuntu Just need a way to turn off that sound

---

### Post by uRock on 2011-02-16
Doesn't stop when you close the browser?

---

### Post by kitsuneclem on 2011-02-16
> **uRock said:**
> Doesn't stop when you close the browser?
Nope the sound is looped for some reason all other sounds working fine

---

### Post by uRock on 2011-02-16
Open System> Administration> System Monitor, then click the Processes tab, then click the firefox process, then click the end process button.

---

### Post by kitsuneclem on 2011-02-16
> **uRock said:**
> Open System> Administration> System Monitor, then click the Processes tab, then click the firefox process, then click the end process button.
thanks 

ps why didnt i think of that...

Pss ending firefox process didn't help neither did unplugging Internet but i reset my comp and that seemed to address the problem

---

### Post by amsterdamharu on 2011-02-16
Log out and log in should do the trick, I assume it's a game that need X.

If that didn't work and reboot isn't an option check out the programs using sound.
Press alt + F2, type pavucontrol and click run.

Under the "playback" tab there should be a list of programs using sound. You can mute the sound here or if it has the name of the program try to kill it.

---

### Post by kitsuneclem on 2011-02-16
thanks a reboot fixed it though no happy pets sad theme is all i can hear in my head

(ps how do you change thread to solved)

---

### Post by amsterdamharu on 2011-02-16
If you click on the thread tools link you should get an option "mark as solved"

---

