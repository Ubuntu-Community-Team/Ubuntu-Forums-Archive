---
title: "Audio &quot;preview&quot;"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-30
I used to be able to listen to my audio files my hovering my mouse over them. How can I enable this feature in Karmic Koala?

---

### Post by Paqman on 2009-11-30
In Nautilus (the file browser) go to Edit > Prefs > Preview and make sure you've got the options set right.

---

### Post by mvalviar on 2009-11-30
The setting is set to "Local files only". When I hover on the audio files there appears a note icon on a speech bubble which I think is a visual cue that the file is being played unfortunately I can't here anything.

---

### Post by Paqman on 2009-12-01
Are the music files actually stored on your machine? If they're coming over the network then set it to "always".

You'll also need the right music player installed, but i'm not 100% certain which one Gnome uses for previews. Totem probably?

---

### Post by mvalviar on 2009-12-01
I have totem installed these files reside in ~/Music.

---

### Post by rudy.b on 2009-12-01
What type of audio files are you previewing?  I assume you can play the files normally otherwise (i.e. you've got the codecs installed for the format you're trying to play).

Otherwise, you can try running the preview from a terminal to see if any errors show up:
```
$ totem-audio-preview file:///path/to/audio.file
```

---

### Post by mvalviar on 2009-12-02
I ran the command. There aren't any errors but I can't hear anything. 
I can play these files in totem. I have the necessary codecs.

---

### Post by mvalviar on 2009-12-02
bump

---

### Post by Perturbed Penguin on 2009-12-03
I seem to be having the same issue... local files, all play fine in totem but Nautilus previews don't work. Any ideas? It may be useful to know that I am using a 'Creative X-Fi Xtreme Gamer' audio card which I think means I am using pulseaudio - at least it works now!! ;)

... I have read somewhere that installing 'esound' from the repos will fix this issue but when I mark it for installation in synaptic it marks ubuntu-desktop for uninstall which doesn't seem like a good idea. Also I noticed that some kind of pulseaudio version of esound is installed - 'pulseaudio-esound-compat', could this replacement driver, as it seems to be, possibly be buggy and be causing this problem?

---

### Post by mvalviar on 2009-12-03
> **Perturbed Penguin said:**
> I seem to be having the same issue... local files, all play fine in totem but Nautilus previews don't work. Any ideas?
I'm not alone in this.

---

### Post by Perturbed Penguin on 2009-12-03
Are you running pulseaudio mvalviar? If so would you mind checking to see if you have that same pulseaudio 'esound' driver installed? Perhaps that fix will work for you if it doesn't mark 'ubuntu-desktop' for uninstall on your system (unlikely).

---

### Post by Perturbed Penguin on 2009-12-03
Sorry for so many replies... just an update:

Installing 'mpg321' and 'vorbis-tools' as suggested elsewhere didn't seem to fix anything for me.

---

### Post by mvalviar on 2009-12-03
Yes, I am using pulse audio. I'm not sure about esound though. It's not installed to I guess I'm not using it.

---

### Post by Perturbed Penguin on 2009-12-03
Interesting, does anybody have any recommendations? Anybody know if it is safe to remove that 'ubuntu-desktop' package in order to install the 'esound' package?

---

### Post by mvalviar on 2009-12-03
> **Perturbed Penguin said:**
> Interesting, does anybody have any recommendations? Anybody know if it is safe to remove that 'ubuntu-desktop' package in order to install the 'esound' package?

I think you can't remove ubuntu-desktop since it's a metapackage.

---

### Post by Perturbed Penguin on 2009-12-03
Ah, that wouldn't surprise me. Not sure what to do then. I suppose we could try installing esound through the terminal but that should make that same package changes as synaptic, aka it would ask the user to remove 'ubuntu-desktop' as well, right?

---

### Post by mvalviar on 2009-12-03
I may be getting somewhere here. On the screenshot it appears that the preview works but its volume is nil. How the hell do I turn it up?! Whenever I move the mouse it disappears from the list.[IMG]http://img268.imageshack.us/img268/5518/audiopreview.png[/IMG]

---

### Post by mvalviar on 2009-12-04
*bump* Please help me figure this out.

---

### Post by mvalviar on 2009-12-05
shameless *bump*

---

### Post by bohoomil on 2009-12-06
Try doing the following: while hovering the mouse over a sound file, keep PulseAudio applet open and press the tab key as long as it jumps to the Preview volume slider and highlights it. Then press Home / End keys to set the volume. This should work. I had exactly the same problem a few days ago.

---

### Post by mvalviar on 2009-12-07
sorry haven't updated this. Figured it out. I ran totem-audio-preview and it appears on pulse audio's list. I can then move the slider.

---

### Post by Perturbed Penguin on 2009-12-07
> **bohoomil said:**
> Try doing the following: while hovering the mouse over a sound file, keep PulseAudio applet open and press the tab key as long as it jumps to the Preview volume slider and highlights it. Then press Home / End keys to set the volume. This should work. I had exactly the same problem a few days ago.

It took me a few minutes to realize that this will not work if you have the window settings set to make the active window the one with the mouse over it like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138993&stc=1&d=1260236407[/IMG]

This works great once you have deselected that top checkbox in Window Preferences (by default this comes deselected so for most people this is not a problem) Thanks a bunch for the tip bohoomil, I once again have audio previews, mwahaha. ;)

...btw sorry for the large pic, next time I will try and make it a bit smaller. lol

---

### Post by wyrless2002 on 2009-12-15
> **rudy.b said:**
> What type of audio files are you previewing?  I assume you can play the files normally otherwise (i.e. you've got the codecs installed for the format you're trying to play).

Otherwise, you can try running the preview from a terminal to see if any errors show up:
```
$ totem-audio-preview file:///path/to/audio.file
```


**Thanks rudy.b!** :D  

Everything was working fine in 9.04 installed on my Dell XPS 1530 laptop, then I realized tonight that PulseAudio didn't move the totem-audio-preview stream to my Logitech USB speakers (that have their own external soundcard) any more. I have the crappy laptop speakers muted (which includes the default, on-board Intel soundcard) unless I want to use the headphones, and then I just switch outputs in PulseAudio device chooser, muting the external speakers and unmuting the headphones. I know how to Move Stream on an item that is continuously playing (like Rhythmbox, or a Flash video) but was failing to figure out how to do it when the music stopped playing as I moved the cursor off of the file. After a couple of dead-end searches in and out of the 'forums, I ended up here and followed your advice. I was able to type totem-audio-preview and then I just drag-n-dropped a sound file from my music folder which automagically copied the path into the terminal. This caused the preview to continue until I closed the terminal, during which time I was able to move the stream back where I wanted it. 

I don't know exactly what caused the problem, but I had just rewired. I only have three USB jacks, and I added a USB hub for the 6 devices that I have plugged in all the time. Whenever I remove and replace the Logitech speakers, PulseAudio doesn't always play nice without a logout or a reboot.

Sorry if I ran long. It's not that you needed to know all of this, but I have often found solutions to my problems in other users descriptions of what was going on, not just in the advice of those trying to help.

---

