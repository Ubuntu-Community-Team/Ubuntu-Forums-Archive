---
title: "[SOLVED] recording a streaming playlist?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-12-17
Hi there

I have found a website - [www.basic.ch](www.basic.ch) - which is full of great music, the problem is i want to download it, but the media is streamed. I have read a few other threads and none seem to deal with the same issue. I tried Audacity, and it told me that the file was a link to a playlist and it could not record it. 

So from what i can gather - the small file i download is a link to a playlist - and nothing i have used has been able to record it.

Any ideas?

cheers

---

### Post by phantomjoker on 2008-12-17
i just read about -dumpstream  using mplayer - i dont understand it? has anyone used it?

---

### Post by andrew.46 on 2008-12-17
Hi Phantomjoker,

There are a lot of streams on that site so I have picked a ram file to demonstrate with MPlayer as this is one of the easy ones :-). Try saving this one offline as follows:

```
$ mplayer -cache 1024 -playlist http://www.basic.ch/ram/mill030109.ram \
          -vc null -vo null -ao pcm:fast:waveheader:file=offline.wav
```

This is ***one*** commandline, not 2. This will save the broadcast as a rather large wave file which you can then convert to mp3 or ogg vorbis as you desire.

For ogg vorbis you could try something like:

```
$ oggenc -q 6 offline.wav -o my_newfile.ogg 
```

while for mp3 you could try something like:

```
$ lame --preset standard offline.wav newfile.mp3 
```

To encode with oggenc you will need the vorbistools package and for lame you will need lame :-). Easy tagging can also be done with a program called, strangely enough, Easytag.


All the best,

  Andrew

---

### Post by phantomjoker on 2008-12-17
thank you! it is doing it now - and will report back with the results. Also - where will it save the file? and under what name? cheers

---

### Post by phantomjoker on 2008-12-17
it has worked!

But i can only do this to .ram file - how do i do this to .pls files [playlist i assume]

cheers

---

### Post by andrew.46 on 2008-12-17
Hi,

> **phantomjoker said:**
> thank you! it is doing it now - and will report back with the results. Also - where will it save the file? and under what name? cheers

The file will be saved to your present working directory, so if you simply open a Terminal window it will most like be $HOME. So you don't lose your downloaded file you can always change to your Desktop first:

```
$ cd $HOME/Desktop
```

and then run the command. The filename in the example I gave is offline.wav but you can of course call it whatever you want.

All the best,

  Andrew

---

### Post by phantomjoker on 2008-12-17
ok, so i just did the same code as you, but changed the http.

```
mplayer -cache 1024 -playlist http://live.basic.ch/ram/murd050105.ram \   
-vc null -vo null -ao pcm:fast:waveheader:file=offline.wav
```

and rather than taking 5 seconds like the first, this one is recording at actual speed, and playing it back to me at the same time - music is playing from the terminal! 

very confused!

---

### Post by Dr Small on 2008-12-17
You can also stream right through VLC. It's rather simple. Select your file to play, and then setup the stream options.

---

### Post by phantomjoker on 2008-12-17
vlc streaming went mental - but i got the other method working... shame i cant record .pls files though.

---

### Post by andrew.46 on 2008-12-17
Hi phantomjoker,

> **phantomjoker said:**
> 

and rather than taking 5 seconds like the first, this one is recording at actual speed, and playing it back to me at the same time - music is playing from the terminal! 

Actually the file should be recoding in real time and you would *not* normally hear the file playing unless you have opened another copy of MPlayer and were using this to play the stream.

As regards the .pls files I have a sneaking feeling that there may be a server problem at their end. If you download any of the .pls files using wget and open them with a text editor the message is:

> ICY 404 Resource Not Found
icy-notice1:<BR>SHOUTcast Distributed Network Audio Server/Linux v1.9.5<BR>
icy-notice2:The resource requested was not found<BR>

Looks like a remote error but I am always ready to be corrected :-). Seems to plenty of .ram files to experiment with for the moment anyway.

Andrew

---

### Post by phantomjoker on 2008-12-20
well i got it working with the .ram files and the download at about 30mins per second.... not real time! I'm not sure why. Anyway - yes after testing i too have not had any joy with .pls

cheers

---

### Post by andrew.46 on 2008-12-20
Hi phantomjoker,

> **phantomjoker said:**
> So from what i can gather - the small file i download is a link to a playlist - and nothing i have used has been able to record it.


I confess myself completely stumped so I have posted to the MPlayer-users:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-December/075446.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-December/075446.html)

Hopefully an answer might come from here.

Andrew

---

### Post by iheartubuntu on 2009-03-10
Andrew, MANY thanks for posting this. I've tried this out and have a few questions...

How do we save a file after running the command line? Do we just close the terminal? Ive done this a few times with different feeds. Ive only been successful so far with an .ASX stream here...

