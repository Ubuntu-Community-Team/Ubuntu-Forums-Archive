---
title: "Which is the best video player for ubuntu"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Alanbuntu on 2009-11-13
hi i have been using media player classic in windows because it supports almost all formats of video files

however when i use ubuntu 9.10, the mplayer always does not the file formats try to read (no matter it is avi, dat, flv, mpeg...etc) and always pops up a window to ask me to download something.

could anyone recommend me the video player which can support as many as video formats please , thank you

---

### Post by masux594 on 2009-11-13
In mi opinion, VLC .. it's so powerful..

Sysc, A

---

### Post by scorp123 on 2009-11-13
> **Alanbuntu said:**
>  could anyone recommend me the video player which can support as many as video formats please On Linux all video players support all formats ... if they are installed.

Guessing from what you write I'd say you're missing all the codecs that Ubuntu doesn't ship with for licensing and software patent reasons.

Read here:
[https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once you have the codec packages choosing a video player is just a matter of taste, as far as their capabilities go they should all be equal as they are relying on the same codec packages.

---

### Post by scorp123 on 2009-11-13
> **masux594 said:**
> In mi opinion, VLC .. it's so powerful.. VLC won't help you one little bit if the codec packages are missing ...

---

### Post by t0p on 2009-11-13
+1 for vlc.  It's my fave.

But you can make (just about) any media player play (just about) any media file by installing the package **ubuntu-restricted-extras**.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by grandtoubab on 2009-11-13
+1 for VLC

very useful for commercial DVD too even if on hard disk, thanks torrent:lolflag:

in Karmic you will find VLC and all in Synaptic

System -> Management ->...Synaptic

---

### Post by coldReactive on 2009-11-13
Totem here

Using this: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

but skipping mplayer and vlc installs.

---

### Post by ikt on 2009-11-13
> **Alanbuntu said:**
> 
however when i use ubuntu 9.10, the mplayer always does not the file formats try to read (no matter it is avi, dat, flv, mpeg...etc) and always pops up a window to ask me to download something.

I wonder if the thing popping up would be mplayer asking for you to download the correct codecs so it can play the media.

---

### Post by ukripper on 2009-11-13
VLC all the way..

---

### Post by andrew.46 on 2009-11-13
Hi Alanbuntu,

> **Alanbuntu said:**
> however when i use ubuntu 9.10, the mplayer always does not the file formats try to read (no matter it is avi, dat, flv, mpeg...etc) and always pops up a window to ask me to download something

I suspect you are referring to the Totem Movie Player rather than MPlayer itself? A fully configured MPlayer is actually the* best* for playing all media files that you can throw at it but to get this it is arguably best to compile the code from source. If this seems like too much of a pain there is always vlc which is a nice package that is also very capable.

All the best,

Andrew

---

### Post by coldReactive on 2009-11-13
Just wondering why people think totem isn't capable at all. :|

I find it very capable after going through the media guide howto. It can play DVDs well, even full screen, etc.

---

### Post by NickJones on 2009-11-13
VLC is by far my favourite.

---

### Post by ubudog on 2009-11-13
Totem.

---

### Post by pedja_portugalac on 2009-11-13
nogui mplayer from svn is definitely the best media player in my opinion. ;)

---

### Post by SuperSonic4 on 2009-11-13
Compiled mplayer is the best I've seen by a long way. I add the smplayer front end

---

### Post by andrew.46 on 2009-11-13
Hi SuperSonic4,

> **SuperSonic4 said:**
> Compiled mplayer is the best I've seen by a long way. I add the smplayer front end

I would have to agree with you there, I believe there is a guide somewhere on these forums that spells out in *excruciating* detail how to compile the svn MPlayer for Karmic and add in the most recent SMPlayer from the developer's PPA..... :).

Andrew

---

### Post by durand on 2009-11-13
My favourite is Totem, which is the default one in ubuntu. As long as you install [apt:ubuntu-restricted-extras]("apt:ubuntu-restricted-extras"), pretty much any media player you use will support most files (except for ugly drm encrypted ones..)

---

