---
title: "linux mint-looking for audio converter"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by irish66 on 2008-12-19
Hi. I'm looking for a good audio converter. I have mp3 files, I want to a convert to a specific bitrate. I've tried sound converter, but it didn't have the bitrate I wanted. I have installed audicity, but don;t  see anything about conversions. Oh, I would like to have an add folder option. 
M

---

### Post by logos34 on 2008-12-19
lossy-to-lossy conversion will result in degraded sound, maybe not noticeable, but degraded nevertheless.  You're probably aware of it, but thought i'd mention it

Try Foobar2000 on wine.  Or k3b. Or just use lame from the cli

---

### Post by irish66 on 2008-12-19
Thank you. Actually the one I used on windows was Goldwave. Although I can't find it at the moment. According to the website it can be used through Wine. But I had no sucess when trying it before.I;ve had a look at k3b in pacage manager. but don't see anything about file conversions. I've installed foobar, but doesn't have the conversion option i want.
yep. I am aware of loss of audio quality. but has never bothered me.
"Or just use lame from the cli" Sorry. don't understand the last word/
M

---

### Post by logos34 on 2008-12-19
> **irish66 said:**
> I've installed foobar, but doesn't have the conversion option i want.

what bitrate or option are you looking for exactly?

---

### Post by SuperSonic4 on 2008-12-19
which mint are you running, gnome, kde or xfce? I know pacpl audio converter is optimised for the kde desktop

---

### Post by markbuntu on 2008-12-19
There is also soundconverter and soundkonverter(for kde).

---

### Post by logos34 on 2008-12-19
> **SuperSonic4 said:**
> pacpl audio converter is optimised for the kde desktop

yes, and there is even a script integrating it into amarok

---

### Post by SuperSonic4 on 2008-12-19
> **logos34 said:**
> yes, and there is even a script integrating it into amarok

and dolphin and konqueror although not in KDE4 I think. I used it on hardy :p

---

### Post by logos34 on 2008-12-19
> **SuperSonic4 said:**
> and dolphin and konqueror although not in KDE4 I think. I used it on hardy :p

really?  I'm still on 8.04 (gnome)--only kde apps I use are k3b and amarok

---

### Post by irish66 on 2008-12-20
Hello folks. Thanks for all the replies.
it's gnome.
I'm looking for two different options
112 joint stereo and 40 in mono.
M

---

### Post by logos34 on 2008-12-20
> **irish66 said:**
> 
I'm looking for two different options
112 joint stereo and 40 in mono.
M

You could use lame, CBR or ABR.  See 'man lame' for mor info.


Here's CBR 112 joint-stereo:

> user@ubuntu:~/music2/1-new/Garrick_Ohlsson-Beethoven_-_Piano_Sonatas,_Volume_3$ [COLOR="Red"]lame -m j -b 112[/COLOR] 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.wav 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.mp3

LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
Using polyphase lowpass filter, transition band: 15115 Hz - 15648 Hz
Encoding 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.wav
      to 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.mp3

