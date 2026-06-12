---
title: "*buntu can not play AudioCD"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by mastablasta on 2011-03-12
Seriously i though it was a joke, But neither Kubuntu 10.10 nor Ubuntu 10.04 can play an audio CD. CD got recognised, i can see the tracks on it but neither OS can play them. Tried even with VLC. 

Anyone got an idea? So far i resorted to "illegal" activities (ripping the CD). Ok Kubuntu is in the proces of some BS swithcing of how devices are loaded but Ubuntu?! i am dissapointed.


What is this? Windows 95 could play them out of the box but the allmighty super duper ubuntu can't?

And that's one of the reasons people stay with windows.

---

### Post by NightwishFan on 2011-03-12
I can understand your frustration. However Ubuntu can certainly play audio cds. I love audio cds and play/have many. Why not try to play an audio cd, and then post the output of dmesg from the terminal here?

---

### Post by grahammechanical on 2011-03-12
What do you have as your preferred application for playing multimedia? Do you have any application set to do that?

I have been using Ubuntu exclusively since spring 2007 and I have never had any problem playing audio CDs. And as I own the CD I do not consider it illegal to copy the tracks on to my hard disc and play them from there. Some may dispute my considered opinion. But I do it and Ubuntu does it. And I do think that Ubuntu is super.

Regards.

---

### Post by mastablasta on 2011-03-13
> **NightwishFan said:**
> I can understand your frustration. However Ubuntu can certainly play audio cds. I love audio cds and play/have many. Why not try to play an audio cd, and then post the output of dmesg from the terminal here?

how would i do that? there is no error message. i used Amarok it just sits there showing 0 tracks on audio CD. when trying to open it it says i can't open and nothing shows up. i tried with rythmbox on another computer still nothing.

dolphin can see the files but when i try to run them it tries to run them with VLC but for some reason VLC says can not open file and the file path points to documents/whatever.... point is path is totaly wrong and made up.

is there a way to play it form terminal? do i need to start amarok form terminal and then follow the messages?

I doubt still i can make it work in Kubuntu.

EDIt just to add here when i try to run them in Ubuntu through Nautilus, nautilus starts up a movie player which also fails to play anything.

attached files:

binning shows when i insert the cd. it is recognised but i can't see it neither in amarok neither in dolphin.
amarok1 - i open amarok and this is what i get when i try to open the file.
doilphinand vlc - i put the CD into the other CD drive. this time the filesshow up but on double click it starts VLC with strange paths to file.

also one from the local team found this:

As already answered in the French thread:
K/Ubuntu is currently in transition from HAL to udev and CD support in Amarok does not work in that distribution. We will know more once this transition is achieved, which is planned for K/Ubuntu Natty Narwal aka 11.04
---

problem is neither does it seems to work in rythmbox or vlc.

---

### Post by jcolyn on 2011-03-13
Have you tried Gnome Mplayer?

If it isn't installed open synaptic and enter gnome-mplayer and check for install..

This is my favorite CD player and it will also play DVD movies as long as you have w32codecs and libdvdcss2 installed from Medibuntu..

---

### Post by llamabr on 2011-03-13
Are you saying that windows plays cd's on this same box previously, or via dual boot?  Or are you just suggesting that other people who run windows are able to do so?

Audio cd's do not play in the cdrom from the software, as mp3's and such do.  Instead, there's sometimes a little cable that usually connects right to the audio card, and it just plays directly.  If you've never used this box to play audio cd's with windows, this may be your issue.

Regarding dmesg:
1, put a disk in the drive
2, sit back, and give it a minute to do whatever it's doing
3, open a terminal, and type dmesg and then copy the last 10 lines or so

Do you hear the disk spin up when you insert it?

---

### Post by mastablasta on 2011-03-13
> **llamabr said:**
> Are you saying that windows plays cd's on this same box previously, or via dual boot?  Or are you just suggesting that other people who run windows are able to do so?

Audio cd's do not play in the cdrom from the software, as mp3's and such do.  Instead, there's sometimes a little cable that usually connects right to the audio card, and it just plays directly.  If you've never used this box to play audio cd's with windows, this may be your issue.

