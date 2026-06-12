---
title: "Easiest elegant way to convert  a MIDI file to MP3?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by honeybear on 2011-06-25
Hi

Please find some mid for example. I tried with sox and convert and it did not work. 

[http://www.gmajormusictheory.org/Freebies/FirstPieces/0AuraLee.mid](http://www.gmajormusictheory.org/Freebies/FirstPieces/0AuraLee.mid)

:8 :popcorn:

-- 
Onnline, one can with : 
[http://www.hamienet.com/midi2mp3](http://www.hamienet.com/midi2mp3)

Come on, sox could ... ?

---

### Post by westie457 on 2011-06-25
Your best bet is probably to try _[here]("http://www.hamienet.com/midi2mp3")_

---

### Post by honeybear on 2011-06-25
> **westie457 said:**
> Your best bet is probably to try _[here]("http://www.hamienet.com/midi2mp3")_

Thanks. I used this solution. I actually wanted to batch to convert lot of old game file I had in my old game dedicated to windows 95 cdrom ... 

In 2011, it is funny that Linux is not capable to convert easily using a sox or kind of emulator of sound card.

---

### Post by westie457 on 2011-06-25
The link I posted was found in _[this thread]("http://ubuntuforums.org/showthread.php?t=566744")_

There probably is no easy way to do what you want. However it does suggest a way.

---

### Post by ron999 on 2011-06-25
> **honeybear said:**
> I actually wanted to batch to convert lot of old game file I had in my old game dedicated to windows 95 cdrom ... 

Hi
Use **timidity**
```
sudo apt-get install timidity
```

To play the file:-
```
timidity 0AuraLee.mid
```

For mp3 pipe it to FFmpeg or LAME.
Like this:-
```
timidity 0AuraLee.mid -Ow -o - | ffmpeg -i - -acodec libmp3lame -ab 64k 0AuraLee1.mp3
```
Or this:-
```
timidity 0AuraLee.mid -Ow -o - | lame - -b 64 0AuraLee2.mp3
```

Then write a script for the batch.:)

---

### Post by honeybear on 2011-06-25
> **ron999 said:**
> Hi
Use **timidity**
```
sudo apt-get install timidity
```

To play the file:-
```
timidity 0AuraLee.mid
```

For mp3 pipe it to FFmpeg or LAME.
Like this:-
```
timidity 0AuraLee.mid -Ow -o - | ffmpeg -i - -acodec libmp3lame -ab 64k 0AuraLee1.mp3
```
Or this:-
```
timidity 0AuraLee.mid -Ow -o - | lame - -b 64 0AuraLee2.mp3
```

Then write a script for the batch.:)

thank you very much ! btw is there something else than timidity?

Gorgeous amazing replay thx!!!!!

 > apt-get install timidity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  timidity-daemon
Suggested packages:
  pmidi fluid-soundfont-gm fluid-soundfont-gs
The following NEW packages will be installed:
  timidity timidity-daemon
0 upgraded, 2 newly installed, 0 to remove and 40 not upgraded.
Need to get 614kB of archives.
After this operation, 1,552kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by andrew.46 on 2011-06-25
> **honeybear said:**
> btw is there something else than timidity?

I suspect that timidity is the best option but vlc can convert from midi to mp3 if it has been compiled against fluidsynth. My own copy has been:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc --list | grep 'fluidsynth'[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 6c101d6)
  fluidsynth             FluidSynth MIDI synthetizer

```

and your midi file converts nicely :). Details here:

MIDI with VLC media player
[http://www.remlab.net/op/vlc-midi.shtml](http://www.remlab.net/op/vlc-midi.shtml)

**Edit:** The commandline to convert your file could be:

```

cvlc -vvv --sout "#transcode{acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst=0AuraLee.mp3}" 0AuraLee.mid

```

---

### Post by ron999 on 2011-06-26
That's interesting Andrew.
My Linux version of VLC isn't compiled with fluidsynth support.
But I've emulated your work using VLC Portable from here:- [http://portableapps.com/apps/music_video/vlc_portable]("http://portableapps.com/apps/music_video/vlc_portable")
And GeneralUser GS FluidSynth v1.43.sf2 from here:- [http://www.schristiancollins.com/generaluser.php]("http://www.schristiancollins.com/generaluser.php")
Then converted the midi file by running VLC Portable in wine with this command:-
```
VLCPortable.exe 0AuraLee.mid --sout "#transcode{acodec=mp3,ab=64,channels=2,samplerate=44100}:std{access=file,mux=dummy,dst="0AuraLee3.mp3"}" vlc://quit

```

---

### Post by honeybear on 2011-06-26
thank you

**ffmpeg does not support MIDI at all** . In the second link,the author is wrong: that is a process of creating and exporting a MIDI sample 

It would be great that mencoder could, by some tricks too... I googled midi and mencoder and low resutls are given

---

### Post by mcduck on 2011-06-26
no, ffmpeg and mplayer can't do that alone as midi is not an audio file.

THat's the reson for using fluidynth. You need soemthing rto actually read the MIDI data and play it into music.

..on the other hand that would give you PCM audio, and that's where ffmpeg or kmplayer comes to play, they are able to encode the PCM audio from fluidynth into MP3 file.

I don't see anybody here claiming that ffmpeg would support MIDI, and the second link from ron999's post is for MIDI soundfonts. Having good soundfonts is essential for getting good audio from the MIDI file. Think of MIDI as sheet music, you still need a good player and instruments to convert it into audible music. Timidity is the player, and soundfonts are the instruments it uses.

---

### Post by andrew.46 on 2011-06-28
> **ron999 said:**
> My Linux version of VLC isn't compiled with fluidsynth support.

I suspect the problem with getting a repository version of vlc compiled to play midi is not so much fluidsynth but more so to do with getting a soundfont with a suitable license and then the sheer size of such a font bulking up the vlc package itself. But if you have followed the vlc compiling guide on these Forums you should be able to playback midi with your Linux vlc? If not I have some work to do :(.

---

