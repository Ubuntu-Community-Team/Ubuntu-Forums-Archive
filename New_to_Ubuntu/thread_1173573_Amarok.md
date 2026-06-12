---
title: "Amarok"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-05-29
Does anyone know how to configure Amarok 2.0.2 to play through a wireless USB headset instead of your computer speakers?  It no longer seems to have "Engine" listed on the left when you click on Settings > Configure Amarok.

---

### Post by markbuntu on 2009-05-29
Well, it can get complicated. If you are using KDE you can try changing the settings in the system settings menu. 
If you are using gnome, you need to change the output device in the pulseaudio volume control if your system is set up so amarok plays through pulseaudio.

Amarok uses xine. If you get xine-ui then you can configure all the xine settings. To gain access to the settings open xine and right click on the window and select settings. You need you to set the Configuration experience level to Master of the known universe to see the settings in audio that you need.

---

### Post by hifly1231 on 2009-05-29
> **markbuntu said:**
> Well, it can get complicated. If you are using KDE you can try changing the settings in the system settings menu. 
If you are using gnome, you need to change the output device in the pulseaudio volume control if your system is set up so amarok plays through pulseaudio.

Amarok uses xine. If you get xine-ui then you can configure all the xine settings. To gain access to the settings open xine and right click on the window and select settings. You need you to set the Configuration experience level to Master of the known universe to see the settings in audio that you need.

I am using Gnome (Ubuntu 9.04).  How do I change the output device in Pulse Audio volume control so that Amarok plays through Pulse Audio?

---

### Post by hifly1231 on 2009-05-31
Just to let others know in case they have the same problem and are still using Amarok 1.4.10, if you click on Settings>Configure Amarok>(left side of screen)Engine, first set output to Alsa, then under **ALSA Device Configuration** in the **Mono** & **Stereo** box, simply type in **hw:Headset,0**(this is how Skype lists your headphones also), and it will point to your USB headset, and the music will play through them.  I'm trying to find out an easier way to do this rather than manually type it in everytime I want to switch between the two, but this is my solution for now.

I guess when I finally upgrade to Jaunty Jackalope (and I won't until they get all the horrible Windows-like bugs out of it) I'll start trying to figure out how to configure Amarok 2.0.2, since they seem to have gotten rid of the "Engine" option on the setting screen.

---