windows XP doesn't need the small cable anymore. it's been a while liek that and i've been playing the CD on my other computer with XP installed  (no cable and it works). I also tried it on a notebook where windows XP were installed before and we can be sure the CD worke there.. That notebook has Ubuntu installed. Before uinder XP CD playing wokred nice. Now Ubuntu - instead of playing it it doens't recognise it. or it does but nothing happens. i  tried to double clicked the file in nautilus there and it ran movie player. nice choice. it didn't work.

now this computer where i am posting from has Kubuntu installed. I am not sure if  it has the cable or not. but the point is CD is not recognised as it should. the computer has 2 drives. a CD-RW and a DVD-RW drive. 

CD-RW - dolphin can read the disk but upon double clicking the file i get the message i posted above. which as you can see starts VLC and the file name points to home/user/documents/... isnetad of to media. hmm i wodner why is thta so?

> 
Regarding dmesg:
1, put a disk in the drive
2, sit back, and give it a minute to do whatever it's doing
3, open a terminal, and type dmesg and then copy the last 10 lines or so

Do you hear the disk spin up when you insert it?

I am attaching the file. don't mind the spurious response as this is crappy ALSA audio drivers. it used to be even worse before. anyway as you can see on picture above CD spins and is recognised as audio cd. it even asks me what action i would like ot take. but when i do nothing happens.
 
dmesg1.txt -  the disk was inserted into CD-RW
dmesg2.txt when i insert the CD into another CD drive.



UPDATE:   I opened the box and checked the cables. CD-RW drive actually has the small cable attached (for the audio CD). while the DVD drive doesn't.



-

---

### Post by mastablasta on 2011-03-16
bump. seriously?

---

### Post by andrew.46 on 2011-03-18
> **mastablasta said:**
> is there a way to play it from terminal?

Perhaps try:

```
mplayer -cache 2048 cdda://
```

or for added coolness:

```
mplayer -cache 2048 -cache-min 80 cddb://
```

Andrew

---

### Post by Matt__ on 2011-03-18
Is it an enhanced multimedia disc by any chance?

with a .exe launcher for windows? 
If so and youre lucky it should mount as two discs, one with extra media (the .exe) and another that is audio (which is the one you should be playing in any linux player).

ps. maybe it just dosnt like bon jovi :P

---

### Post by mastablasta on 2011-03-20
> **andrew.46 said:**
> Perhaps try:

```
mplayer -cache 2048 cdda://
```

or for added coolness:

```
mplayer -cache 2048 -cache-min 80 cddb://
```

Andrew

OK this actually plays the AudioCD. Now i tried to open the .wav file with VLC and it said can only open local files. ?!!

Anyway how to make it play in GUI?

LOast command gives this output:
```
tatie@tatie-desktop:~$ mplayer -cache 2048 -cache-min 80 cddb://
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing cddb://.
No cache found.
Request[http://freedb.freedb.org/~cddb/cddb.cgi?cmd=stat&hello=anonymous+localhost+MPlayer VERSION&proto=1]
Resolving freedb.freedb.org for AF_INET6...
Couldn't resolve name for AF_INET6: freedb.freedb.org
Resolving freedb.freedb.org for AF_INET...
Connecting to server freedb.freedb.org[195.214.216.38]: 80...
body=[210 OK, status information follows (until terminating `.')
Server status:
    current proto: 1
    max proto: 6
    interface: http
    gets: no
    puts: no
    updates: no
    posting: no
    validation: accepted
    quotes: no
    strip ext: no
    secure: no
    current users: 62
    max users: 100
Database entries: 3029795
Database entries by category:
    data: 66362
    folk: 245475
    jazz: 179865
    misc: 951394
    rock: 788881
    country: 86739
    blues: 156563
    newage: 118289
    reggae: 40975
    classical: 273418
    soundtrack: 121834
