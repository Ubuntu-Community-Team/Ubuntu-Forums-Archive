---
title: "converting .mp3 files"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by DFord425 on 2009-02-09
Is there a good application that can convert .mp3 files to a type where i can make an audio cd that i can play in a car. I dont think .ogg will play in most cars, but im not sure.

---

### Post by uberg on 2009-02-09
Use k3b to burn the audio CD.  This will take your files and convert to wav files on the audio CD.

---

### Post by DFord425 on 2009-02-09
When i try that i get this error message:
```
Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
/home/dford/Music/Nickelback/Dark Horse/01 - Nickelback - Something In Your Mouth.mp3
```

---

### Post by SuperSonic4 on 2009-02-09
I use soundkonverter

---

### Post by DFord425 on 2009-02-09
Thanks

---

### Post by houstonbofh on 2009-02-09
There is a very good reference on sound conversion here. [http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux)

---

### Post by DFord425 on 2009-02-09
> **SuperSonic4 said:**
> I use soundkonverter

Is there any plugin or anything else i have to do to be able to convert .mp3 to .wav, it doesnt seem to let me do that as is.

---

### Post by Gannon8 on 2009-02-09
I use MediaCoder, but its a little technical.

A very easy way to do it is at [http://www.mediaconverter.org](http://www.mediaconverter.org)

---

### Post by sydbat on 2009-02-09
I use GnomeBaker. It seems to handle the conversion in stride. Simple to use too. It's in the repos.

Also, you mention plugins...have you followed the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") how-to?

---

### Post by unplugged23 on 2009-02-09
You also might want to check synaptic to make sure you have all the codec packages installed. This should help alot!

---

### Post by DFord425 on 2009-02-09
Ok so i tried using this from one of the links above.
```
mpg123 -w song.wav song.mp3
```
But i cannot find where the .wav file is. Does anyone know where the converted file would be, i did not specify a directory in the command.

---

### Post by uberg on 2009-02-09
Sorry, 
     kb3 should work if you follow the instructions found here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

     I actually had to go and look it up myself as i haven't tried to burn from mp3's in awhile.  
  
     If you were to cut and paste the commands for your version of Ubuntu it will get the proper codecs necessary.  

[B]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

[/B]I used the instructions for 32 bit Ubuntu Users but then had to: sudo apt-get install libk3b2-extracodecs libtunepimp5-mp3 libxine1-ffmpeg to add the codecs for the 32 bit Kubuntu Users that were missing from that line.  

     I like Gnome but i use a  lot of KDE apps. 

     After you do that you shouldn't get that error message anymore.

Joe

---