[http://s7.viastreaming.net/7610/listen.asx](http://s7.viastreaming.net/7610/listen.asx)

(its polka music) I recorded about 10 minutes of it then close the terminal. In my directory was the offline.wav file. But if I try it again, say for a minute or two it wont save an offline.wav file.

Ive also tried it for about 5 minutes with a good classical station here...

[http://www.kusc.org/streams/kusc96.m3u](http://www.kusc.org/streams/kusc96.m3u)

But again, no offline.wav file. Would you happen to know why? Is there any documentation about recording streams like this I can read up on and understand? Id like to make some classical and some polka CDs for my dad (ok, and myself too!) since he isnt too tech savvy to hook up a laptop to a stereo and listen live.

Thanks for any help!


> **andrew.46 said:**
> Hi Phantomjoker,

There are a lot of streams on that site so I have picked a ram file to demonstrate with MPlayer as this is one of the easy ones :-). Try saving this one offline as follows:

```
$ mplayer -cache 1024 -playlist http://www.basic.ch/ram/mill030109.ram \
          -vc null -vo null -ao pcm:fast:waveheader:file=offline.wav
```

This is ***one*** commandline, not 2. This will save the broadcast as a rather large wave file which you can then convert to mp3 or ogg vorbis as you desire.

For ogg vorbis you could try something like:

```
$ oggenc -q 6 offline.wav -o my_newfile.ogg 
```

while for mp3 you could try something like:

```
$ lame --preset standard offline.wav newfile.mp3 
```

To encode with oggenc you will need the vorbistools package and for lame you will need lame :-). Easy tagging can also be done with a program called, strangely enough, Easytag.


All the best,

  Andrew

---

### Post by andrew.46 on 2009-03-11
Hi shirteesdotnet,

> **shirteesdotnet said:**
> Andrew, MANY thanks for posting this. I've tried this out and have a few questions...

How do we save a file after running the command line? Do we just close the terminal? 

The full commandline actually writes the file in real time so I guess it is more a question of how to *stop* recording the file. There are a couple of different ways of doing this varying from simply using the Control + C key to terminate the MPlayer process to deciding beforehand how much of the stream you wish to record. So for the polka station you could record 2 minutes as follows by using -endpos:


```
$ mplayer -cache 1024 -playlist [http://s7.viastreaming.net/7610/listen.asx](http://s7.viastreaming.net/7610/listen.asx) **[COLOR="Red"]-endpos 02:00[/COLOR]** \
          -vc null -vo null -ao pcm:fast:waveheader:file=offline.wav
```

This will not work with all streams but certainly works with this particular one.

> Ive done this a few times with different feeds. Ive only been successful so far with an .ASX stream here...

[http://s7.viastreaming.net/7610/listen.asx](http://s7.viastreaming.net/7610/listen.asx)

(its polka music) I recorded about 10 minutes of it then close the terminal. In my directory was the offline.wav file. But if I try it again, say for a minute or two it wont save an offline.wav file.

I am not sure what the problem is here as I cannot duplicate this. Be aware that if you do not vary the output filename the file will be overwritten.

> Ive also tried it for about 5 minutes with a good classical station here...

[http://www.kusc.org/streams/kusc96.m3u](http://www.kusc.org/streams/kusc96.m3u)

But again, no offline.wav file. Would you happen to know why?

I tested the stream and had no problem saving the file. I place the full output below. You will see at the base where I terminate the MPlayer process with Control + C:

```

andrew@skamandros~/Desktop$ mplayer -cache 1024 http://www.kusc.org/streams/kusc96.m3u \
>           -vc null -vo null -ao pcm:fast:waveheader:file=test.wav
MPlayer SVN-r28876-4.2.4 (C) 2000-2009 MPlayer Team

Playing http://www.kusc.org/streams/kusc96.m3u.
Resolving www.kusc.org for AF_INET6...
Couldn't resolve name for AF_INET6: www.kusc.org
Resolving www.kusc.org for AF_INET...
Connecting to server www.kusc.org[207.155.248.31]: 80...
Cache size set to 1024 KBytes


Playing http://68.181.156.19:8000/kuscaudio96.mp3.
Resolving 68.181.156.19 for AF_INET6...
Couldn't resolve name for AF_INET6: 68.181.156.19
Connecting to server 68.181.156.19[68.181.156.19]: 8000...
Name   : KUSC-fm
Genre  : Classical
Website: http://www.kusc.org/new/index.php
Public : yes
Bitrate: 96kbit/s
Cache size set to 1024 KBytes
Cache fill:  0.78% (8192 bytes)   
ICY Info: StreamTitle='Leonard Bernstein - Mass';
Cache fill: 19.53% (204800 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 329 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 96.0 kbit/6.80% (ratio: 12000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO PCM] File: test.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mpg123: Can't rewind stream by 199 bits!
A:  45.7 (45.7) of -0.0 (unknown) 61.0% 0% 

MPlayer interrupted by signal 2 in module: decode_audio


MPlayer interrupted by signal 2 in module: enable_cache
A:  46.1 (46.1) of -0.0 (unknown) 62.1% 0% 
Exiting... (Quit)

```

> Is there any documentation about recording streams like this I can read up on and understand? Id like to make some classical and some polka CDs for my dad (ok, and myself too!) since he isnt too tech savvy to hook up a laptop to a stereo and listen live.

Unfortunately there is very little documentation available concerning recording radio streams, in part because I believe the radio stations themselves are not all that keen for their streams to be recorded :-). MPlayer is not the only option of course, I believe vlc works well and a lot of people speak of StreamRipper which I have not tried. For scripting such a recording there is always ['For the God Who Sings']("http://www.andrews-corner.org/ftgws.html") which has always worked well for me :-). 

Perhaps when you build up some expertise you could write some of the documentation yourself? This would fill a pretty big gap.

Andrew

---

