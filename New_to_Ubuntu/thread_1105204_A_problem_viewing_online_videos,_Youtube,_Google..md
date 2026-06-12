---
title: "A problem viewing online videos, Youtube, Google."
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Extreedoc on 2009-03-24
Hi,

I have had Ubuntu 8.10 for a few days only, I am getting on fine with it but find that most (but not all) Youtube and Google videos don't work, the screen remains black, the loading bar seems "greyed out" but is visible and goes up as expected but the video doesn't appear. The really funny thing is that *some* videos work but most do not(??) I installed Gnash when I found that my personal videos weren't working and that went well. I also installed the "Ubuntu restricted extras" as recommended on this forum. Still no go. I had "Firestarter" installed and have tried disabling it to no effect, Now I have uninstalled it and still no good. I also have "WOT" and have disabled it...no good. Oh, I also tried a Gnash re-install, that didn't work either. In the case of the Google videos, the message is: "Cannot connect with the server".
Any ideas?

---

### Post by chrisinspace on 2009-03-24
It sounds like you have conflicting Flash players installed.  You should completely remove all Flash players, decide on the one that works best for you, and then reinstall it.  I generally use Adobe's Linux Flash player and I don't really run into issues, but I know a lot of people advocate Gnash because it's truly open source.

---

### Post by leonardo_neo on 2009-03-24
I have heard that Firefox is giving trouble with youtube and other streaming videos recently.

A fix has been discovered for that. You can try that.

Open terminal and enter the following 3 commands.....

> 
1 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
2 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
3 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

This helped many people, and I hope this should help you too.

Best of luck :)

---

### Post by Extreedoc on 2009-03-24
> **chrisinspace said:**
> It sounds like you have conflicting Flash players installed.  You should completely remove all Flash players, decide on the one that works best for you, and then reinstall it.  I generally use Adobe's Linux Flash player and I don't really run into issues, but I know a lot of people advocate Gnash because it's truly open source.

Thanks for this Chris, is there a simple way to check what Flash players I might have? I've looked in "Add and Remove" and can't see any other than Gnash, there is a lot of GStreamer stuff but that isn't flash player is it?

Leonardo: thanks also for this, I will try this if I can't find any other Flash players, being a noob to Linux I am slightly intimidated by the terminal. I suppose you press enter between each command and don't enter the numbers 1,2,3.

---

### Post by philinux on 2009-03-24
An easy way in firefox is Tools>addons>plugins. Look for flash and report back.

---

### Post by chrisinspace on 2009-03-24
Try leonardo_neo's commands and see if that helps.  The 3rd command he gave you is actually uninstalling Gnash and then replacing it with the closed-source Adobe Flash player.

Don't let the command line intimidate you.  You've already got the right idea.  Copy everything but the number and then paste it into the command line and hit 'Enter'.  The last command (#3) might take a couple of minutes to run depending on the speed of your computer...there's a lot going on there.

---

### Post by Extreedoc on 2009-03-24
> **philinux said:**
> An easy way in firefox is Tools>addons>plugins. Look for flash and report back.

Ok, I've got Shockwave Flash 9.0 which appears to be the Gnash.
I also have Quick Time 7.2.0, Totem web browser2.24.3 and Windows media player 10 Totem compatible. These all deal with video streaming but aren't Flash, just thought I'd better mention them.

---

### Post by Teamgeist on 2009-03-24
Ok, you should uninstall gnash via Synaptic or via ```
sudo aptitude purge gnash
```

Afterwards install the ubuntu-restricted-extras package via Synaptics or via ```
sudo aptitude install ubuntu-restricted-extras
```

This will install all kinds of codecs, java6 and also the original Adobe flashplayer for you.

---

### Post by chrisinspace on 2009-03-24
Did you try the commands leonardo_neo recommended?  Here they are broken out in a little bit easier format for copy/paste:

1
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

2
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

3

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

---

### Post by Extreedoc on 2009-03-24
> **chrisinspace said:**
> Did you try the commands leonardo_neo recommended?  Here they are broken out in a little bit easier format for copy/paste:

1
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list
```

2
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

3

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

Yes! Thank you Chris and Leonardo, I have just had my first encounter with the terminal and everything works! I have just watched two vids that I previously couldn't see.

I am most grateful to you all who have helped. I do have another couple of questions but they can wait for another day.

John.

---

### Post by Extreedoc on 2009-03-24
> **Teamgeist said:**
> Ok, you should uninstall gnash via Synaptic or via ```
sudo aptitude purge gnash
```

Afterwards install the ubuntu-restricted-extras package via Synaptics or via ```
sudo aptitude install ubuntu-restricted-extras
```

This will install all kinds of codecs, java6 and also the original Adobe flashplayer for you.

All working now, I have already installed the restricted extras. Bit disappointed at Gnash, I would have preferred an open source player but...shame.

---

### Post by chrisinspace on 2009-03-25
No problem.  I'm glad we could help.  The community is one of the best things about Linux in general, but especially Ubuntu.

---

### Post by carml on 2009-03-25
It worked for me also,before I was a bit frustated and unhopeful about this problem on Youtube.:P
Thanks a lot,even if I would have prefered to use Gnash.

---

