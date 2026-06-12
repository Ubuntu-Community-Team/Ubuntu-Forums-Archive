---
title: "Cannot play Radio Stream..."
date: 2010-04-24
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-04-24
For the last ten minutes I've been trying to play a radio stream in Linux Mint 8 KDE CE (Kubuntu 9.10 'Karmic Koala') however it just won't play:confused:

I've tried it in both VLC and MPlayer and Neither work...

with MPlayer I get the following error:

```
mplayer -playlist http://mediaweb.musicradio.com/Playlist.asx?StreamID=158
Resolving mediaweb.musicradio.com for AF_INET...                                                
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...                               
Resolving mediaweb.musicradio.com for AF_INET...                                                
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...                               
STREAM_ASF, URL: http://mediaweb.musicradio.com/Playlist.asx?StreamID=158                       
Resolving mediaweb.musicradio.com for AF_INET...                                                
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...                               
Server returned 302:Redirect                                                                    
Failed to parse header.                                                                         
Failed, exiting.                                                                                
Resolving mediaweb.musicradio.com for AF_INET...                                                
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...                               
Resolving mediaweb.musicradio.com for AF_INET...                                                
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...                               
Cache size set to 320 KBytes                                                                    
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team                                             
mplayer: could not connect to socket                                                            
mplayer: No such file or directory                                                              
Failed to open LIRC support. You will not be able to use your remote control.                   

Playing http://mediaweb.musicradio.com/<font face="Arial" size=2>.
Resolving mediaweb.musicradio.com for AF_INET...                  
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80... 
Server returned 404: Not Found                                    
STREAM_ASF, URL: http://mediaweb.musicradio.com/<font face="Arial" size=2>
Resolving mediaweb.musicradio.com for AF_INET...                          
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...         
Server returned 404:Not Found                                             
Failed to parse header.                                                   
Failed, exiting.                                                          
Resolving mediaweb.musicradio.com for AF_INET...                          
Connecting to server mediaweb.musicradio.com[81.20.48.115]: 80...         
Server returned 404: Not Found                                            
No stream found to handle url http://mediaweb.musicradio.com/<font face="Arial" size=2>

```

Radio Stream is:
[http://mediaweb.musicradio.com/Playlist.asx?StreamID=158](http://mediaweb.musicradio.com/Playlist.asx?StreamID=158)

it is the Galaxy South Coast Radio station (United Kingdom)

---

### Post by HermanAB on 2010-04-24
Try Streamtuner and Streamripper.

I use streamtuner together with xmms for playback.  It is configurable somewhere in a menu.

---

### Post by kamitsukai on 2010-04-24
> **HermanAB said:**
> Try Streamtuner and Streamripper.

I use streamtuner together with xmms for playback.  It is configurable somewhere in a menu.

Not to be rude but that's completely pointless and doesn't solve the problem](*,)

Galaxy South Coast isn't even listed in Streamtuner...

---

### Post by arochester on 2010-04-24
Try going here: [http://radiotime.com/Search.aspx?query=Galaxy+south+coast](http://radiotime.com/Search.aspx?query=Galaxy+south+coast)

and clicking: "Listen"

---

### Post by kamitsukai on 2010-04-24
> **arochester said:**
> Try going here: [http://radiotime.com/Search.aspx?query=Galaxy+south+coast](http://radiotime.com/Search.aspx?query=Galaxy+south+coast)

and clicking: "Listen"

Works with there player but trying to use mplayer still produces the same errors...

even after compiling the latest svn :(

---

### Post by yetiman64 on 2010-04-24
Hi, kamitsukai, I tried your stream posted earlier with vlc, mplayer, streamtuner to xmms with absolutely no luck at all.

However in looking around I found a stream to Galaxy South Coast (hope it's the same station you're after) using 

> [http://media-ice.musicradio.com/GalaxySouthCoast.m3u](http://media-ice.musicradio.com/GalaxySouthCoast.m3u)pasted into streamtuner (with vlc only - it didn't work with xmms for me), and also tried successfully with vlc directly (however mplayer failed again, even with this one).

Btw, I've been tuned in and listening to Galaxy from Australia with the above link which has me wondering if it is what you're looking for. Hope it is and good luck.

Also don't click directly on the link and try opening in your browser with vlc etc - it just gives an error, try pasting the link into vlc > Media > Open Network, set to http and paste in the full link above.

---

### Post by kamitsukai on 2010-04-24
Thanks for the link, arochester also posted a working stream so I've got a few to choose from =] I'm still interested in getting mplayer to work though!:lolflag:

***Edit***

I got it to work!!! [yetiman64]("http://ubuntuforums.org/member.php?u=1043255")'s stream works if I use the command below:

```
mplayer -playlist http://media-ice.musicradio.com/GalaxySouthCoast.m3u

```

Still I wonder why the original stream from the galaxy site refuses to work?

---

### Post by tgalati4 on 2010-04-24
I read in another thread that there is a bug in a recent codec update that causes wma2 streams to crap out.  It should be fixed shortly.  The work around seems to be either a rollback of the codec update or use the playlist method.

---

### Post by yetiman64 on 2010-04-24
> **kamitsukai said:**
> 

```
mplayer -playlist http://media-ice.musicradio.com/GalaxySouthCoast.m3u

```

:redface: Yep the playlist option has this working in mplayer for me now too, thanks kamitsukai, as I definitely prefer to use mplayer. Bye.

---

