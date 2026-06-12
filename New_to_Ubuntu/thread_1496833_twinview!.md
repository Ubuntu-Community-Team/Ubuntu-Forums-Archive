---
title: "twinview!"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by maryalesia on 2010-05-29
Hey y'all!

I'm running ubuntu 10.04 on my gateway laptop, and I have a question about twinview in Nvidia settings. 

The laptop monitor is 1440x900, and the external monitor is 1920x1080.  I've gotten it to work before by setting the resolution on the external monitor to 1440x900, but doing so undermines the visual quality. I would like to know if there is a way to make twinview work without changing the resolution on either monitor and maintaing the full desktop image on my laptop, not just the corner of the image projected on my external monitor. 

Furthermore, when two monitors are hooked up, the external monitor has a screen tearing issue, while the laptop monitor is fine. If I disable the laptop monitor, the problem on the external monitor dissapears. Is there a way to get the screen tearing gone, or at least to shift it onto my laptop monitor? I've tried setting the external monitor as the main x-screen, to no avail.

In Vista, nvidia would auto-format the external monitor to the correct resolution while maintaining a full desktop on my laptop monitor. The screen would tear badly on my laptop monitor, but I didn't mind that because I use the TV to watch shows on hulu. 

Sorry for the long-winded question; any help would be much appreciated!

---

### Post by quixote on 2010-05-30
I don't know if this can help your specific problem, but the best thing I've found to get monitors to play nice is [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution").

---

### Post by maryalesia on 2010-06-07
> **quixote said:**
> I don't know if this can help your specific problem, but the best thing I've found to get monitors to play nice is [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution").

Thanks for the help; I typed in the command, but it came up with only the info on my laptop monitor, not the flatscreen. :confused:
anyway, I'm just going to stick with my solution of disabling the laptop monitor. The screen still tears during video playback, but not nearly as bad as when I use twinview. Maybe one day linux and nvidia will learn to live with one another in harmony ... untill then, though :)

---

### Post by quixote on 2010-06-07
Yeah, getting graphics cards and monitors to work right is generally a big project, if they're not doing it out of the box.  Nvidia is still easier than ATI (which isn't saying much).  Are you using the "nouveau" driver?  It's the open source driver, but for my purposes it's way better -- for a change -- than nvidia's own!  I don't know if it would help in your case though.  Setting up and editing an xorg.conf file may be the only solution :(.  xrandr is purely command line, and you have to give it all the switches and info it needs.  There's more at the link.

Or, as you say, just disable the laptop monitor and not worry about it.

---