Encoding as 44.1 kHz 112 kbps j-stereo MPEG-1 Layer III (12.6x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  4627/4627  (100%)|    0:13/    0:13|    0:14/    0:14|   9.1290x|    0:00 
-------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %                             
  112.0        8.7  91.3        99.6   0.2   0.2                               
Writing LAME Tag...done
ReplayGain: +1.7dB

user@ubuntu:~/music2/1-new/Garrick_Ohlsson-Beethoven_-_Piano_Sonatas,_Volume_3$ ls
13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.mp3
13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.wav
user@ubuntu:~/music2/1-new/Garrick_Ohlsson-Beethoven_-_Piano_Sonatas,_Volume_3$ mediainfo 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.mp3 
General #0
Complete name                : 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.mp3
Format                       : MPA1L3
File size                    : 1.61 MiB
PlayTime                     : 2mn 868ms
Bit rate                     : 112 Kbps
Writing library              : LAME3.97 

Audio #0
Codec                        : MPEG-1 Audio layer 3
Codec profile                : Joint stereo
Bit rate mode                : CBR
Bit rate                     : 112 Kbps
Minimum bit rate             : 112 Kbps
Channel(s)                   : 2 channels
Sampling rate                : 44.1 KHz
Resolution                   : 16 bits
Writing library              : LAME3.97 
Encoding settings            : CBR


mono 40: 

> 
user@ubuntu:~/music2/1-new/Garrick_Ohlsson-Beethoven_-_Piano_Sonatas,_Volume_3$ [COLOR="Red"]lame -m m -b 40 [/COLOR]13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.wav 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace-
mono.mp3

LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
Autoconverting from stereo to mono. Setting encoding to mono mode.
Resampling:  input 44.1 kHz  output 24 kHz
Using polyphase lowpass filter, transition band: 10548 Hz - 10839 Hz
Encoding 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace.wav
      to 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace-mono.mp3
Encoding as 24 kHz  40 kbps single-ch MPEG-2 Layer III (9.6x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  5036/5036  (100%)|    0:04/    0:04|    0:05/    0:05|   26.564x|    0:00 
-------------------------------------------------------------------------------
   kbps       mono %     long switch short %                                   
   40.0      100.0        99.2   0.5   0.3                                     
ReplayGain: +3.5dB

user@ubuntu:~/music2/1-new/Garrick_Ohlsson-Beethoven_-_Piano_Sonatas,_Volume_3$ mediainfo 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace-mono.mp3 
General #0
Complete name                : 13.Piano_Sonata_No._25_in_G_Major,_Op._79_-_III._Vivace-mono.mp3
Format                       : MPA2L3
File size                    : 590 KiB
PlayTime                     : 2mn 864ms
Bit rate                     : 40 Kbps

Audio #0
Codec                        : MPEG-2 Audio layer 3
Bit rate mode                : CBR
Bit rate                     : 40 Kbps
Channel(s)                   : 1 channel
Sampling rate                : 24 KHz
Resolution                   : 16 bits
Writing library              : Xing (old)


Hope that helps

---

### Post by irish66 on 2008-12-21
hi, thanks for replying. I presume last sentence See 'man lame' for mor info. should have read "see "main lame" for more info, and that I should look at lame help.it looks like you did that from Terminal. At the moment, that looks a bit complicated for me.
M

---

### Post by zvacet on 2008-12-21
Maybe this will be helpful to you:

```
sudo apt-get install mpg321 vorbis-tools
```

After that in synaptic install **nautilus-script-manager** and ** nautilus-script-audio-convert.** After you install nautilus-script-audio-convert right click on file in synaptic and you will see files recommended for install.Install them all if you want to.

```
nautilus-script-manager enable ConvertAudioFile
```

After that when you right click on audio file you will see option  **ConvertAudioFile**.

---

### Post by logos34 on 2008-12-21
> **zvacet said:**
> Maybe this will be helpful to you:

```
sudo apt-get install mpg321 vorbis-tools
```
...

How's that going to help the OP?  It only gives you 4 general quality settings, and no mono.  You'd have to edit the script file.


> **irish66 said:**
> hi, thanks for replying. I presume last sentence See 'man lame' for mor info. should have read "see "main lame" for more info, and that I should look at lame help.it looks like you did that from Terminal. At the moment, that looks a bit complicated for me.
M

I meant the man page for lame--you just type in a terminal
> 
man lame

(or you can do **lame --longhelp**)

This

lame -m j -b 112 

is difficult?  

You can even make a script to automate it and do batch conversion of .wavs.    Like this:
> 
#!/bin/bash
#
# wav2mp3
#
for i in *.wav; do
#out=$(ls $i | sed -e 's/.wav//g')
#out=$(echo $i | sed -e 's/.wav$//')
#lame -h -b 192 "$i" "$out.mp3"
[COLOR="Red"]lame -m j -b 112 [/COLOR]"$i" "${i%.wav}.mp3"
done

Name it wav2mp3.sh, and invoke it from the command line to convert all files in a given folder

If you use zvacet's script you'll have to try to add your bitrate options to the script

---

### Post by cozmicharlie on 2008-12-22
A few people mentioned PACPL and it is a great script that handles a wide variety of codecs.  I just want to add that it also does work fine in gnome.  I use it as my main converter in gnome.  You don't need to use it via Amarok either.  You can install it and use it from the command line (or it does have a very simple GUI).  The advantage of PACPL is it utilizes a wide variety of codecs, is very flexible (you can change parameters and even change which encoders you prefer, you can convert and tag simultaneously).  Installing is easy - just follow the instructions here ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl))

---

### Post by logos34 on 2008-12-22
> **cozmicharlie said:**
> A few people mentioned PACPL and it is a great script that handles a wide variety of codecs.  I just want to add that it also does work fine in gnome.  I use it as my main converter in gnome.  You don't need to use it via Amarok either.  You can install it and use it from the command line (or it does have a very simple GUI).  The advantage of PACPL is it utilizes a wide variety of codecs, is very flexible (you can change parameters and even change which encoders you prefer, you can convert and tag simultaneously).  Installing is easy - just follow the instructions here ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl))

+1

PACPL, shntool, mplayer, soX...there's a lot good command line audio utilities/converters. (although as for PACPL I can't seem to get it to work from within Amarok--the right-click menu shows but nothing happens on any of the codecs).  

Irish66,

Since you don't seem to want to use any tool from the CLI, the only other thing I can suggest is give k3b, which I mentioned in my first post, a serious consideration.  Like I said, you probably ought to be using it as your default burning app (it's simply the best native linux app), but it can rip and convert with ease to a number of formats--mp3, wav, ogg, flac, ape, mpc etc.  For mp3 you need to make sure you have libk3b2-extracodecs.  Set the lame executable in configure>plugins>external encoders

