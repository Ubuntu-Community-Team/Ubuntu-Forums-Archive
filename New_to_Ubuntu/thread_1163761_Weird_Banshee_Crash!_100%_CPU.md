---
title: "Weird Banshee Crash?!? 100% CPU"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2009-05-19
To make a long story short, i have been playing with itunes replacements for all day (that means i installed and removed exaile, banshee, songbird and amarok a couple times) and decided to pick banshee. Everything was working just fine.After i organized my music with banshee i went and installed ipod-convinience and gtkpod, it worked just fine and i actually used banshee a couple times after.

Then after i left my pc alone for a couple hours i went back, restarted and noticed banshee doesn't quite work, the windows frame loads but the buttons and all the gui doesnt show up and it just stays there idle until gnome says is not responding and i have to force quit.

When i use "top" i notice that banshee-1 is consuming 100% of my cpu's and it will continue to do so unless i kill it.

I tried running banshee from the console in debug mode and this is what i got

```

ndranc@uMIA:~$ banshee --debug
\** Running Mono with --debug   **
[Info  00:57:24.296] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, x86_64) @ 2009-03-22 17:00:13 UTC]
[Debug 00:57:25.590] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[Debug 00:57:25.598] Core service started (DBusServiceManager, 0.001501s)
[Debug 00:57:25.600] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[Debug 00:57:25.611] Core service started (DBusCommandService, 0.012631s)
[Debug 00:57:25.662] Opened SQLite connection to /home/ndranc/.config/banshee-1/banshee.db
[Debug 00:57:25.662] Core service started (DbConnection, 0.05165s)
[Debug 00:57:25.672] Database version 22 is up to date
[Debug 00:57:25.688] Core service started (PreferenceService, 0.015267s)
[Debug 00:57:25.689] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[Debug 00:57:25.689] Core service started (SourceManager, 0.000783s)
[Debug 00:57:25.867] Core service started (MediaProfileManager, 0.17799s)
[Debug 00:57:25.868] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[Debug 00:57:25.870] Core service started (PlayerEngine, 0.002495s)
[Debug 00:57:25.875] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 00:57:25.932] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 00:57:25.939] Core service started (TranscoderService, 0.009183s)
[Debug 00:57:25.941] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[Debug 00:57:25.941] Core service started (PlaybackController, 0.002552s)
[Debug 00:57:25.942] Core service started (ImportSourceManager, 0.000504s)
[Debug 00:57:25.947] Core service started (LibraryImportManager, 0.005413s)
[Debug 00:57:25.948] Core service started (UserJobManager, 0.000369s)
[Debug 00:57:25.960] Core service started (HardwareManager, 0.012118s)
[Debug 00:57:25.963] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[Debug 00:57:25.964] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[Debug 00:57:25.965] Core service started (CollectionIndexerService, 0.004939s)
[Debug 00:57:25.982] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 00:57:25.982] Core service started (GtkElementsService, 0.017317s)
[Debug 00:57:26.048] Core service started (InterfaceActionService, 0.065806s)
[Debug 00:57:26.050] Album artwork path set to /home/ndranc/.cache/album-art
[Debug 00:57:26.050] Core service started (ArtworkManager, 0.001678s)
[Debug 00:57:26.529] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[Debug 00:57:26.529] Core service started (NereidPlayerInterface, 0.479416s)
[Debug 00:57:26.531] Extension service started (DapService, 0.000536s)
[Debug 00:57:26.531] Extension service started (DaapService, 0.000802s)
[Debug 00:57:26.539] Extension service started (BookmarksService, 0.007692s)
[Debug 00:57:26.575] Extension service started (AudioCdService, 0.035497s)
[Debug 00:57:26.591] Extension service started (LastfmRecommendationService, 0.016124s)
[Debug 00:57:26.601] Core service started (Network, 0.004478s)
[Debug 00:57:26.602] Audioscrobbler state: connected
[Debug 00:57:26.604] Extension service started (AudioscrobblerService, 0.01291s)
[Debug 00:57:26.611] Extension service started (GnomeService, 0.006523s)
[Debug 00:57:26.829] Extension service started (NotificationAreaService, 0.218512s)
Mirage - Open DB - URI=file:/home/ndranc/.cache/banshee-mirage/mirage.db,version=3
Mirage - Database version 2 is up to date
[Debug 00:57:26.841] Mirage - Initialized
[Debug 00:57:26.841] Extension service started (MirageService, 0.011541s)
[Debug 00:57:27.016] Extension service started (PodcastService, 0.175265s)
[Debug 00:57:27.020] Using GNOME 2.22 API for Multimedia Keys
[Debug 00:57:27.025] Extension service started (MultimediaKeysService, 0.008686s)
[Debug 00:57:27.114] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 00:57:27.170] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 00:57:27.170] Extension service started (GStreamerCoreService, 0.14496s)
[Debug 00:57:27.192] Player state change: NotReady -> Ready
[Debug 00:57:27.203] Player state change: Ready -> Idle
[Debug 00:57:27.210] (libbanshee:player) Disabled ReplayGain
[Debug 00:57:27.212] Extension service started (CoverArtService, 0.001694s)
[Info  00:57:27.213] All services are started 1.622192s

```

To make things more interesting, when i switch users to a guest account banshee does run fine in there. I already tried removing and reinstalling, deleting the config files, rebooting, emptying the music folder, deactivating compiz and emerald, tried rythmbox and works fine. I don't know if this is the place for this, but i have no idea what this could be (since im really new at linux). It's probably something i end up doing that i don't remember.

