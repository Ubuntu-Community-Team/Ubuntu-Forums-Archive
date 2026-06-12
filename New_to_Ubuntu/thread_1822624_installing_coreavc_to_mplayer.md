---
title: "installing coreavc to mplayer"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by genericman on 2011-08-10
I've been following this guide ([http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)) to installing coreavc on my 11.04 ubuntu netbook.  So far, the guide has been pretty spectacular, but I've hit my first and my only major roadblock: cd <path to mplayer source code>
[LEFT][FONT=Verdana]I have no clue as to where I'd find that path...I installed mplayer a while ago while trying to find a suitable video player to play HD content.  I did this by opening terminal and using sudo apt-get mplayer.[/FONT]  [FONT=Verdana]Later, I went on to download smplayer using ubuntu software center.  The path confuses me as I'm not sure if it's something like /etc/mplayer/mplayer.config, menu.config, or something else entirely.[/FONT]  I also tried following a couple other guides I found after that block, but the information is either cryptic, outdated, guide in a guide in a guide that doesn't explain any of the steps when compiled, or something that forces you to download 30 more programs, and then follow another guide that does the same thing but with different programs.

[FONT=Verdana]Basically, if someone can explain in very basic lingo as to how I'd find this, or what I need to do, please assist.[/FONT]  [FONT=Verdana]I wouldn't be against [/FONT]just calling it a loss, and just installing coreavc to my windows 7 partition and watching videos there, but I also am trying to get a similar setup for my ps3 running 10.04 ubuntu.  At this point, I'm so close, that quitting seems silly.
[/LEFT]

---

### Post by jtarin on 2011-08-10
[Did you know Mplayer claims to already support H.264 video decoding?]("http://www.mplayerhq.hu/design7/news.html")

You can find the Mplayer source code at that link if you still want to compile Mplayer.

---

### Post by genericman on 2011-08-11
Yea, I noticed that mplayer supported HD...I read somewhere that coreavc would allow for HD content to be played without hiccups on a netbook though.  That claim turned out to be false.  Broke down and installed it on the windows partition, and ran it through windows media player classic HD with all the plugins linked to coreavc and I couldn´t notice a difference.  Tried installing WinFF on my ps3 to at least convert the videos over to something a bit more manageable.  That was over 4 hours ago, and it&#347; still trying to do the first video >.>;

I forgot all about .mkv and subtitles being the most obnoxious situation to deal with when converting files, and it would appear that neither WinFF, nor Arista Transcoder can properly convert files in such a light cpu setting.  I tried Arista on my netbook while the ps3 was working on it&#347; first, and the outcome was extremely jumpy, majorly pixelated, and of course minus any subtitles...I probably should have just gave up a long time ago, and torrented something else.

---

