---
title: "ABSolutE NOOB Rhythmbox"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Darkhorse85 on 2009-12-21
Rhythmbox does not want to open or import any mp3 or aac files. (those are the only ones i have tried.) It has also crashed while i was trying to load a folder. My music is on my windows partition (in the host folder) When I drop a single file into the library it says transferring 1 out of 1 ( 0%) and stays that way indefinitely. I couple of times it has said it is unable to play MPEG-1 Layer 3 (MP3) and when i request the plugin it says no packages available. also i have tried copying songs to the ubuntu desktop and adding it to the library or playing it. Doesn't work either. I have tried opening it with movie player to and it didnt work. Please help, if possible in a step by step sequence as i have very little programming experience and i'm still learning. Im running 9.10. 

Thank you very much indeed

---

### Post by USB_NL on 2009-12-21
hi 
find in [Ubuntu software center] this install [Ubuntu restricted extras]
ok?

---

### Post by CaptainMark on 2009-12-21
+1 by default ubuntu wont play mp3 ubuntu-restricted-extras installs the codecs you need

---

### Post by USB_NL on 2009-12-21
Hi again

this is the commandline way

applications>accessories>terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 3rdalbum on 2009-12-21
First you need to load up the list of available packages. Usually this is loaded when you install, but if you weren't connected to the Internet at the time then this wouldn't have been done.

Connect your computer to the Internet. Go to System > Administration > Software Sources and make sure that the first four checkboxes are ticked. Close it. go to System > Administration > Synaptic Package Manager. Hit the Reload button and Ubuntu will download a list of packages available to it.

Now when you go to play an MP3 file, it will search for the codec in the repository and then install it.

Another good option is to kill lots of birds with one stone and use Synaptic Package Manager to install the "ubuntu-restricted-extras" package. This gets Flash, Java, most of the codecs you'll ever need, Microsoft fonts and MIDI playback. And probably other stuff too that I've forgotten about.

---

