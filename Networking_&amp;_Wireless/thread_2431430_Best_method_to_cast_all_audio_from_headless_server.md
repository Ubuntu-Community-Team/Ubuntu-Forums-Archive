---
title: "Best method to cast all audio from headless server"
date: 2019-11-16
forum: Networking &amp; Wireless
---

### Post by scales2 on 2019-11-16
Hello,

My goal is to be able to stream music from my local library on my headless computer to the several chromecast audio devices I have scattered throughout my house.  My initial idea has been to run MPD on the server, use ympd to change/control the audio tracks, and have the PC default stream to a specific device (or the group of devices).  I have managed to get this setup working by using pulseaudio-dlna.  My steps are as follows:
-ensure that the MPD service is running
-remote into the computer via ssh
-run the command pulseaudio-dlna --filter-device DeviceName
-open a web browser on a networked computer
-navigate to ympd and play music

The trouble I am having, is that there is a >20 seconds of lag between me pressing play/skip/etc and the music actually responding.

Can anyone offer a better solution that keeps the source headless?  I would like to keep my PC in the basement while I control the music from another room in my house via tablet.

Thanks,

---

### Post by scales2 on 2019-11-20
Any advice?

---

### Post by CatKiller on 2019-11-20
I use volumio on a Raspberry Pi for local playback - the music is on a NAS and played through speakers attached to the Pi - and I understand that it can also act as a DLNA source although it's not something I've played with. It's lightweight and fairly responsive on my Pi, and automatically starts mpd at boot and offers control through any web browser. It's possible that would work for you with lower latency and less hassle than what you're using.

---

### Post by TheFu on 2019-11-20
If you use DLNA, then any _server_ can connect to any _renderer_ and be controlled by any _controller_. I have no clue how to use multiple renderers concurrently.  The server, renderer and controller can all be on 1 machine, if you like.

I routinely use Plex as the DLNA server, an android device (both tablet and phones) as the controller (bubbleUPnP) and raspberry pis running kodi/OSMC as the renderers.  Can't think of a reason why miniDLNA couldn't work as the DLNA server.  Plex is a headless server with a web interface.  I use that web interface when I'm away from home through a ssh-socks proxy to listen and watch my content.  No paid plex-pass needed. I don't like any of the official Plex clients. They aren't necessary.

I suppose a chromecast can be a renderer for specific content, but expect it to ignore lots of normal content because it is extremely limited. If all you have is CBR mp3, that should playback fine.  I couldn't get oga or flac audio to work and some VBR mp3s didn;t work.

---

### Post by scales2 on 2019-11-21
Thanks for the input Catkiller and TheFu.

I am familiar with Volumio (just recently started using it) and I have used miniDLNA before.  A DLNA server would be a great source, but the trouble is that Googles Chromecast devices (of which I have 6) dont easily work with DLNA...usually you need Plex or another device to cast to them?  Additionally, I want all the chromecast devices to be in sync when playing music.

I have avoided Plex in the past.  I don't have anything particularly against them, but I was weary of how it/they handle my data...ie what information are they collecting?  I am not opposed to giving it a try if it works.

---

### Post by TheFu on 2019-11-21
I completely understand NOT wanting to use non-FLOSS tools. 

I'm weary of Plex too!  Would much prefer a F/LOSS solution.  They do nag in subtle ways about having a Plex account and I suppose newer versions will nag about a paid plex pass.  I have neither, so any data that sneaks passed my outbound firewall restrictions doesn't have any identifier.

---

### Post by ajgreeny on 2019-11-21
I use a plexmediaserver for streaming music, videos and pictures to my Smart TV with no problems, but I also have minidlna running on a low powered laptop and that also works well on the TV and other client devices. For some reason that I never really managed to find a reason for I found enabling the dlna server in plex raised it's resource use hugely, occasionally bringing a previous machine almost to a halt, so I tried minidlna and that worked fine with low resource usage.

At all times I find that minidlna requires and uses much lower resources than plex, but it is not quite as user friendly, not having such a fully featured display on the client device.  It is still very easy to use once you have figured out the way it lists displays the media types, ie, pictures, video and music, separately on the clients.

Plex certainly does keep reminding you that you are not using plex-pass but it's not really nagging; they are, after all, a business trying to make some money, and so far at least the extras available with a plex-pass have not been of any real use to me so I have been using it without any cost.

---

### Post by TheFu on 2019-11-21
I tried to use miniDLNA, but it wasn't keeping the catalogue current.  We record TV, remove commercials, transcode to save 75% of the storage, then add it into the library.  After watching, most recordings are deleted.  MiniDLNA was never current with the content. The full rescan was just too abusive for a non-trivial library.  Was I just doing it wrong?

As for plex resource use - plex can transcode to support specific formats required by lower-end devices like a roku or chromecast.  This would hit 1 CPU at 50%-100% easily for hidef transcodes.  As for storage abuse, plex will happily make screen shot images every 30 sec of a movie to make feedback during ffwd/rwnd show the frame.  I think that is enabled by default, but can be disabled.  They call it "optimizing".  That turns into a huge amount of storage used for images that may never be used.  If there is lots of new content, creating those screenshots for all the video content can take weeks.  I don't know if old metadata stored inside plex ever gets removed.

My Plex box (dual core Pentium G3258) is using 11% CPU now, streaming a video to a tablet. No transcoding needed.  It is also a VM server for Nextcloud, Wallabag, Calibre, ZNC, and NFS for the network. It was a $50 CPU 5+ yrs ago.  Stuttering does happen on some 1080p content, but that is a r-pi client-side player limitation.

If you don't use any plex clients, there isn't any nagging, except on the plex webapp - [http://plexsrv:32400/web/index.html](http://plexsrv:32400/web/index.html) - as an **!** surrounded by yellow/orange background. Pretty minor for a nag.

---

### Post by ajgreeny on 2019-11-22
@ TheFu

Does your /etc/minidlna.conf file contain the uncommented line ***inotify=yes*** which as I read things means new files are detected automatically when added to the media folders?

What I'm not sure about is whether files removed are seen to be removed and thus removed from the database used by minidlna; it sounds from what you're saying that this is not so, though it may depend on the time interval set for inotify which in my case is every 15 minutes (900 secs).

---

### Post by SeijiSensei on 2019-11-22
I don't make many changes to the assets distributed by minidlna, but with inotify=yes, it does refresh the database routinely.

> Additionally, I want all the chromecast devices to be in sync when playing music.
Wouldn't that only work with some kind of server-push arrangement?  I only use DLNA with individual clients. Does the protocol even support a server-push method?

---

### Post by TheFu on 2019-11-22
I'll probably look at again, but some of my playback devices need the built-in transcoding that plex provides.  Have some really old family videos that are avi/divx and some other odd formats.

Looks like they changed the name to ReadyMedia. 

Sometimes I use the plex webapp to stream content through either a VPN or ssh-socks proxy when I'm travelling.  Sometimes transcoding the videos down to 480p is necessary from remote locations.

---

### Post by SeijiSensei on 2019-11-23
What are you using to view those avi/divx videos? I have a couple in the AVI container and with mpv and with VLC they play fine. They even play on my Android phone using MXPlayer with BubbleUPnP as the DLNA client. Do you have clients that cannot handle those container formats? What codecs are they using? Most videos in those containers were encoded in some flavor of mpeg4 which pretty much everything can display.

Update: My Roku device sees my minidlna server but won't play .avi files.  It won't play some other formats either and has trouble with "ASS" subtitles.  Sometimes it displays the subtitles as closed captions but doesn't show the video!

---

