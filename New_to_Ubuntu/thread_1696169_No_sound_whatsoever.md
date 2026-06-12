---
title: "No sound whatsoever"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by daoster on 2011-02-27
I recently tried to make it so that my laptop would play music through my headphones only.  Not only did it not work, apparently, sound has completely disappeared from my laptop!  

I can still access the alsa-base.conf, and I've deleted the extra stuff that I added to try to make the music go through the headphones only, but I still don't get any sound! 

Anybody know what's up?

---

### Post by LewRockwellFAN on 2011-02-27
If you don't get a better answer from someone who knows more about it and can tell you what it was you must have changed and not changed badk or if you just don't want to wait, you could try useing Synaptic and uninstall everything that looks like it is involved, keeping careful note of what you uninstall and then reinstall it, hopefully getting back installation default settings. Might not work, as uninstalling doesn't always eliminate all config files and such and sometimes old settings persist when you reinstall. But I don't see how it could hurt as long as you are careful to make note of everything uninstalled, including the things Synaptic asks permission to uninstall along with the things you tell it to uninstall because of dependencies and such.

---

### Post by daoster on 2011-03-01
Anybody else with suggestions?  I want to try all other options before I start uninstalling and installing!

---

### Post by LewRockwellFAN on 2011-04-04
One more thing if you try the uninstall and reinstall approach. After you do the uninstalling, you might spend some time running down config files and deleting them before you reinstall. In Synaptic with "all" highlighted click settings/filters/new, name it trash or something, click "deselect all" and check "orphaned" and "residual config". Then use the new filter to take out the trash. For some reason it doesn't always work, so I would still search for relevant config files manually and delete them before reinstalling to prevent some bad settings from the previous installation getting reset automatically.

---

### Post by barnex on 2011-04-04
A possible problem is that some audio channels are muted. Open your volume control, select "visible channels", enable all of them, then unmute all of them and put them on maximum volume. 

I once had a clean install where the PCM channel was muted and invisible by default, for some reason. It took me quite a while to figure this out. 

Hope this helps.
cheers.

---