Any suggestions? Or mind pointing out where i could get some answers? I tried google but i just get vague bug reports.

**#]]==========\#\ EDIT /#/==========[[#**

Here's a screenshot of banshee running on one side and "top" running on a terminal beside it.

[[IMG]http://img141.imageshack.us/img141/4838/stiscreenshot.th.png[/IMG]](http://img141.imageshack.us/my.php?image=stiscreenshot.png)

---

### Post by directhex on 2009-05-19
I think the Mirage add-on is to blame here. Try uninstalling it.

---

### Post by skymera on 2009-05-19
I've had a few Banshee crashes with 100% CPU.

Turns out it was Python. (Emesene also crashed)

---

### Post by barbedsaber on 2009-05-19
I had the same problem (well, I think it was the same problem).
it started when I dragged my entire music library into mirage... bad idea.
Anyway, I solved it by removing banshee (and the configs, which I believe are in .gnome-1 or something like that) and then reinstalling banshee from the banshee ppa.
Hope that is able to help.

---

### Post by Ryuki_NdranC on 2009-05-19
> **skymera said:**
> I've had a few Banshee crashes with 100% CPU.

Turns out it was Python. (Emesene also crashed)


Mind elaborating? What did you do to fix it?


[QUOTE=barbedsaber]I had the same problem (well, I think it was the same problem).
it started when I dragged my entire music library into mirage... bad idea.
Anyway, I solved it by removing banshee (and the configs, which I believe are in .gnome-1 or something like that) and then reinstalling banshee from the banshee ppa.
Hope that is able to help. [/QUOTE]

Ok i just tried that in the exact order you put it in and nothing...

1. sudo apt-get remove banshee & sudo apt-get autoremove
2. rm  -rf ./.config/banshee-1
3. Added Banshee PPA
4. sudo apt-get install banshee

Same problems still... I thing the mirage idea might be right... but so far it doesn't seem so. It has to be some stupid config file somewhere, because on the same machine on a guest account, with all the same things installed it runs just fine.

Thanks for the quick responses.

---

### Post by skymera on 2009-05-19
> **Ryuki_NdranC said:**
> Mind elaborating? What did you do to fix it?

I didn't do anything.

I killed Python and Banshee and it hasn't happened since.

Python 2.6 seems buggy compared to 2.4 ane 2.5

---

### Post by barbedsaber on 2009-05-19
As long as you have removed mirage as well as banshee, and gotten it again from the PPA, I can't help you. Thats what I did, and so it seems that I had a different problem.
Sorry I couldn't be more help, good luck though.

---

### Post by Ryuki_NdranC on 2009-05-19
> **skymera said:**
> I didn't do anything.

I killed Python and Banshee and it hasn't happened since.

Python 2.6 seems buggy compared to 2.4 ane 2.5


Ok... im new to linux, but isn´t python important for something? What are you saing is that i should

1. $ top
2. $ kill #### (python id number)
3. $ banshee

Even if that works, would that mean that i can´t ever use python with banshee again?. I´m sorry if this somehow seems rather obvious, but as i have stated before, i´m still learning to move arround in linux.

**EDIT**: I just test the python thing by doing "killall python" and then running banshee with no change what so ever.

[QUOTE=barbedsaber]As long as you have removed mirage as well as banshee, and gotten it again from the PPA, I can't help you. Thats what I did, and so it seems that I had a different problem.
Sorry I couldn't be more help, good luck though. [/QUOTE]

Yep, i did just that, in the same steps order i posted before. No thank you for helping out. Now at least i know it doesnt seem to be mirage. I wish it was though. I have a slight OCD and this thing is litteraly killing me ](*,).

PS: I´m not at home right now, im just confirming by memory what i should do once i get there (in about 7 hours from now).



**EDIT**: I added a screenshot illustrating what seems to happen with banshee and the 100% cpu banshee-1 in the terminal running "top".

---

### Post by Ryuki_NdranC on 2009-05-20
Fixed it... I though it had to be a config file somewhere that was messing with banshee, so i did a "sudo find / -name *banshee*" and "rm -rf" everything that showed up. The just installed back and everything was back to normal. No idea what triggered this though, but im not getting near mirage just incase. :)

---

### Post by sdowney717 on 2009-11-26
well I am getting 100% cpu and banshee turns gray and becomes unusable or is terribly slow.

I have no music loaded. But was using it for video podcasting. I loaded in 30 rss feeds, everything was fine shut down banshee came back restarted it and it is horrible.
the config files are located in home/.config/banshee1

I removed the config files and restarted, everything was fine and then on a reboot, the whole terrible problem reoccured.

so yes it is a nice program, but it is unreliable and i cant use it.
I even tried making working backups of the database, but copying them over and restarting still gives the bad horrible experience.

I have a core2 duo 3.5ghz with 4gb ram so my machine is perfectly fine. memtest86 passes with no erros. so the problem is in the poorly written software.

---

### Post by Steve Roscio on 2009-12-16
Anyone ever find a solution to this?  I've upgraded to the latest banshee as of today (1.6 Beta 4) 1.5.3.  I disabled anything related to internet downloads (and strange - the option disappeared after disabling it after restarting banshee, so how can it be turned back on?).  I disabled every extension except the five basic ones.  I disabled replay gain correction.

Anyway, after *any* song change, the CPU pegs at 100% for 30-45 seconds, the UI becomes unresponsive (gnome even dims it to gray), and it leaks another chunk of memory.  Sometimes it never comes back from this.

I really hope this gets fixed.  Banshee is the best replacement I've found for iTunes, but this bug makes it nearly unusable.

---

