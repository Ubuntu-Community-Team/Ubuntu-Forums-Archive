---
title: "Audio Players"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by bgast1 on 2008-12-20
It's time to kick this around again. Not just for me but for anyone else new to Linux. I have used Amarok most of the time in the past. Rythmnbox comes default with Mint and Ubuntu. Why? Is it better? I wouldn't mind native iTunes in Linux, but I don't suppose that will happen anytime soon. Even in windows I couldn't decide which media player to use. 

What I am asking is for some of you to post your favorite players and why. If there is something better than Amarok then I am certainly willing to switch. Cover art is a must. I also liked how Amarok would give you information on the artist.

---

### Post by zvacet on 2008-12-20
Amarok is very good player,but if you want to try something else maybe you will be interested in [Songbird.]("https://help.ubuntu.com/community/Songbird")

---

### Post by OutOfReach on 2008-12-20
I like Banshee, but I use MPD+Sonata which might or might not be right for you.

I've also heard good things about Songbird 1.0, but I don't like the fact that it has a webbrowser built in too.

---

### Post by eriqjaffe on 2008-12-20
The main reason that Ubuntu comes with Rhythmbox is because it's a non-KDE app.

Personally, I like gmusicbrowser.  Handles a large library pretty well, and is fairly resource-light.  I tried Songbird and didn't really like it - especially how it ignored my Emerald theme.

---

### Post by Vakman on 2008-12-20
I love Banshee. My favourite music player ever.
I like Songbird as well but only use it if I am on Windows since Banshee is not available on Windows.
Banshee often downloads cover art automatically for me. Also works with the Ipod etc.
Last.fm is integrated, which I also love.
Try it out.

---

### Post by dwasifar on 2008-12-20
I've tried most of those and I keep coming back to Amarok.

I don't care much for the new Amarok 2.0 though.  I think the interface is better in 1.4, and various-artist discs are handled better.

---

### Post by sigurnjak on 2008-12-20
I think i have tried them all  amarok , exaile , banshee . songbird since version 0.2  and i keep coming back to rhytmbox .

---

### Post by nhasian on 2008-12-21
I must admit, I like Songbird quite a bit.  