.
]
Request[http://freedb.freedb.org/~cddb/cddb.cgi?cmd=cddb+query+f90ec511+17+150+14027+33650+53498+72475+88948+104928+121695+136576+152186+168959+171896+195935+213156+238963+254979+268563+3783&hello=anonymous+localhost+MPlayer VERSION&proto=6]
Resolving freedb.freedb.org for AF_INET6...
Couldn't resolve name for AF_INET6: freedb.freedb.org
Resolving freedb.freedb.org for AF_INET...
Connecting to server freedb.freedb.org[195.214.216.38]: 80...
body=[202 No match for disc ID f90ec511.
]
Album not found.
Found audio CD with 17 tracks.
Cache fill:  0.00% (0 bytes)   
Track 1

rawaudio file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  12.3 (12.3) of 3781.4 ( 1:03:01.4)  0.1% 21% 
```

> **Matt__ said:**
> Is it an enhanced multimedia disc by any chance?

with a .exe launcher for windows? 
If so and youre lucky it should mount as two discs, one with extra media (the .exe) and another that is audio (which is the one you should be playing in any linux player).

no just normal Audio CD.
> 
ps. maybe it just dosnt like bon jovi :P
LOL. yeah i had that thought, but Sinatra, Anggun, Queen... They are not playing as well.

---

### Post by andrew.46 on 2011-03-21
> **mastablasta said:**
> Anyway how to make it play in GUI?

If MPlayer will play your cds from the commandline the SMPlayer will be able to as well.

Andrew

---

### Post by mastablasta on 2011-03-21
> **andrew.46 said:**
> If MPlayer will play your cds from the commandline the SMPlayer will be able to as well.

Andrew

No. Thats the beauty of Ubuntu Linux - nothing works out of the box it would seem. Samba installed but was missing a package before it worked.... this AudioCD also seems to be not mounting propperly. I guess it's an older issue ?!: [http://ubuntuforums.org/showthread.php?t=1516501](http://ubuntuforums.org/showthread.php?t=1516501)

But who cares about fixing that, Apparently there are other more important issues to resolve, like making new Desktop Evnironment from scratch.

This is what i get when i try to run it from Smplayer (which doesn't even recognise the disk) - see attached picture.

This in picture is what i get when i try to open a specific file. because i tried to open the Audio CD and nothing happens. Oh and i still think this is a mounting issue because when i try to do it with VLC it says file can not be found and is looking for it in /Home/documents

/cdrom
/mnt

both folders are empty.

/media has floppy in it. nothing else


this is what i get when running kdesudo dolphin


```
kdesudo dolphin
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/tatie/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QMetaObject::invokeMethod: No such method DolphinApplication::loadCommandLineOptionsForNewInstance()
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kbuildsycoca4 running...
"/usr/bin/dolphin(2263)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2263)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/dolphin(2263)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2263)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/dolphin(2263)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2263)" Soprano: "QLocalSocket::connectToServer: Invalid name"
"/usr/bin/dolphin(2263)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2263)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2263)" Soprano: "org.freedesktop.DBus.Error.ServiceUnknown - The name org.kde.nepomuk.services.nepomukstorage was not provided by any .service files"
"/usr/bin/dolphin(2263)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2263)" Soprano: "Unsupported operation (2)": "Invalid model"
"/usr/bin/dolphin(2263)" Soprano: "Invalid iterator."

```

and then it is looking for a file in folder

audiocd:/track.wav

This doesn't seem right to me.

---

### Post by mastablasta on 2011-03-24
Issue still not resolved.

---

### Post by mastablasta on 2011-03-28
Bump.

---

### Post by mastablasta on 2011-03-31
Bump!

---

### Post by deathadder on 2011-03-31
> **mastablasta said:**
> No. Thats the beauty of Ubuntu Linux - nothing works out of the box it would seem. Samba installed but was missing a package before it worked.... this AudioCD also seems to be not mounting propperly. I guess it's an older issue ?!: [http://ubuntuforums.org/showthread.php?t=1516501](http://ubuntuforums.org/showthread.php?t=1516501)
Linux / Ubuntu works wonderfully for me out of the box while Windows doesn't, I understand you're having problems that are frustrating but people are here, trying to help so try and stay calm so we can get your music working! Audio cd's do not have a filesystem, so you simply can't  mount them.

We know that there isn't a problem with playing your CD's (mplayer does it) so there's a problem with some configuration in one of the apps you're attempting to use. 

Can you run a gui app from the command line and post the output? From your first post I can see you've tried amarok, can you run that from the command line, attempt to play the CD and post all of the output. It's probably a missing codec, or the apps are looking in the wrong place. Both of which are easy to fix. 

I know it's frustrating, but that's problem with software patients, Microsoft etc end up telling you you need to pay to play your own CDs or worse (??) you need to use their software and their software alone. This isn't a "ubuntu / linux sucks" problem. This is a "software patients suck" issue...

---

### Post by mastablasta on 2011-03-31
> **deathadder said:**
>  
Can you run a gui app from the command line and post the output? From your first post I can see you've tried amarok, can you run that from the command line, attempt to play the CD and post all of the output. It's probably a missing codec, or the apps are looking in the wrong place. Both of which are easy to fix. 
 
 
i can try and run from command line, though i am not sure what good will that do as the CD in those GUI apps is simply not recognised. I do not see it in them. I can not select it to play. 
 
I will try again when i get home from work. perhaps to open a "file" from AudioCD. Maybe that will give some output to terminal. Will try it when i get home.
 
i sitll think it's looking for the CD in the wrong place for some reaosn as it is saying that it can't find the thing in documents.
 
--
Nah in windows i use Winamp for CD (been using it since it came out in beta all those years ago) and opensource (or is it freeware) Media player classic for DVD's and the rest...

---

### Post by deathadder on 2011-03-31
Ok, to me it looked like amarok had actually found the cd but wasn't able to read it. 

Can you post it anyway, if we're lucky it'll tell us where it's looking. If it doesn't provide anything useful you can always try running it in debug mode:
```
$ amarok --debug
```
> Nah in windows i use Winamp for CD (been using it since it came out in beta all those years ago) and opensource (or is it freeware) Media player classic for DVD's and the rest...
Sorry not sure what you mean by this...?

---

### Post by mastablasta on 2011-04-01
This is as bizzare as it gets.

1. Using debug command makes it read the cd propperly and it works s it should. 
2. Using a normal amarok command afterwards - again the cd is read and playing as it should. it also works if i run Amarok form GUI.
3. If i close the terminal (console), change the cd with another one, open the terminal and run amarok - it can't see the cd. it also doesn.t play it. It can see the CD among "file->open" GUI
4. i then run amarok with debug command and again it now sees the CD. 

i tried this with several CD's and result is the same.

I saved all logs but since i knwo people dont' have time to go through them all i will only put up here 2 of them. They are from the item 3 and 4 example. So i inserted a new CD opened Amarok normally through terminal and got this output:
amarok_sinatra_not working.txt

But in this case CD propperly show up and it worked.
amarok_sinatra_debug_working.zip (sorry, but i had to compress this one due to forum rules)

As i said the system recognises the AudioCD when it is inserted and offers to play it with amarok. BUt once there there is no CD in the menu. 

Also the CD only seems to be playing on the CD drive that is directly connected to sound card. I can live with that as long as it works.

---

### Post by deathadder on 2011-04-01
While I'm having a look at that output, have you installed the restricted extras package? Can you run the command:
```
amarok --cd-play
```
Then post the output.

Just so you know, I don't have internet access at home atm so I might not get back to you until I'm back at work next week. But don't worry, I'm still looking :)

---

### Post by qyot27 on 2011-04-01
> **deathadder said:**
> It's probably a missing codec, or the apps are looking in the wrong place. Both of which are easy to fix.

I know it's frustrating, but that's problem with software patients, Microsoft etc end up telling you you need to pay to play your own CDs or worse (??) you need to use their software and their software alone. This isn't a "ubuntu / linux sucks" problem. This is a "software patients suck" issue...
It's not a patent issue - LPCM (i.e. 'uncompressed' audio) is long, *long* past the point it could be encumbered by patents, and Microsoft has/had nothing to do with the Red Book Standard that defines what Compact Disc Digital Audio is (and an interesting tidbit - copy protection/DRM is not allowed per Red Book, so in order for an audio disc to be properly approved by said standard, it cannot have DRM on it, and according to Philips, discs that are crippled by DRM are not supposed to have the trademarked standards logo on them).



Anyway, there have been or are several analogues to Winamp on *nix systems: XMMS, Beep Media Player, Audacious...Audacious being the most current one.

As for the issue of mounting, I would have thought that the [libcdio-cdda0](http://packages.ubuntu.com/maverick/libcdio-cdda0) package would already be installed so that the discs could in fact be mounted.  I'd look to see if that is installed, and if it isn't, then install it and see if the issue is resolved.

---

### Post by deathadder on 2011-04-01
I was making a more generic point about how it's frustrating that music can't be played on a Linux machine out of the box because of patients, rather than a specific point about CD's, sorry if that wasn't clear. But the point remains, it's a pain playing mp3's, dvds etc because of patients wrongly given to Microsoft etc.

The analogues to Winamp doesn't have any weight here, as far as I'm concerned, cd's can be played on the machine by using mplayer. A configuration issue somewhere means that gui's are having problems. I would imagine that it's a gstreamer, or simiilar, plugin issue (hence the restricted extras).

---

### Post by mastablasta on 2011-04-03
this is the output. CD is again not loaded or recognised.
```
QObject::connect: Cannot connect Meta::MediaDeviceHandler::incrementProgress() to (null)::incrementProgress()
QObject::connect: Cannot connect Meta::MediaDeviceHandler::endProgressOperation(QObject*) to (null)::endProgressOperation(QObject*)
Object::connect: No such signal Podcasts::SqlPodcastProvider::playlistAdded( Playlists::PlaylistPtr )
Object::connect: No such signal Podcasts::SqlPodcastProvider::playlistRemoved( Playlists::PlaylistPtr )
Object::connect: No such signal Playlists::SqlUserPlaylistProvider::playlistAdded( Playlists::PlaylistPtr )
Object::connect: No such signal Playlists::SqlUserPlaylistProvider::playlistRemoved( Playlists::PlaylistPtr )
amarok(2264)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2264)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2264)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(2264)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
amarok(2264)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/tatie/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QGraphicsLinearLayout::removeAt: invalid index 1
Object::connect: No such slot Plasma::WebView::urlChanged(const QUrl &)
amarok(2264)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok(2264)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok(2264)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(2264)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
QMetaObject::invokeMethod: No such method App::loadCommandLineOptionsForNewInstance()
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
tatie@tatie-desktop:~$ amarok(2264)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
amarok(2264)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/home/tatie/.local/share/mime/magic"


