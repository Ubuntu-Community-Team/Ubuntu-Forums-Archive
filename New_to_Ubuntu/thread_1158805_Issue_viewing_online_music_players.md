---
title: "Issue viewing online music players"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by bodyofchrist on 2009-05-14
I recently started using Ubuntu and I have an issue getting all of the music players to show up online.  I have all of the flash and java downloaded and I'm not really sure why they aren't showing up.  If you could help me resolve this issue I would appreciate the help.  thank you.

---

### Post by AndThenWhat on 2009-05-14
Okay, just open up Synaptic (System -> Administration -> Synaptic Package Manager) and type "mozilla" in the Quick Search box.  Then, if their checkboxes are not already green, make sure you check/mark these for installation:

totem-mozilla
flashplugin-installer
adobe-flashplugin

Then click Apply and let Synaptic work its magic.  After that finishes you can open up Firefox and hopefully videos start working. Otherwise, a dialog should popup and offer to install flash for you.

---

### Post by bodyofchrist on 2009-05-14
Alright I'm trying that now.  thank you ^_^

> **AndThenWhat said:**
> Okay, just open up Synaptic (System -> Administration -> Synaptic Package Manager) and type "mozilla" in the Quick Search box.  Then, if their checkboxes are not already green, make sure you check/mark these for installation:

totem-mozilla
flashplugin-installer
adobe-flashplugin

Then click Apply and let Synaptic work its magic.  After that finishes you can open up Firefox and hopefully videos start working. Otherwise, a dialog should popup and offer to install flash for you.

---

### Post by bodyofchrist on 2009-05-14
Well, that didn't work.  Perhaps the player isn't a flashplayer?  It's a music player like on imeem.

---

### Post by AndThenWhat on 2009-05-14
Yeah IMEEM uses flash to display their music player.  If you're using Firefox then go try going to (Edit -> Preferences) then go to the Applications tab.  Scroll down until you see Shockwave Flash and make sure it is using Shockwave Flash in the dropbox on the right.

---

### Post by bodyofchrist on 2009-05-14
everything is saying it's set up right but no music players are showing up.  I'm really not sure what's going on.
Thank you for your help. 

Is there anything else you can think I can try?

> **AndThenWhat said:**
> Yeah IMEEM uses flash to display their music player.  If you're using Firefox then go try going to (Edit -> Preferences) then go to the Applications tab.  Scroll down until you see Shockwave Flash and make sure it is using Shockwave Flash in the dropbox on the right.

---

### Post by aimpau on 2009-05-14
sudo apt-get remove swfdec-mozilla swfdec-gnome

These files interfere with adobe flash plugin. I already had that kind of problem before.

---

