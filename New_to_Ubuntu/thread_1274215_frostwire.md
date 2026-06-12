---
title: "frostwire"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by ray62 on 2009-09-24
Hi can any one help installed frostwire downloads stuff no problems 
but if i leave it a few mins it freezes and av 2 restart frostwire any ideas 
any one ???

---

### Post by Marflus on 2009-09-24
Not having ever used Frostwire, I wouldn't know enough to help you, probably. I do know, though, that people will need a bit more information to know what's going wrong. What version of Ubuntu are you running? What are your system specs? Does Frostwire report any error messages? (Have you checked logfiles, etc?)

The more information users have to go on, the easier it is to help.

---

### Post by astrakhan on 2009-09-24
I also don't know much about frostwire, but open a terminal (Applications > Accessories > Terminal) and type frostwire. Debug is enabled by default. Copy all of the terminal output and paste it here after it freezes again.

---

### Post by ray62 on 2009-10-06
ray62@ray62-laptop:~$ frostwire
HOSTNAME IS ray62-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_16]
Configuring environment...
Loading FrostWire:
CLASSPATH SET TO: :./httpcore-nio-4.0-beta2.jar:./guice-1.0.jar:./mp3spi.jar:./ProgressTabs.jar:./jorbis.jar:./FrostWire.jar:./jmdns.jar:./junit.jar:./jogg.jar:./daap.jar:./gettext-commons.jar:./jdic_stub.jar:./httpclient-4.0-alpha3.jar:./httpcore-niossl-4.0-alpha7.jar:./icu4j.jar:./themes.jar:./lw-all.jar:./commons-logging.jar:./looks.jar:./onion-fec.jar:./aopalliance.jar:./foxtrot.jar:./onion-common.jar:./messages.jar:./jflac.jar:./clink.jar:./jl.jar:./jython.jar:./jdic.jar:./jcraft.jar:./jaudiotagger.jar:./log4j.jar:./tritonus.jar:./forms.jar:./httpcore-4.0-beta2.jar:./commons-codec-1.3.jar:./vorbisspi.jar
****STARTUP DEBUG: Is this a supported windows or Mac? false
**OverlayAd.image() - OVERLAY AD, im going to load:file:///home/ray62/.frostwire4.18/overlays/frostclick_default_overlay.jpg
UpdateManager.scheduleUpdateCheckTask() - TimerTask.run()
UpdateManager.checkForUpdates() - Invoked
Trying to start chat panel...
initializing chat community...
Creating new IRC App...
Initializing new IRC App...
UpdateMessageReader.startElement overlay intro=true
UpdateMessageReader.endElement() - addOverlay
UpdateMessageReader.endElement() - addOverlay
UpdateMessageReader.startElement overlay intro=true
UpdateMessageReader.endElement() - addOverlay
UpdateMessageReader.endElement() - addOverlay
UpdateMessageReader.startElement overlay intro=true
UpdateManager.isMessageForMe() - Message was null
UpdateManager.checkForUpdates() - We have overlays to update.
UpdateManager.updateOverlays() invoked.
OverlayImageManager.getCachedImagePath(): Image didn't change, using cached
SearchResultDisplayer.refreshOverlayAd()
**OverlayAd.image() - OVERLAY AD, im going to load:file:///home/ray62/.frostwire4.18/overlays/frostclick_default_overlay.jpg
Can load libraries!
Smileys should be ACTIVE!
Initialized! new IRC App...
getting nick: ray62Chat enabled?: true
OverlayImageManager.getCachedImagePath(): Image didn't change, using cached
UpdateManager.updateOverlays() - About to update secondary mofo - file:///home/ray62/.frostwire4.18/overlays/default.png
Removing previous banners...
Getting banners from server...
Loading banners...
User-Agent: FrostWire/Linux/4.18.1
SponsorLoader.startElement -> Detected a custom refreshrate -> 0
SponsorLoader.startElement -> Killing Banner Refresh Tasks
BannerContainer.setupBannerRefreshTask() - No banner refresh for me.
Fetching ip address on separate thread
My IP address looks like this ->0.0.0.0
Waiting one more second to get the ipAddress
Fetching ip address on separate thread
My IP address looks like this ->0.0.0.0
Waiting one more second to get the ipAddress
Fetching ip address on separate thread
My IP address looks like this ->0.0.0.0
Waiting one more second to get the ipAddress
This is what the networkManager grabbed ->
0.0.0.0

Waiting one more second to get the ipAddress
Fetching ip address on separate thread
My IP address looks like this ->0.0.0.0
Waiting one more second to get the ipAddress
This is what the networkManager grabbed ->
0.0.0.0

Waiting one more second to get the ipAddress
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Matalica - Enter Sand Man.mp3
Fetching ip address on separate thread
My IP address looks like this ->0.0.0.0
Waiting one more second to get the ipAddress
Banners loaded!
BannerContainer.banners.size() -> 5
Refresh ended
end of try...
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Metalica - For whom the bells toll.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Def Lepard - Hysteria.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Nirvana - Smells Like Teen Spirit .mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Drowning Pool - Full Circle.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Seether - **** It (Creed, Puddle of Mudd, Godsmack, Nickelback, Staind, Taproot, Nirvana, Bush, Drowning Pool).mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Guns And Roses - Welcome To The Jungle.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/02 - Where Did All The Love Go.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Nirvana - In Bloom.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Drowning Pool - 37 Stitches.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Drowning Pool - Tear away(1).mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Def Lepard - Photograph.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Metallica - One.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Poison - Talk Dirty To Me.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Poison - Every Rose Has Its Thorn   80's rock Monster Ballads-.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Def Lepard - Love Bites.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Drowning Pool - Let the bodies hit the floor!.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Guns & Roses - November Rain.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/White Snakes - Here I Go Again On My Own.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/GUNS & ROSES- Sweet Child Of Mine.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/def lepard - def leppard - lets get rocked.mp3
*****SPECIAL FILE IS: /home/ray62/FrostWire/Saved/Drowning Pool - Hate.mp3
This is what the networkManager grabbed ->
0.0.0.0

Waiting one more second to get the ipAddress
This is what the networkManager grabbed ->
0.0.0.0

Waiting one more second to get the ipAddress
This is what the networkManager grabbed ->
0.0.0.0

Waiting one more second to get the ipAddress
Initializing Connection Doctor...
FrostWire's connection doctor will be started at 15 seconds, now waiting: 1 seconds
This is what the networkManager grabbed ->
0.0.0.0
and still freezes ???

---

