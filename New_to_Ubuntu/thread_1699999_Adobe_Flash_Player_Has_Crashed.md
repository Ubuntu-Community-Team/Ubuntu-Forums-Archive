---
title: "Adobe Flash Player Has Crashed"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-03-04
I can't get anything at YouTube to play. All I get is a gray screen that says....

**"Adobe Flash Player Has Crashed....Send Crash Report"**

If I embed the page on a forum or facebook I can watch it fine.

I have looked around and tried a few things I have found here, but nothing has worked.

Is it something that just doesn't like YouTube in my computer?

---

### Post by Frogs Hair on 2011-03-04
First , what browser and flash version are you using ? Second , if you are using Firefox , give this add-on a try.[https://addons.mozilla.org/sl/firefox/addon/flash-aid/](https://addons.mozilla.org/sl/firefox/addon/flash-aid/)

---

### Post by Greg Mueller on 2011-03-04
Yes Firefox
I tried to update Adobe but it says I have the latest version

I'll try it
Thanks

---

### Post by Greg Mueller on 2011-03-04
That seems to have worked.
Thanks a bunch

Now to figure out how to mark this solved ??

---

### Post by davidmohammed on 2011-03-04
well done ... see my signature!

---

### Post by Frogs Hair on 2011-03-04
> **Greg Mueller said:**
> That seems to have worked.
Thanks a bunch

Now to figure out how to mark this solved ??

Glad it worked , that add-on seems to help a lot of people.

---

### Post by Softa on 2011-03-04
Unfortunately, it didn't work for me.  I still get the grey screen, and I have to xkill it.

Any ideas or suggestions would really help.

Thanks

---

### Post by Jose Catre-Vandis on 2011-03-04
I have been getting this too. Simply refreshing the page seems to fix it for me? Fortunately not too enslaved to youtube :)

---

### Post by ikt on 2011-03-04
> **Softa said:**
> Unfortunately, it didn't work for me.  I still get the grey screen, and I have to xkill it.

Any ideas or suggestions would really help.

Thanks

Do you still have the issue if you use chromium?

---

### Post by Softa on 2011-03-05
I use only Firefox and/or Thunderbird.

A friend however, suggested that I uninstall and then reinstall Adobe Flash player to see if that might help.  I'll let you know if it helps.

---

### Post by gradinaruvasile on 2011-03-05
The latest Adobe flash has issues on newer nvidia cards.
If you use the adobe-provided 10.2 r152 flash player version and have a nvidia card that supports vdpau playback (8 series or higher) + proprietary drivers you might experience crashes, blank flash areas, remaining screen corruption after the browser is closed, tearing video playback via vdpau in media players etc caused by the new Stage Video technology that in some cases (the sites have to have a stage video supporting embedded player) can use the cards hardware decoding capabilities (vdpau on nvidia, uvd2/3 on ati/amd 4xxx/4xxx+ series cards).
On nvidia cards that have vdpau capabilities the plugin works very badly (detailed above) - i have a nvidia 8200 IGP (vdpau B) and a nvidia Quadro NVS 135M (vdpau A) card and both exhibit these symptoms. I dont know about the aforementioned ati card having these issues.

A workaround is to use the flash player bundled with Chrome (version 10.2 r154) that has the problematic new feature (Stage Video) disabled as it seems (so no hw decoded video possible on youtube/etc but no additional headaches either). This flash player (libgcflashplayer.so from the google chrome install directory) works with any browser.

The 10.2 flash issue is present in any browser in Linux (including Chromium) except Chrome - because Chrome it has its own problem-free flash plugin bundled.
It might not be the OP's case, but others who see this thread should know these issues.

---

### Post by Softa on 2011-03-05
The problem just started within the last 24 - 36 hours.  Up until then, everything was just fine.

---

### Post by sideburns on 2011-03-05
I'm Sofia's brother, and tech support.  AFAIK, crashes are the only symptom.  We'll try uninstall/reinstall first and see if it helps.  Thanx anyway, as somebody else may find your post exactly what they need.

---

### Post by reiki on 2011-03-05
YouTube crashing my firefox here as well. Ubuntu 10.04. Seems to have started with the latest flash plugin update as I don't install from outside the repositories.

** edit ** ok I can do youtube again and not crash. I installed Google Chrome (not Chromium) browser. Seems to have taken care of the problem.

---

### Post by reiki on 2011-03-05
Try this if you can...
Go to [http://moodstream.gettyimages.com/](http://moodstream.gettyimages.com/)
Just right-click on the page and go to settings and uncheck the box for hardware acceleration. 

That seems to have fixed flash in firefox for me. Not sure if there's a way to do it without opening that page.

---

### Post by skag on 2011-03-05
indeed the crashes stopped when i unchecked hardware acceleration.... i think you can change the settings from every site that uses flash... thnx :D

---

### Post by beew on 2011-03-05
> **gradinaruvasile said:**
> The latest Adobe flash has issues on newer nvidia cards.
If you use the adobe-provided 10.2 r152 flash player version and have a nvidia card that supports vdpau playback (8 series or higher) + proprietary drivers you might experience crashes, blank flash areas, remaining screen corruption after the browser is closed, tearing video playback via vdpau in media players etc caused by the new Stage Video technology that in some cases (the sites have to have a stage video supporting embedded player) can use the cards hardware decoding capabilities (vdpau on nvidia, uvd2/3 on ati/amd 4xxx/4xxx+ series cards).
On nvidia cards that have vdpau capabilities the plugin works very badly (detailed above) - i have a nvidia 8200 IGP (vdpau B) and a nvidia Quadro NVS 135M (vdpau A) card and both exhibit these symptoms. I dont know about the aforementioned ati card having these issues.

A workaround is to use the flash player bundled with Chrome (version 10.2 r154) that has the problematic new feature (Stage Video) disabled as it seems (so no hw decoded video possible on youtube/etc but no additional headaches either). This flash player (libgcflashplayer.so from the google chrome install directory) works with any browser.

The 10.2 flash issue is present in any browser in Linux (including Chromium) except Chrome - because Chrome it has its own problem-free flash plugin bundled.
It might not be the OP's case, but others who see this thread should know these issues.


I have an Nvidia card that is vdpau capable and the new flash works quite well actually, cpu usage is very low even for 1080p on youtube, before only mplayer and XBMC (both use vdpau) can achieve that kind of performance.  On sites other than Youtube it is kind of hit and miss.

I have experienced some of those problems you described but only very briefly in the beginning.  Now I am not seeing them anymore. 

I do notice that it crashes sometimes in FF4 beta , especially for the Youtube 3d channel (I was just there for testing), but refreshing the page solves the problem. I think it may have something to do with FF beta though as it is much more rarely that flash crashes in Opera.

---

### Post by Softa on 2011-03-06
I've tried everything that you all have suggested, but to no avail. :(  I'm stumped.

What next?  I'm willing to do almost anything, if it will help.

I just thought of something.  I *think* this started for me when one of the last updates was installed.  If so, how do I go back to the one before?

---

### Post by sideburns on 2011-03-06
We tried removing/replacing flash, but when we went to the Package Manager, none of the flash packages were marked as installed.  I selected the flash installer and had it install that, but nothing.  Still no sound.  However, we're now not getting sound from anything, including Rhythmbox, so we may have accidentally lost something.

---