I don't think there's a way to edit the nautilus-covert script for your custom bitrates, and I couldn't seem to get soundconverter to output to the  112 bitrate (let alone mono):

gconftool-2 --type string --set /apps/SoundConverter/mp3-mode "cbr"
gconftool-2 --type string --set /apps/SoundConverter/mp3-cbr-quality "112"

doesn't seem to work or the output file is default 128kbps.   

Good luck

---

### Post by irish66 on 2008-12-22
Thanks people for all those replies. I say cautiously that Goldwave is working for me. But it's nice to have these suggestions for future reference. (1 hour or so later)Well it seems okay, if i don't move from the goldwave window. Otherwise it freezes up.
i tried the sudo apt-get install mpg321 vorbis-tools suggestion. When i right click an audio file, there is an option called scripts and within that-convert audio file, but only the option to convert to wav, ogg, or flac.
Anyway just to be more specific about what i want to do. I have a folder called "convert to 112" within those folders are sub folders. Without going into each subfolder, I want to be able to convert the audio files to my preferred bitrate.      
M

---

### Post by irish66 on 2009-01-27
Hi. Well although soundkonverter was mentioned before, I can't remember whether I tried it or not. Anyway I'm trying it now after seeing it mentioned in another thread. So thank you markbuntu.
M

---

### Post by Sylslay on 2009-01-27
Try Audacity, load the track and than export with Yours seting.
Meaby there is easy whey to do it with that softwere
PS.Greeting from westcoast

---

### Post by cozmicharlie on 2009-01-27
> **logos34 said:**
> +1

PACPL, shntool, mplayer, soX...there's a lot good command line audio utilities/converters. (although as for PACPL I can't seem to get it to work from within Amarok--the right-click menu shows but nothing happens on any of the codecs).  

I added directions for installing PACPL to Amarok ([http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl&page=5](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl&page=5)) see post #49. Hopefully this helps.

+1 for SoundKonverter  -  it should work for you

---