### Post by Iksf on 2009-11-13
VLC with restricted codeks is by far the best in my opinion, powerful, easy to use, system resource friendly. Only things that matter

---

### Post by pedja_portugalac on 2009-11-13
> **coldReactive said:**
> Just wondering why people think totem isn't capable at all. :|

I find it very capable after going through the media guide howto. It can play DVDs well, even full screen, etc.
Full screen? No joke? :D 

It all depend of someones needs and expectations. Totem compared to mplayer is like albanian soccer team compared to brasilian seleção. :D

---

### Post by wizardfingers on 2009-11-13
I agree +1 VLC even though I would never use it on Windows.

---

### Post by durand on 2009-11-13
> **pedja_portugalac said:**
> Full screen? No joke? :D 

It all depend of someones needs and expectations. Totem compared to mplayer is like albanian soccer team compared to brasilian seleção. :D

I use both totem and mplayer on a daily basis. I prefer to use mplayer in gentoo but when I go on ubuntu, I find totem to be nicer. Unless you need advanced features, totem suits the majority of users.

I have no idea why people like vlc so much. I mean, it's a great player but it doesn't do much more than mplayer or similar players and it certainly doesn't look that nice.

---

### Post by nitstorm on 2009-11-13
i prefer the regular movie player, if the sound is too low then vlc, otherwise movie player works jus fine for me...

---

### Post by coldReactive on 2009-11-13
> **durand said:**
> I have no idea why people like vlc so much. I mean, it's a great player but it doesn't do much more than mplayer or similar players and it certainly doesn't look that nice.

Seriously.

Maybe because so many windows users use it?

---

### Post by durand on 2009-11-13
> **coldReactive said:**
> Seriously.

Maybe because so many windows users use it?

I guess its familiar territory but if someone doesn't mind trying something new, we could just suggest a native linux player. When I say this, it feels like I'm anti-vlc, I'm not. I just don't see what the fuss is about.

---

### Post by pedja_portugalac on 2009-11-13
> **coldReactive said:**
> Seriously.

Maybe because so many windows users use it?
And mac users use it to. :D 

Do you know what's the player called 123 or media player in windows world? It comes with cccp codecs pack? 

It's a derivate of mplayer. :D

---

### Post by coldReactive on 2009-11-13
> **pedja_portugalac said:**
> And mac users use it to. :D 

Do you know what's the player called 123 or media player in windows world? It comes with cccp codecs pack? 

It's a derivate of mplayer. :D

media player classic is a derivative of Windows Media Player 5 and earlier.

---

### Post by pedja_portugalac on 2009-11-13
Maybe I am wrong, it's long time away from windows. ;)

---

### Post by scorp123 on 2009-11-15
> **coldReactive said:**
> media player classic is a derivative of Windows Media Player 5 and earlier. "mplayer" and Microsoft's "Media Player" are not the same. Just to make sure we have no misunderstanding here.

"mplayer" homepage:
[http://www.mplayerhq.hu](http://www.mplayerhq.hu)

I still remember the times when us Linux users had to compile "mplayer" by hand because none of the major distros dared to distribute it yet .... 

Only after the "mplayer" project separated the codecs into separate packages the "mplayer" started showing up in all the major distros. Now it's more or less installed per default on almost every Linux distro.

And what Pedja meant to say is that even in the Windows world there are video players that are based on "mplayer" -- a Linux project.

---

### Post by Alanbuntu on 2009-11-22
thank you all of you very much. the problem was solved.

---

### Post by Arup on 2009-11-22
My vote is for Mplayer compiled with excellent instructions from andrew.46 who has posted above, if you have nvidia 8400 and above, you get added benefit of VDPAU. Mplayer is best when combined with SMPlayer. Even the built in Ubuntu Mplayer will play everything, make sure you install w32codecs or w64codecs depending on your architecture. After mplayer, VLC is true jack or trades and it comes with its own codecs, no need for external gstream packs.

---

### Post by frenchn00b on 2009-11-22
> **Alanbuntu said:**
> hi i have been using media player classic in windows because it supports almost all formats of video files

however when i use ubuntu 9.10, the mplayer always does not the file formats try to read (no matter it is avi, dat, flv, mpeg...etc) and always pops up a window to ask me to download something.

could anyone recommend me the video player which can support as many as video formats please , thank you

mplayer

---

### Post by Cotopaxi on 2010-01-08
Ok guys, here goes my &#8220;how-to&#8221;, actually a summary, based on all your inputs from this thread. First of all, I want to thank you for your contributions, because watching videos and DVD is working fantastically now!:D :popcorn:

Step 1)
Install the files that give you access to all DVD formats.

