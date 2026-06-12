---
title: "Volume Control Applet Icon Vanished"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by jimwims on 2011-02-19
I have gnome-volume-control-applet as the command for one of my startup applications to put the volume control applet in my desktop panel when my computer starts up.  It has worked quite well for a few weeks.  However, the icon has now vanished from the panel and does not appear on startup.  I believe the applet is actually running.  If I try to run it from terminal, I get the message: "** (gnome-volume-control-applet:2213): WARNING **: Applet is already running, exiting." System monitor reports two instances of the process with the status of "sleeping."

Can anyone help me recover the icon so that I can use this applet?

TIA.

---

### Post by vivek.pandey on 2011-02-19
try this 
  system->administration->system monitor see if its sleeping then end process start again

i prefer locking the applet on panel

---

### Post by jimwims on 2011-02-19
I tried this.  When I try to restart the process from terminal by using the command "gnome-volume-control-applet", nothing happens.  Terminal just hangs. I thought I should try reinstalling the package that includes this applet, but I haven't been able to figure out what that package is. Any further thoughts? Thanks.

---

### Post by PhibreOptix on 2011-02-19
Right click the panel you want it on and click on Add To Panel..

then add the Indicator Applet
that should get it to reappear

---

### Post by wilee-nilee on 2011-02-19
The volume manager is attached to the envelope for evolution. Go to startup application in preferences and add a new one use your terminal command as the command and name it what ever, you icon will be there at startup.
gnome-volume-control-applet

---

### Post by jimwims on 2011-02-20
PhibreOptix--

Thanks for your help.  I have tried the Indicator Applet before.  It does not work for me.  As best I can tell, this applet requires use of PulseAudio.  I have had to disable PulseAudio in order to get Skype to work.  With this applet, the volume control has no effect on the speaker volume.  When I select "Sound Prefereces", I merely get a message about waiting for the sound system to respond.  I believe what I need to do is get the gnome volume control applet back working again.


wilee-nilee--

Thanks for your help also.  I have a startup application with the command line you suggest.  It worked fine until earlier today.  Now I cannot even get that command line to work in terminal.  Terminal just hangs up.  I think I need to reinstall the package that includes the genome volume control applet, but can't figure out how to do that.  I had removed Evolution from my computer, so I took what you said and reinstalled it.  That does not seem to have changed anything.


Still open to suggestions.

---

