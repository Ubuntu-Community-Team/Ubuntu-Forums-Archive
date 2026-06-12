---
title: "Not getting sound??? Help me!!"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by nirmalfx3 on 2010-08-15
**Not getting sound??? Help me!!** 			 			 			 		   		 		 		I am not getting sound output from the system...
i earlier got it...But after reinstalling I removed Sound applet from the Panel...
Hardware is detected as it should be.
I think it is because I configured the applet earlier, but as I removed it, I don't know how to restore it...

So tell me how to restore the sound applet as It is not coming in Add to panel menu....

---

### Post by superninja on 2010-08-15
Can you access it from System> Preferences> Sound?

---

### Post by nirmalfx3 on 2010-08-15
Device for output is set to Dummy output stereo....
Normally options come for switching between headphones and output in applet...

---

### Post by superninja on 2010-08-15
Maybe try reinstalling the ALSA driver for your speakers or doing a power cycle (where you turn of your computer then unplug/take out battery). Heres the link to the ALSA drivers [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

---

### Post by nirmalfx3 on 2010-08-15
I just want to restore the applet!!!

---

### Post by superninja on 2010-08-15
Right click on the panel, Add to Panel, choose Indicator Applet. It will make a sound applet and a mail applet. But if your hardware is not being recognized I don't think that the applet will recognize it either, but I may be wrong.

---

### Post by nirmalfx3 on 2010-08-15
Problem solved!!
I got sounds now after configuring the applet...
Many many thanks to you....

---

### Post by jmfal on 2010-08-15
System>preferences>sound

right click on sound, click add this launcher to panel

If you still don`t have sound, try

         ```
  alsamixer
```

in a terminal, select your sound card and make sure volume/pcm/speakers are turned up

must use arrows on keypad, left/right changes selection< up/down changes vloume/output

---

### Post by superninja on 2010-08-15
Cool :). I didn't think that would do it, but I guess I'm wrong. No problem :)

---