Files to download: &#8220;libdvdnav4&#8221;, &#8220;libdvdread4&#8221;, &#8220;gstreamer0.10-plugins-bad&#8221;  and  &#8220;gstreamer0.10-plugins-ugly&#8221;. They are in the repositories.
Or, in terminal type:

> sudo apt-get install libdvdnav4

Afterwords you repeat the process for the other files.

In order to be able to view encrypted DVDs, type in terminal:

> sudo /usr/share/doc/libdvdread4/install-css.sh

A link, that explains it beautifully:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html)


Step 2)
Install the &#8220;ubuntu-restricted-extras&#8221; which are in the repositories.
Or, in the terminal type:

> Sudo apt-get install ubuntu-restricted-extras

A link that explains the whole process:

[https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.10/musicvideophotos/C/video-playback.html)


Step 3) (optional)
install VLC, a media player, which is doing a fantastic job!

In terminal type:

> sudo apt-get install vlc

---------

Again, Thanks to all of you for your inputs!!!:popcorn:

---

### Post by Lord Stig on 2010-01-08
> **durand said:**
> I use both totem and mplayer on a daily basis. I prefer to use mplayer in gentoo but when I go on ubuntu, I find totem to be nicer. Unless you need advanced features, totem suits the majority of users.

I have no idea why people like vlc so much. I mean, it's a great player but it doesn't do much more than mplayer or similar players and it certainly doesn't look that nice.
I like Mplayer but on my machine, if a video has any errors in it, MPlayer will do one, some or all of the following:
1) display a dialogue box telling me of the error(s). I don't want that, I want it to carry on playing as best it can like all the other video players I've used.
2) Sometimes the above dialogue boxes appear behind the video (e.g. in full screen I don't even know it's there). If that happens and I want to skip forward by pressing right arrow it doesn't work. I have to press Return to confirm the error I can't see and then press right arrow.
3) Sometimes the error will completely lock up the applicaton so it can't be closed by clicking the close button.

VLC just gets on with playing files and has never crashed on me. It also has codecs built in, although I admit it can be a little slow catching up when I click forward on the video progress bar, and I've yet to find keyboard shortcuts for fast forward/rewind in full screen mode. It's my preferred choice at the moment.

---

### Post by benfindlay on 2010-01-08
My personal preference is for VLC. It may be somewhat basic in its features, but it seems to play almost every file format that exists with little difficulty. It's low on system resource demands too I believe.

---

### Post by beegary on 2010-01-08
I use VLC and SMPlayer.
VLC is good for converting files, an opening pretty much anything.
SM Player is a bit mor eser friendly - it has preset keyboard shortcuts (modifyable) and will resume playback.

---

### Post by anaconda on 2010-01-08
I use 
Totem, vlc, kaffeine, (and sometimes mplayer)

Each is good for some things. eg. VLC can show subtitiles in formats, that totem or mplayer cant.

And some video formats can be difficult to fast-forward in some players, while some other player will load them flawlessly.

And TV-movies saved from kaffeine work best with kaffeine.. suprising...

---

### Post by dilantha on 2010-01-08
For me the best player is Mplayer..Most of the plugins are not coming with the default package because of the proprietary issues. But if you installed suitable plugins it supports every type of video format. Also im addicted to its short cut keys..:lolflag:

---

### Post by freak42 on 2010-01-08
> **scorp123 said:**
> VLC won't help you one little bit if the codec packages are missing ...

that is not correct, vlc is self contained with respects to codecs. so if you install vlc on any system (linux,mac,osx) it will always be able to play whatever format it supports anyhow.

---