```

Kubuntu restricted extras are intalled. Also the menitoned AudioCD package is installed. 

What i find strange is that debug mode recognises the CD just fine and everyhtign works and loadsa as it should. Whereas normal star of amarok seems to not see it.

Where as SM player wants me to configure the CD drive and sleect one of the options that say where is it mounded (e.g. /dev/cdrom)


Similary VLC media player suggests /dev/ directory

But in reality when i click on AudioCD in dolphin GUI i get this: cdda://audiocd:/

I also can't give this folder (cdda:// or cddb://) as the drive in any configuration. And as i can see it is supposed to be the exact one (as in that command that was given by Andrew for the playing the cd in CLI).

---

### Post by NightwishFan on 2011-04-03
> **mastablasta said:**
> I also can't give this folder (cdda:// or cddb://) as the drive in any configuration. And as i can see it is supposed to be the exact one (as in that command that was given by Andrew for the playing the cd in CLI).

cdda:// and etc seems to me to be a virtual directory, so not all programs will be able to use it. The absolute path in /dev/ is what Linux itself sees I am sure.

---

### Post by mastablasta on 2011-04-04
i thought it must be something different as it is not a directory designation.
 
problem is there is nothing in /dev  and if you see some of my early screens, for some reason instead of dev it seems to be looking for Audio in /home/documents
 
again this only seems to increase the suspicions that AudioCD is actually "mounted" in the wrong place. In all of the GUI programmes.

---

### Post by wizard10000 on 2011-04-04
Can't speak to the GNOME side but this is a known issue with KDE and has been kicked around the Kubuntu forums for months.  KDE doesn't seem to play audio CDs at all, not with amarok or anything else  :(

---

### Post by mastablasta on 2011-04-04
> **wizard10000 said:**
> Can't speak to the GNOME side but this is a known issue with KDE and has been kicked around the Kubuntu forums for months. KDE doesn't seem to play audio CDs at all, not with amarok or anything else :(
 
Is it really? I guess you have not read my previous posts... So let me repeat:
 
running amarok from terminal in debug mode makes Amarok recognise the AudioCD propperly and also plays it.
 
I think i saw your post searching for sulution (sort of ur avatar stayed in my head, i could be wrong.)
 
anyway if you have KDE you can try it. just type in amarok --debug
 
now the quesiton is why it works in debug mode and not in nromal mode? and moreover how can you debug and troubleshoot like that? :-P

---

### Post by wizard10000 on 2011-04-04
> **mastablasta said:**
> Is it really? I guess you have not read my previous posts... So let me repeat:
 
running amarok from terminal in debug mode makes Amarok recognise the AudioCD propperly and also plays it.
 
I think i saw your post searching for sulution (sort of ur avatar stayed in my head, i could be wrong.)
 
anyway if you have KDE you can try it. just type in amarok --debug
 
now the quesiton is why it works in debug mode and not in nromal mode? and moreover how can you debug and troubleshoot like that? :-P

You're right - I just skimmed this thread.  Haven't had enough coffee this morning yet  :)

I have no idea how to troubleshoot something that works in debug mode but not in regular mode - let me look at launchpad real quick -

Look here -

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/477667](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/477667)

and here - I think this explains it.

[http://forum.kde.org/viewtopic.php?f=115&t=91305&start=15#p185538](http://forum.kde.org/viewtopic.php?f=115&t=91305&start=15#p185538)

I still can't explain why it works in debug mode, though  :)

---

### Post by oldos2er on 2011-04-04
> **wizard10000 said:**
>   KDE doesn't seem to play audio CDs at all, not with amarok or anything else 

I know this doesn't help, but I haven't had a problem playing audio CDs on either Kubuntu 10.10 or 11.04. I usually use either Kaffeine or vlc.

---

### Post by mastablasta on 2011-04-06
> **oldos2er said:**
> I know this doesn't help, but I haven't had a problem playing audio CDs on either Kubuntu 10.10 or 11.04. I usually use either Kaffeine or vlc.
 
you're right. It doesn't. CD is also not played in VLC. Nor in SMplayer. Only in CLI mplayer and Amarok  with debug mode on. which is strange...
 
But sitll how is your CD Drive connected (if you know)? I have one only to disk and one to Disk and soudn card. And this one directly to sound card actually works in debug mode. Did you maybe upgrade to KDE 4.6?
 
I wonder, what would happen if i tried to boot it via the LiveUSB and then try to play it... hmm...

---

### Post by oldos2er on 2011-04-06
Yes, I'm running KDE 4.6. DVD/CD-ROM uses an SATA connector.

---

### Post by mastablasta on 2011-04-08
I am running default KDE which is not 4.6 i believe.
 
Hmm i will wait for a month or so and then upgrade to 11.04. Perhaps that will solve the problem.

---

### Post by mastablasta on 2011-04-10
UPDATE

I added the latest stable KDE 4.6.2 to it.

Now Amarok loads the Audio CD but doesn't play it. Even with debug mode on. Simply nothing happens when i press play. Though it says sort of liek it's playing it.

Anyway i couldn't get the full info from debug as Konsole is limited and there are plenty of messages going out.

but what i could get is attached.

 BTW is there a way/command to make the output from debug go to txt file so i can have the the whole message? Also what forums do i turn to for better support? KDE?

---

### Post by NightwishFan on 2011-04-10
Try going to the Amarok IRC channel.
[http://amarok.kde.org/en/support](http://amarok.kde.org/en/support)

---

### Post by deathadder on 2011-04-11
When you run a command you can redirect the output like so:
```
$ amarok --debug > debugOut
```
That'll create a file called debugOut in the current directory.

Have a look at the amarok support channels NightwishFan has pointed you towards.

---

### Post by mastablasta on 2011-04-11
it created a file but there is nothing in it :-) is there something missing in the command?

---

### Post by mastablasta on 2011-04-14
Back to Ubuntu forums i guess. I received this reply on KDE forums:
> if you had searched the internet and both this forum and the bugs list you would know this is related to the HAL -> Udev transition that happend in Kubuntu and KDE. Not much we can do about that, sorry.

I think I have answered this question at least about 20 times by now.
 
I am curious - does this mean Kubuntu is unable to play CD in GUI? And if so how come some can play it?

---

### Post by srauls on 2011-09-20
Had the same problem

Try adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

It works for me!

---

### Post by jmate24 on 2011-09-20
I have found that in past versions there was an entry for the cdrom drive in /etc/fstab and /etc/mtab and now they are missing and i cannot figure out how to add my cdrom device to those lists. anyone have an answer?

---

### Post by mcduck on 2011-09-21
Well, I can definitely see at least one problem in the way you are trying to play the CD. You are trying to open the audio tracks as *files*, which is not going to work. you need to tell your music player to open an audio CD instead.

Even while some file managers have ways of showing audio CD's as if they contained separate files (usually they show you .wav or .cda as file type), audio CD's don't actually contain any files or even a directory structure such as you have on your computer or on data-CD's. So any program that is showing you the content of the disc as files simply has some feature that allows it to read the tracks from the disc and convert them into files for you on-the-fly. That might work fine if you want to move copy the tracks to your computer, but if you want to play the tracks on a music player such file-based approach will not work.

edit: For example if you wanted to play the CD using VLC, the File/Open File and browsing to the CD method is not going to work. Instead you need to use File/Open Disc.

---

### Post by Lisiano on 2011-09-21
Right. [http://ubuntuforums.org/showpost.php?p=11271886&postcount=196](http://ubuntuforums.org/showpost.php?p=11271886&postcount=196) Or not.
You can abstract the access to the CD drive using KIO or GIO. Sadly KIO can't be used but GIO can be (As in it uses fuse for legacy/non-gnome apps and "mounts" stuff at ~/.gvfs) but sadly it's a PITA to set up for some reason on Kubuntu (At least it was for me when I tried that approach with the poster of the post I linked above).
So why not use another abstraction? CDFS it let's you use the normal "mount" command to mount the CDs and since they are in wav (Read uncompressed, the way they are stored on a CD) and it can be accessed by going to a arbitrary directory like /media/cdrom, any and all applications will recognize the "files" and play them.

Advantages:
[LIST]
[*]Scriptable
[*]Easy to use
[*]Works in any program that can access the local filesystem
[*]Backwards-compatible with older apps
[/LIST]
Disadvantages:
[LIST]
[*]Not available as a already compiled filesystem
[/LIST]

Yes, it's a workaround but it's possible to listen to Audio-CD's in a more or less intuitive manner.
Hope this helps someone.

---

### Post by mastablasta on 2011-12-04
> **mcduck said:**
> Well, I can definitely see at least one problem in the way you are trying to play the CD. You are trying to open the audio tracks as *files*, which is not going to work. you need to tell your music player to open an audio CD instead.
 
Even while some file managers have ways of showing audio CD's as if they contained separate files (usually they show you .wav or .cda as file type), audio CD's don't actually contain any files or even a directory structure such as you have on your computer or on data-CD's. So any program that is showing you the content of the disc as files simply has some feature that allows it to read the tracks from the disc and convert them into files for you on-the-fly. That might work fine if you want to move copy the tracks to your computer, but if you want to play the tracks on a music player such file-based approach will not work.
 
edit: For example if you wanted to play the CD using VLC, the File/Open File and browsing to the CD method is not going to work. Instead you need to use File/Open Disc.
 
nope. i get this with VLC:
 
Your input can't be opened:
VLC is unable to open the MRL 'cdda:///dev/cdrom'. Check the log for details.
 
if i go browse to other location file browser crahses.
 
Edit:
 
I've added the aforementioned modules. then i noticed that amarok marks CD differently. So i gave it another shot with VLC. VLC now opened it,
 
however i had to go to Media->open disc
select AudioCd
then i have to manually find the cd as the default shortcut is wrong. my cd is under /dev/scd0 and not under dev/cdrom (no wonder it couldn't read it before).
 
Is there any other programme that can do this that is perhaps more made for music?
Is there a way to make /dev/scd0 and dev/scd1 in VLC kind of a default? changing the path to AudioCD device in system settings doesn't seem to do the trick. unless a reboot is required? i need to make this as much user friendly as possible (ie- open and play) as this is my wife's computer.... :D

---

### Post by mastablasta on 2011-12-14
bump

---

### Post by mastablasta on 2011-12-19
bump

---

### Post by cnupm on 2012-04-21
It's working!

I'm running Xubuntu on live USB because my hard disk died :(. System is working great but i had problems playing audio cd's.
But after installing gnome-mplayer i can listen to audio CD's. That's OK

But still, when i double-click the CD icon on the desktop i get the error message:

|Failed to mount "Audio Disc"|
|Location is not mountable        |

And Audio CD Extractor giving this error message:

Could not read the CD

|Sound Juicer could not read the track listing on this CD.                 |
|Reason: Cannot access CD: The specified location is not supported|

But Gnome MPlayer still can play audio CD's

Can it be because i'm using a live USB system?

---

