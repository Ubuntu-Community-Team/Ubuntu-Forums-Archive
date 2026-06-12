---
title: "How to adjust Bass and Treble ?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ubfu on 2009-06-11
Using Ubuntu 8.04

Right click the volume panel click on volume control and I don't see any bass or treble control.

Or I need to manually control through the Rhythmbox 0.11.5 ?

---

### Post by s.fox on 2009-06-11
Hi,

Are you using pulse audio or alsamixer?

If you are using alsamixer try running this:
 
```

alsamixer -Dhw

```

-Ash R

---

### Post by ubfu on 2009-06-11
How do I know I am using alsamixer ? 
went into terminal but which one I should select for bass and treble ?

---

### Post by s.fox on 2009-06-11
Hi,

Just had a thought.  Take a look [here]("http://ubuntuforums.org/showthread.php?t=789578"). 

-Ash R

---

### Post by Sinkingships7 on 2009-06-11
Unfortunately, the "Linux Way" seems to be to extend instead of integrate. Things like audio manipulation are left to the specific program. So you won't be able to find anything satisfyingly universal, but you might be able to scratch by with alternatives. The latest build of Songbird is attempting an equalizer and it's coming along nicely. Amarok pre-2 has an equalizer, but they removed it in 2 for some reason.

---

### Post by ubfu on 2009-06-11
> **Ash R said:**
> Hi,

Just had a thought.  Take a look [here]("http://ubuntuforums.org/showthread.php?t=789578"). 

-Ash R

I had install PluseAudio but I still can't configure the bass setting.
Where is it actually ?

Using Rhythmbox
At the volume control >  Playback it doesn't show anything.

Try using Mplayer or VLC it shows but I still can control the bass.
Only have one bar increase/decrease the volume

---

### Post by ubfu on 2009-06-11
Which bar or where I can setthe bass ?

---

### Post by aysiu on 2009-06-11
Close Rhythmbox and then paste these commands into [the terminal](http://www.deviantdark.altervista.org/uploads/rhythmbox-equalizer.tar.gz): ```
wget -c http://www.deviantdark.altervista.org/uploads/rhythmbox-equalizer.tar.gz
mkdir ~/.gnome2/rhythmbox/
mkdir ~/.gnome2/rhythmbox/plugins/
tar -xzvf rhythmbox-equalizer.tar.gz -C ~/.gnome2/rhythmbox/plugins/
rhythmbox &
``` and the equalizer should show up under Edit > Plugins.

---

### Post by ubfu on 2009-06-11
> **aysiu said:**
> Close Rhythmbox and then paste these commands into [the terminal](http://www.deviantdark.altervista.org/uploads/rhythmbox-equalizer.tar.gz): ```
wget -c http://www.deviantdark.altervista.org/uploads/rhythmbox-equalizer.tar.gz
mkdir ~/.gnome2/rhythmbox/
mkdir ~/.gnome2/rhythmbox/plugins/
tar -xzvf rhythmbox-equalizer.tar.gz -C ~/.gnome2/rhythmbox/plugins/
rhythmbox &
``` and the equalizer should show up under Edit > Plugins.

Thanks , the equalizer does appear , once I enable it , the mp3 that I played having full of hissing noise. ~ ziiiiiiiii 

It don't seem to work correctly.I tried disable it and it play smoothly without the bass equalizer.

I wonder why it's so hard to have a program that support equalizer.

---

### Post by ubfu on 2009-06-12
Need help , 
I had downloaded the realtek linux driver.
What should I do ? or it'll crach with pluseaudio and ALSA ?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

> Linux driver (2.6)

5.11	2009/3/6	5038k	

What I should do next ?

---

### Post by ubfu on 2009-06-12
Should continue to install the driver provided or I need to remove the other pluseaudio or ALSA ?

---

### Post by ubfu on 2009-06-12
Does it safe to follow the instruction removing pluseaudio ?

[http://ubuntuforums.org/showthread.php?p=6068479](http://ubuntuforums.org/showthread.php?p=6068479)

---

### Post by Chemical Imbalance on 2009-06-12
Banshee has an equalizer under View, Equalizer.

I think a system-wide equalizer would be a great idea.

Last time I used windows (XP), I never noticed an equalizer either.

Does Vista have one?

---

### Post by ubfu on 2009-06-12
> **Chemical Imbalance said:**
> Banshee has an equalizer under View, Equalizer.

I think a system-wide equalizer would be a great idea.

Last time I used windows (XP), I never noticed an equalizer either.

Does Vista have one?

I installed Banshee , now playing a song but it doesn't have any equalizer under View.?????:(:(:(

---

### Post by Chemical Imbalance on 2009-06-13
> **ubfu said:**
> I installed Banshee , now playing a song but it doesn't have any equalizer under View.?????:(:(:(

Try pressing ctrl+e

Look under "help, about" and  post what version you have.

---

### Post by ubfu on 2009-06-13
Banshee 0.13.2

Music Management and Playback for GNOME.
Copyright © 2005-2007 Novell, Inc.
Copyright © 2005 Aaron Bockover

I went to [http://ubuntuforums.org/showthread.php?t=882009](http://ubuntuforums.org/showthread.php?t=882009)

Since it need to download manually the equalizer 

wget [http://www.mikesplanet.net/files/equalizers.xml.gz](http://www.mikesplanet.net/files/equalizers.xml.gz)
gunzip -c equalizers.xml.gz > ~/.config/banshee-1/equalizers.xml

Once I type gunzip -c equalizers.xml.gz > ~/.config/banshee-1/equalizers.xml
it shows  :No such file or directory


Still it doesn't show any equalizer.Please help.I went to plugin but stil can't find it.

---

### Post by Chemical Imbalance on 2009-06-13
That's wierd.  My version is 1.4.3.

Are you using Jaunty and have you installed Banshee from Synaptic Package Manager?

---

### Post by ubfu on 2009-06-13
> **Chemical Imbalance said:**
> That's wierd.  My version is 1.4.3.

Are you using Jaunty and have you installed Banshee from Synaptic Package Manager?

Sorry I am using 8.04.Still can't find any equalizer.Download through synaptic.

I tried other player , amarok does have the equalizer.Finally can set the song bass and treble.

---

### Post by Chemical Imbalance on 2009-06-13
I guess the Banshee version in Jaunty just got the equalizer then.

Glad you found one with an equalizer on Intrepid.

---

### Post by ubigT on 2009-06-16
I installed the Rythmbox EQ posted above and i was terribly excited to finally have an EQ! I hate Amarok (and 3 has no EQ... WTF?) but this EQ does nothing, it shows up, I can adjust the sliders, but there is no audible difference. Any suggestions?

---

### Post by treesurf on 2009-06-16
I suggest installing the latest stable version of Banshee 
(1.4.3), which does have an equalizer.  You can get it through the Banshee PPA:

[https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa)

There are instructions there on how to do the installation.

---

### Post by Lunx on 2009-06-16
VLC also comes with an equaliser and I find it works well, I get far better quality sound than I do with Rhythmbox, or some other players I've tried.

---

### Post by treesurf on 2009-06-16
I never knew VLC had an equalizer, but there it is hiding under Tools>Extended Settings.  And there's a Spatializer too, fun to play with!  Thanks for the tip, it certainly is a better featured equalizer than the one in Banshee.

So, for the original poster, you can find VLC in Synaptic Package Manager.  In addition to the equalizer it's an all around great program that will play just about any media file you throw at it.

---

### Post by Nipu011 on 2011-07-16
install it from software manager... search for alsamixer

---