[http://getsongbird.com/](http://getsongbird.com/)

In addition to album art, it also shows news about the artist, pictures, videos, etc.

I added the [Lyric Master]("http://addons.songbirdnest.com/addon/1230") plugin to give you the lyrics of the song playing as well as [Seeqpod]("http://addons.songbirdnest.com/addon/1267") so you can just enter any song you want to hear and viola it either plays it for you or downloads it to your library.

---

### Post by blairm on 2008-12-21
I've just cycled through half a dozen audio players in the past couple of weeks to see if I could find anything better than Rhythmbox, and for what it's worth here's my thoughts:

Amarok - Probably the best combination of reliability and features I've seen in Linux (Media Monkey in Windows might just have beat, but not by much).

Amarok 2 - Very promising and probably fine for people with collections of under 1000 tracks; at this stage some of the filtering features from the previous release have not been incorporated, making it harder to use with large collections.

Exaile - Again very promising: Like Amarok, it provides Wiki info on the artist, lyrics etc which I do like.

Rhythmbox - Boring. Ugly. But it's very stable, and it does grow on you - seems I keep going back to it despite the fact it lacks some of Amarok's features. Just wish they'd include an equalizer!

Blair

---

### Post by razy60 on 2008-12-21
rhythm box and the last.fm player(can be found in add/remove) fits all my needs and is stable, others that i have tried have all had problems.

Raz

---

### Post by Abu_Dayya on 2008-12-21
for me its Banshee. Just love it. And since the introduction of Banshee 1, ot has become a full blown media manager, rather than just an audio manager

---

### Post by northern lights on 2008-12-21
Threads like this often run the danger of multiple redundant posts. "For me it's this", "For me that" and "I use blah" without further explanation or reasons will in my opinion not aid in making an informed decision. If you really wonder what suits your needs, here's a decent article:

[www.pcworld.com - Linux Audio Players Tested and Graded]("http://www.pcworld.com/article/128636-3/linux_audio_players_tested_and_graded.html")

---

### Post by bgast1 on 2008-12-21
I installed Banshee 1.2.1, don't know if it is the latest or not. Noticed a couple of issues right of the bat. It downloads cover art ok, but it didn't on some of my albums. I don't know how to install cover art when it isn't downloaded.

The second issue is that it came up with errors on some of the DVD's that I ripped to my computer. Perhaps I don't know how to properly rip a DVD. Downloaded Video files work fine and installed into the library fine. 

Other than those 2 issues, Banshee is nice.

---

### Post by northern lights on 2008-12-21
> **bgast1 said:**
> The second issue is that it came up with errors on some of the DVD's that I ripped to my computer. Perhaps I don't know how to properly rip a DVD.
Ubuntu does not ship with DVD support out of the box. Does playback work? If it doesn't work either, you need to add the medibuntu repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/[COLOR="Red"]intrepid[/COLOR].list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs
```
Replace [COLOR="Red"]intrepid[/COLOR] by whatever version your on. The above adds DVD support as well as support for wma/wmv files.

---

### Post by stickman51 on 2008-12-21
Interesting discussion. Since Ubuntu comes with Rhythmbox, I figured I try it. I copied some MP3 files from a Windows machine to the Music folder in Ubuntu and double-clicked one to play it. Hmmmm; not that easy. It told me I needed codecs. So I followed the prompts and installed a codec. Double-clicking an MP3 in the Music folder opened Totem Movie Player but the music still did not play. The player looked like it was playing the MP3 which showed under "Playlist." All I could hear was static. When I opened Rhythmbox and tried to drag/drop an MP3 into that, I could not. Instead, I clicked "Music" and then "Import folder" and brought in all the tunes, but they would not play; just a lot of horrible static. If I play tunes in Windows on that machine, no problem. Can someone tell from all that where I messed up?

---

### Post by northern lights on 2008-12-21
You need the meta-package ubuntu-restricted-extras for mp3 support. If you haven't installed it already, run ```
sudo apt-get install ubuntu-restricted-extras
```

Check *alsamixer* and adjust volume. Make sure the line-out isn't muted. If the package is installed an neither VLC, totem or Rhythmbox play an mp3 you know is not corrupted, report back.

---

### Post by waspbr on 2008-12-21
I have tried all the other players mentioned here and I seem to have stuck with banshee, before I used songbird a lot more, but some features are still missing and it does seems a little heavy. 

banshee however seems very frugal, it integrates well with my gtk theme, keyboard commands work fine.  

I like it, in fact I am listening to music with it right now.

---

### Post by bgast1 on 2008-12-21
I am currently using Mint. DVD's play fine. What I was talking about was a Banshee issue. I can play all of the DVD's that I ripped to my computer as well with Totem. I was trying to get them to import into the Banshee Video Library. Only downloaded videos import correctly, not the ones I ripped to my computer (used windows for that).

Also, how do you get covers that aren't found by the standard cover download with Banshee. I fix that in Amarok easily. 

I am trying to give Banshee a fair shot. 

Rythmnbox is boring, but works good. 

Amarok is nice but haven't figured out how to configure it very well yet. I just use it. I have changed some colors but are there skins?

---

### Post by sigurnjak on 2008-12-21
Here , rhytmbox EQ :
[http://www.deviantdark.altervista.org/?p=438](http://www.deviantdark.altervista.org/?p=438)    :guitar:

---

### Post by stickman51 on 2008-12-21
> **northern lights said:**
> You need the meta-package ubuntu-restricted-extras for mp3 support. If you haven't installed it already, run ```
sudo apt-get install ubuntu-restricted-extras
```

Check *alsamixer* and adjust volume. Make sure the line-out isn't muted. If the package is installed an neither VLC, totem or Rhythmbox play an mp3 you know is not corrupted, report back.

Thanks, NL, I did that but don't see any "alsamixer" and Line-out so I still hear nothing.

---

### Post by northern lights on 2008-12-21
> **stickman51 said:**
> Thanks, NL, I did that but don't see any "alsamixer" and Line-out so I still hear nothing.
You've also got to run it from a terminal```
alsamixer
```

---

### Post by stickman51 on 2008-12-22
> **northern lights said:**
> You've also got to run it from a terminal```
alsamixer
```

OK, NL, I entered that at the prompt and got a black box with orange and blue text, and a "red/green/white" vertical bar with "100<>100" and "<Master>" below it. What should I do there?

---

