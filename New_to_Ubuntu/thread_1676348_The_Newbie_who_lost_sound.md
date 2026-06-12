---
title: "The Newbie who lost sound"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by platyviolence on 2011-01-27
(Warning: Although I am proficient with other operating systems, I am an Ubuntu noob!)

Hey everyone, allow me to begin by saying I absolutely love this operating system. It's so sharp, responsive and very logical.

Everything runs fine, no graphic issues, no sound issues. I install Mangler (Linux Ventrilo client) but I am simply unable transmit my voice through the microphone. I browsed many forums, including these particular ones (to which I found the most help!) and ended up downloading a program called "GNOME ALSA MIXER." 

Though people had similar problems, none was like mine. I had sound just fine but I simply could not find out why I couldn't use my microphone. 

LONG STORY SHORT, in attempt to change settings in hopes of getting my microphone to work I have now lost sound all together. And like me, when I accidentally stumble upon a problem sometimes I poke around a little too much and find myself in a bigger hole than in which i started. 

I don't know how to restore defaults, I don't know if I left something checked or unchecked that I shouldn't have and I also don't know if GNOME ALSA MIXER overrides settings I change in sound preferences. 

So please, fellow Ubuntu know alls, shed light on this situation so that I may do the same to others in the future! Thankyou! I can provide any information as long as you explain to me how to do it if it's not obvious to my noob brain!


I have the latest version of GNOME ALSA MIXER.

Ubuntu
Release 10.10 (Maverick)
GNOME 2.32.0

---

### Post by migs73 on 2011-01-27
Welcome,

The best place to start for sound issues is probably here;

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)


Regards

Mike

---

### Post by fabricator4 on 2011-01-27
The Alsa mixer is good.  The most likely thing is that you've inadvertently left one of the mute buttons clicked on.  In particular, make sure all four level sliders are at the top - the four to the left of the Alsa panel. 

For using the microphone make sure the record button is ticked, and slide the "capture" slider to the top.

The rest is trouble shooting the speakers - are they still plugged in and powered up? Are they plugged into the right socket, not headphone, line in, or mic?

You'll note that the volume control indicator applet (on the top panel) will affect two of the sliders in Alsa.  Use one or the other, but do check.  Similarly, using mute in one will affect the other.

Chris

---

