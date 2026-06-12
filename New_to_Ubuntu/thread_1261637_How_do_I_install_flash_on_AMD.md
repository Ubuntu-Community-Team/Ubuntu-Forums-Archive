---
title: "How do I install flash on AMD"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by eddski on 2009-09-09
I've been trying to install flash on my amd system and get an error telling me the "Error: wrong architecture "i386" " on the status line when I left click the flash 10 .deb package. There are browsers open or any other windows open, what am I doing wrong?

---

### Post by QIII on 2009-09-09
If you are running the 64 bit version of Ubuntu, I think you will continue to encounter that error using the drop-down box on Adobe's website.  I think the Flash for 64 bit systems is still an Alpha -- but you can install from the .tar if you are adventurous and follow the instructions carefully.

Unless you are fairly familiar with doing that sort of thing, for the moment I'd just use the version from the repositories.  If I am not mistaken, I think Jaunty will update to version 10.0.32.18 (32 bit).

Make sure that gnash and swfdec are NOT installed, as they will cause conflicts.

---

### Post by eddski on 2009-09-09
According to Synaptic Package Manager, I have 2 packages installed and now I am totally confused.
flashplugin-nonfree 10.0.32.18
flashplugin-installer 10.0.32.18
And they both have green filled boxes.
Is there anything I can do next?

---

### Post by QIII on 2009-09-09
That's what you need to be checked.  What that will do is cause Flash to be installed.

Go back to Synaptic (since I'm not sure of your level of experience or comfort with using the command line, I'll suggest the GUI for now) and check for gnash and swfdec.  If they are installed, uninstall them.  They cause conflicts with Flash and it may appear that Flash is not working.

---

### Post by gn2 on 2009-09-09
oops

---

### Post by gn2 on 2009-09-09
If you have 64-bit Ubuntu, [these instructions]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml") should help. 

[Download it here]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by eddski on 2009-09-09
I had read about removing gnash and swfdec and I checked and they were not installed. But according to synaptic I already have flash installed.

---

### Post by QIII on 2009-09-09
Are you not able to view Flash content?

---

### Post by eddski on 2009-09-10
Sorry for the late reply, had some kernel probs, but no, I cannot view flash content.

---

### Post by oldos2er on 2009-09-10
There is a script to install the latest 64-bit Flash here: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

 The version of Flash in the repos is 32-bit (with nspluginwrapper).

---

### Post by eddski on 2009-09-11
I getting a little frustrated, as I have all the files installed and the wrong ones are not installed, yet I still cannot get any flash videos to play. Does it matter what browser I'm using(swiftfox), or should I switch to another browser?

---

### Post by bumanie on 2009-09-11
The only way I could flash working with any sort of stability on a 9.04 64 bit machine was following [this]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html"). Never had a problem since. You have to copy the commands to a text document as firefox needs to be closed when doing the commands.

---

### Post by SunnyRabbiera on 2009-09-11
the install from the repos should have worked, but there are many who have issues with it.
Blame adobe on this one

---

### Post by DougieFresh4U on 2009-09-11
I just installed flash tonite using this:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)
Make sure all other flash is removed.If you need more assistance, let me know and I'll try to help.

---

### Post by eddski on 2009-09-11
I'm preyty sure I am using 32-bit, my apologies for misleading anyone, but I'm looking for 32-bit installation info. I tried the installation on their website and keep getting "Error: wrong architecture 'i386' " even after uninstalling my supposedly installed packages through synaptic.

---

