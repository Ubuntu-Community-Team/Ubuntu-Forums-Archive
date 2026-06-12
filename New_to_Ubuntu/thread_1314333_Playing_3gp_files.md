---
title: "Playing 3gp files"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by mvalviar on 2009-11-04
I have some 3gp files that I used to be able to play when I was in ubuntu JJ. Now I'm in ubuntu studio KK and I can't play them. I've installed all the non-free stuff already but I still can't play them. We'll they played after I installed codecs but without audio. What have gone wrong?

---

### Post by LunaticHiatus on 2009-11-04
I don't use studio but I am using KK and it will say searching for a codec for 3gp, codec not found but then it plays anyway.

---

### Post by empax on 2009-11-04
i have same problem.
9.04 x64

---

### Post by mvalviar on 2009-11-04
My mplayer displays a dialog saying. ```
Cannot find codec for audio format 0x726D6173
```It must mean something is wrong because the video plays with out audio. I used to be able to play these without problems when I'm with JJ. VLC, Totem is out of the question because I never got them to play 3gp files with audio at all even in JJ.

---

### Post by andrew.46 on 2009-11-04
Hi,

The Medibuntu MPlayer for Jaunty and previous had support for amr but Medibuntu no longer carries MPlayer. You can compile your own under Karmic with support for amr:

Howto: Utilise the svn MPlayer to Improve Karmic Koala's 'mplayer-nogui' Package
[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Andrew

---

### Post by mvalviar on 2009-11-04
So much work just to get those files playing. I there a way for me to convert them to an linux-playable format? Compiling from source is just not my thing.

---

### Post by SunnyRabbiera on 2009-11-04
Did you try VLC?

---

### Post by Ant59 on 2009-11-04
VLC will play your 3GP video :) I tried it only yesterday.

---

### Post by andrew.46 on 2009-11-04
Hi Ant59,

> **Ant59 said:**
> VLC will play your 3GP video :) I tried it only yesterday.

3gp files come with a small range of codecs and for sound there can be aac or amr audio. Usually the problem that comes up is with the amr sound which vlc also fails with unless it is using a copy of FFmpeg that has had amr supporrt compiled in and this is not the case with standard Ubuntu repository software. I have a sample 3gp video with h263 video and amr sound that you might be interested in trying with your copy of vlc to see whether this is also a problem with your copy:
```

wget http://www.andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

Karmic Koala has an added problem with amr as Medibuntu no longer carries a copy of MPlayer with amr playback enabled as it has for previous Ubuntu versions. BTW this means that Jaunty users can still get amr playback with the Medibuntu MPlayer. The remaining option for Karmic users is to build your own package although I have heard that RealPlayer has amr support, I have not tested this however.

All the best,

Andrew

---

### Post by aloisam on 2009-11-05
> **mvalviar said:**
> So much work just to get those files playing. I there a way for me to convert them to an linux-playable format? Compiling from source is just not my thing.

if you want to convert amr in Ubuntu, try this:
[http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)

but i dont understand why there isn't  compiled version of ffmpeg in medibuntu repository as it was till Interpid.. with it, even Totem was able to play amr..

---

### Post by mvalviar on 2009-11-05
Would it be possible to revert back to an mplayer version with support for amr?

---

### Post by andrew.46 on 2009-11-05
Hi mvalviar,

> **mvalviar said:**
> Would it be possible to revert back to an mplayer version with support for amr?

I suspect not as MPlayer would be calling for a host of older libraries, it would become quite messy. However if you are not keen to compile against the new opencore-amr libraries I believe that there is an MPlayer PPA run by RVM, the developer of SMPlayer that has amr support.

But can I clarify if you are running Karmic or Jaunty? Your profile says Jaunty which means you can download the Medibuntu MPLayer and get full support for amr. For Karmic RVM's MPlayer might well be the answer.

Andrew

---

### Post by rvm4000 on 2009-11-05
The mplayer packages from this PPA have been compiled with amr support:

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

---

### Post by andrew.46 on 2009-11-05
Hi rvm,

> **rvm4000 said:**
> The mplayer packages from this PPA have been compiled with amr support:

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

Thanks for that clarification.

Andrew

---

### Post by mvalviar on 2009-11-06
Haven't updated my profile yet. I'm on ubuntu studion KK. I there a repo I can add to my sources.list so I can install mplayer with amr support. I already DLed the converter but it still think its better to have a player that can play 3gps. 

...rvm already mentioned that. I'll give it a try.

---

### Post by mvalviar on 2009-11-06
Gave it a try. It won't do. I'm getting the pop up.```
[AO_ALSA}Unable to find simple control 'PCM'0.
```

It keeps on popping up over on over. We'll I guess if it isn't stable it really isn't.

---

### Post by andrew.46 on 2009-11-06
Hi mvalviar,

> **mvalviar said:**
> ```
[AO_ALSA}Unable to find simple control 'PCM'0.
```

I cannot speak for rvm's build itself but if alsa is giving trouble you could try:

```
mplayer *[COLOR="Red"]-ao pulse[/COLOR]* myfile.3gp
```

The various audio-out options available to you can be seen by running:

```
mplayer -ao help
```

from the commandline. If you are not really a commandline sort of person you could always install SMPlayer and try these options from a more comfortable gui :).

Andrew

---

### Post by rvm4000 on 2009-11-06
> **mvalviar said:**
> Gave it a try. It won't do. I'm getting the pop up.```
[AO_ALSA}Unable to find simple control 'PCM'0.
```

Try adding the option *-mixer-channel Master*

> **mvalviar said:**
> It keeps on popping up over on over. We'll I guess if it isn't stable it really isn't.

The problem is that gmplayer pops up a window every time there's a warning from mplayer. I suggest you to use smplayer instead, it won't bother you with those warnings.

---

### Post by Spiritof76 on 2009-11-14
After some frustration with not being able to see the blackberry videos sent to me I now can hear as well as see the movies my niece sends of her babies,  Thanks RVM4000 I was about to reinstall jaunty to just to hear these short videos,  I'm sure glad I stumbled accross this thread.  

Thanks so much ..

---

### Post by Yorkan on 2010-06-04
please visit the 3gp player official website, where you can find alot of information about how to play 3gp video files on your ubunto OS.

the 3gp player website url is: [http://www.3gp-player.com](http://www.3gp-player.com)

---

### Post by pjman on 2010-07-22
> **rvm4000 said:**
> The mplayer packages from this PPA have been compiled with amr support:

[https://launchpad.net/~rvm/+archive/testing](https://launchpad.net/~rvm/+archive/testing)

rvm,

It looks like your PPA was updated for 10.04 but I can't seem to get it to work. I get no video or audio when playing 3gp files. Any suggestions?

Thanks!

---

### Post by rvm4000 on 2010-07-23
Paste here the output from mplayer.

---

