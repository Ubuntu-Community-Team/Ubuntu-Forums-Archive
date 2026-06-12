---
title: "Banshee freezes when opened (screenshot included)"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Townley89 on 2010-08-16
Not really a new user, but usually pretty clueless nonetheless, running Lucid on a Dell Inspiron 15. 

Anyway, whenever I start up Banshee it simply freezes even before I can see the music browser part (I've attached a screenshot here, Banshee) The problem persists after uninstalling and reinstalling Banshee, and the problem does not occur with other music players like Rhythmbox. Starting it up causes the CPU usage to shoot through the roof (also screen'd). I've used Banshee on this computer for 5 months now without incident, so I was pretty confused when it randomly started acting up one day. 

Anyway, any help you can provide would of course be most appreciated. If I don't get my video podcasts, I get cranky :popcorn:

---

### Post by ubudog on 2010-08-16
You might want to report this to the Banshee Team:
[https://launchpad.net/~banshee-team](https://launchpad.net/~banshee-team)

---

### Post by giannibat on 2010-08-23
same problem for me, Banshee 1.7.4 from PPA on Lucid.
Solved by disabling some extensions, but I don't know which one.
Try disabling one by one.

---

### Post by Townley89 on 2010-08-24
Thanks for the advice, I'd like to try this. Unfortunately, I can't get to my extensions to disable them, since the crash occurs before Banshee loads. Is there a way to disable the extensions outside of banshee?

---

### Post by bowens44 on 2010-08-24
You can uninstall the extensions.

---

### Post by ubudog on 2010-08-24
Do you know if they are kept in a folder?  (eg. /usr/share/banshee/extensions)

---

### Post by SQuark on 2010-09-12
Same problem here. Did you manage to fix it?

---

### Post by Jesus_Valdez on 2010-09-12
Maybe deleting the Banshee folder helps is on /home/USER/.config/banshee-1

---

### Post by barbedsaber on 2010-09-12
I was having this problem a long time ago, I solved it by using rhythmbox, possibly not the answer you were looking for though :)

---

### Post by bombaklat on 2010-09-13
> **Townley89 said:**
> Thanks for the advice, I'd like to try this. Unfortunately, I can't get to my extensions to disable them, since the crash occurs before Banshee loads. Is there a way to disable the extensions outside of banshee?

go to:
/home/USER/.config/banshee-1/addin-db-001
and use gedit to modify config.xml

I've just disabled both amazon extensions and banshee is running.

---

### Post by jdorenbush on 2010-09-16
If you're having problems with Banshee freezing upon loading, you should run it in debug mode first to determine where it's hanging. 

In my case it was at:
```
**banshee --debug**
...
[1 Debug 23:10:38.735] Delayed Initializating Banshee.Daap.DaapService
[3 Warn  23:10:38.741] Failed to load media-player-info file for 
** (Banshee:7925): CRITICAL **: itdb_get_control_dir: assertion `mountpoint' failed
[4 Debug 23:10:38.909] DAAP Proxy listening for connections on port 8089
```

I then ran Banshee as root, and it worked just fine. So it seems as though it's an issue with privileges. At least in my case. At the end of it all, I determined that there were three services causing Banshee to lock up:
```
Banshee.Daap.dll
Banshee.Dap.dll
Banshee.Podcasting.dll
```

I removed them from the extensions dir. and everything is working fine now.

```
/usr/lib/banshee-1/Extensions
```

---

### Post by ubudog on 2010-09-16
Or remove the extensions one by one, until the problem is fixed, so that you don't have to get rid of all your extensions.

---

### Post by Townley89 on 2010-09-19
Awesome, deleting my extensions did the trick! I was having problems getting permission to delete the files in the aforementioned folder, so I used sudo rm (file in question) which you can helpfully do by dragging the file from the browser into the terminal window and getting rid of the extraneous space at the end of the command before executing (total newbie stuff, I know, but I thought if it helps someone else who has no idea what to do, I'll throw it in here.) 

Thanks again for all the help!

---

### Post by ubudog on 2010-09-20
Cool!

---

### Post by jdorenbush on 2010-09-20
> **Townley89 said:**
> Awesome, deleting my extensions did the trick! I was having problems getting permission to delete the files in the aforementioned folder, so I used sudo rm (file in question) which you can helpfully do by dragging the file from the browser into the terminal window and getting rid of the extraneous space at the end of the command before executing (total newbie stuff, I know, but I thought if it helps someone else who has no idea what to do, I'll throw it in here.) 

Thanks again for all the help!

FYI, Alt+F2 (Run), type "gksu nautilus", and hit enter. Now you'll have unrestricted access (sudo) to files/folders. :)

---

### Post by slughappy1 on 2010-09-21
My Banshee install started to freeze on startup with version 1.7.5. I just updated to 1.7.6 tonight, and it has the same problem. I ran it with the --debug and this is what I got
```
jason@Barnaby ~ $ banshee --debug
** Running Mono with --debug   **
[1 Info  02:52:50.461] Running Banshee 1.7.6: [Ubuntu 10.04.1 LTS (linux-gnu, x86_64) @ 2010-09-20 04:21:21 UTC]
[1 Debug 02:52:50.476] Initializing GTK
[1 Debug 02:52:51.678] Post-Initializing GTK
[1 Debug 02:52:51.691] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[1 Debug 02:52:51.697] Using default gconf-base-key
[1 Debug 02:52:51.747] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with PrimaryOwner
[1 Debug 02:52:51.807] Core service started (DBusServiceManager, 0.001134)
[1 Debug 02:52:51.809] Registering remote object /org/bansheeproject/Banshee/DBusCommandService (Banshee.ServiceStack.DBusCommandService) on org.bansheeproject.Banshee
[1 Debug 02:52:51.817] Core service started (DBusCommandService, 0.009966)
[1 Debug 02:52:51.883] Opened SQLite (version 3.6.22) connection to /home/jason/.config/banshee-1/banshee.db
[1 Debug 02:52:51.884] Core service started (DbConnection, 0.066761)
[1 Debug 02:52:51.887] Database version 43 is up to date
[1 Info  02:52:51.903] Starting collection of anonymous usage data
[1 Debug 02:52:51.933] Core service started (PreferenceService, 0.01854)
[1 Debug 02:52:51.933] Registering remote object /org/bansheeproject/Banshee/SourceManager (Banshee.Sources.SourceManager) on org.bansheeproject.Banshee
[1 Debug 02:52:51.933] Core service started (SourceManager, 0.000599)
[1 Debug 02:52:51.941] Core service started (MediaProfileManager, 0.000183)
[1 Debug 02:52:51.943] Registering remote object /org/bansheeproject/Banshee/PlayerEngine (Banshee.MediaEngine.PlayerEngineService) on org.bansheeproject.Banshee
[1 Debug 02:52:51.944] Core service started (PlayerEngine, 0.003003)
[1 Debug 02:52:51.960] Registering remote object /org/bansheeproject/Banshee/PlaybackController (Banshee.PlaybackController.PlaybackControllerService) on org.bansheeproject.Banshee
[1 Debug 02:52:51.961] Core service started (PlaybackController, 0.003444)
[1 Debug 02:52:51.968] Starting - Startup Job
[1 Debug 02:52:51.968] Core service started (JobScheduler, 0.007419)
[1 Debug 02:52:51.986] IO provider extension loaded (Banshee.IO.Gio.Provider)
[1 Debug 02:52:52.013] Loaded HardwareManager backend: Banshee.Hardware.Gio
[1 Debug 02:52:52.015] Core service started (HardwareManager, 0.046968)
[1 Debug 02:52:52.018] Bus.Session.RequestName ('org.bansheeproject.CollectionIndexer') replied with PrimaryOwner
[1 Debug 02:52:52.020] Registering remote object /org/bansheeproject/Banshee/CollectionIndexerService (Banshee.Collection.Indexer.CollectionIndexerService) on org.bansheeproject.CollectionIndexer
[1 Debug 02:52:52.020] Core service started (CollectionIndexerService, 0.005055)
[1 Debug 02:52:52.022] Core service started (SaveTrackMetadataService, 0.00138)
[1 Debug 02:52:52.029] Adding icon theme search path: /usr/share/banshee-1/icons
[1 Debug 02:52:52.029] Core service started (GtkElementsService, 0.007428)
[1 Debug 02:52:52.031] Core service started (InterfaceActionService, 0.001365)
[1 Debug 02:52:52.117] Extension actions loaded: MetadataFixActions
[1 Debug 02:52:52.117] Registering remote object /org/bansheeproject/Banshee/GlobalUIActions (Banshee.Gui.GlobalActions) on org.bansheeproject.Banshee
[1 Debug 02:52:52.118] Album artwork path set to /home/jason/.cache/media-art
[1 Debug 02:52:52.139] Core service started (ArtworkManager, 0.021476)
[1 Debug 02:52:52.139] Core service started (BookmarksService, 0.000122)
[1 Debug 02:52:52.472] Constructed Nereid interface: 0.309333
[1 Debug 02:52:52.524] Creating new surface cache for 90px images, capped at 0.74 MiB (24 items)
[1 Debug 02:52:52.599] Registering remote object /org/bansheeproject/Banshee/ClientWindow (Nereid.PlayerInterface) on org.bansheeproject.Banshee
[1 Debug 02:52:52.599] Core service started (NereidPlayerInterface, 0.459849)
[1 Debug 02:52:52.617] Extension service started (GStreamerCoreService, 0.017593)
[1 Debug 02:52:52.624] Extension service started (BpmService, 0.006456)
[1 Debug 02:52:52.628] Using GNOME 2.22 API for Multimedia Keys
[1 Debug 02:52:52.628] Extension service started (MultimediaKeysService, 0.003692)
[1 Debug 02:52:52.629] Extension service started (LibraryWatcherService, 0.001442)
[1 Debug 02:52:52.630] Extension service started (DapService, 0.000937)
[1 Debug 02:52:52.633] Extension service started (PodcastService, 0.002332)
[1 Debug 02:52:52.635] Extension service started (CoverArtService, 0.0023)
[1 Info  02:52:52.638] Updating web proxy from GConf
[1 Debug 02:52:52.642] Direct connection, no proxy in use
[1 Debug 02:52:52.656] Extension service started (GnomeService, 0.021226)
[1 Debug 02:52:52.659] Extension service started (AmazonMp3DownloaderService, 0.002317)
[1 Debug 02:52:52.660] Extension service started (DaapService, 0.000927)
[1 Debug 02:52:52.728] Extension service started (NotificationAreaService, 0.067883)
[1 Debug 02:52:52.750] Extension service started (AudioCdService, 0.022436)
[1 Info  02:52:52.751] All services are started 1.002823
[1 Debug 02:52:53.239] Extension source loaded: Now Playing
[1 Debug 02:52:53.247] Extension source loaded: Amazon MP3 Store
[1 Debug 02:52:53.274] Extension source loaded: File System Queue
[1 Debug 02:52:53.277] Extension source loaded: Miro Guide
[1 Debug 02:52:53.562] Registering remote object /org/bansheeproject/Banshee/SourceManager/PlayQueue (Banshee.PlayQueue.PlayQueueSource) on org.bansheeproject.Banshee
[1 Debug 02:52:53.562] Extension source loaded: Play Queue
[1 Debug 02:52:53.584] Extension source loaded: Audiobooks, etc
[1 Debug 02:52:53.588] Starting GTK main loop
[1 Debug 02:52:53.642] Growing surface cache for 90px images to 1.24 MiB (40 items)
[1 Debug 02:52:53.761] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:52:53.781] Creating Pango.Layout, configuring Cairo.Context
[1 Debug 02:52:53.849] Creating Pango.Layout, configuring Cairo.Context
[1 Info  02:52:54.174] nereid Client Started
[1 Debug 02:52:54.177] Delayed Initializating Banshee.MediaEngine.PlayerEngineService
[1 Debug 02:52:54.182] (libbanshee:player) Stream volume supported: YES
[1 Debug 02:52:54.184] (libbanshee:player) Audiosink has volume: NO
[1 Debug 02:52:54.205] (libbanshee:player) Using system (gst-plugins-good) equalizer element
[1 Debug 02:52:54.242] Player state change: NotReady -> Ready
[1 Debug 02:52:54.246] Loaded equalizer presets: 0.000179
[1 Debug 02:52:54.250] Selected equalizer: Rock
[1 Debug 02:52:54.253] Player state change: Ready -> Idle
[1 Debug 02:52:54.255] (libbanshee:player) Disabled ReplayGain
[1 Debug 02:52:54.260] Delayed Initializating Banshee.LibraryWatcher.LibraryWatcherService
[1 Debug 02:52:54.269] Core service started (LibraryImportManager, 0.004559)
[1 Debug 02:52:54.387] Started LibraryWatcher for Music (/media/windows/Users/Jason/Music/iTunes/)
[1 Debug 02:52:54.393] Started LibraryWatcher for Videos (/home/jason/Videos/)
[1 Debug 02:52:54.394] Delayed Initializating Banshee.Dap.DapService
[1 Debug 02:52:54.414] Dap support extension loaded: Banshee.Dap.MassStorage
[1 Debug 02:52:54.415] Dap support extension loaded: Banshee.Dap.AppleDevice
[1 Debug 02:52:54.421] Delayed Initializating Banshee.Podcasting.PodcastService
[2 Warn  02:52:54.435] Failed to load media-player-info file for 
[1 Debug 02:52:54.520] Delayed Initializating Banshee.Daap.DaapService
[3 Debug 02:52:54.620] DAAP Proxy listening for connections on port 8089
^C
jason@Barnaby ~ $
```

Can you tell me what's freezing Banshee? When I tried to load it with *sudo banshee* it loaded, but obviously I don't want to have to load it with sudo every time.

---

### Post by jdorenbush on 2010-09-21
> **slughappy1 said:**
> My Banshee install started to freeze on startup with version 1.7.5. I just updated to 1.7.6 tonight, and it has the same problem. I ran it with the --debug and this is what I got
```
jason@Barnaby ~ $ banshee --debug......
```

Can you tell me what's freezing Banshee? When I tried to load it with *sudo banshee* it loaded, but obviously I don't want to have to load it with sudo every time.


Try removing (move files to your desktop for backup) the three Banshee .dll files from the extensions directory that I listed in this [post]("http://ubuntuforums.org/showpost.php?p=9851690&postcount=11").

---

### Post by JRBye on 2010-09-21
Also if you are uninstalling a problem app it is good to do it from the Shell using Purge.

EX: sudo apt-get --purge remove 'nameofprogramherewithoutquotes' -y

sudo - gives you Super User rights
apt-get - Package manager
--purge - This does a more complete uninstall
remove - tells the package manager to uninstall
nameofprogramwithquotes - is the name of the program you want to uninstall. It may be something odd so you may need to go to the developers site to get the package name or look it up.
-y - Bypasses the 'Are you sure?' prompt.

Then you can run a sudo apt-get autoremove
This will scan all of your packages and come up with a list of 'unneeded' ones and you can choose to remove them. It isn't necessary but it can help in the off chance that one of those packages is causing the issue after your program is installed.

This is a pretty simple overview of this. It is much more complex and has a ton more options. For a more full explanation go to [http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

---

### Post by ibizatunes on 2010-09-21
you could update to 1.7.6
[http://www.unixmen.com/software/1183-banshee-176-is-released-ppa-ubuntu](http://www.unixmen.com/software/1183-banshee-176-is-released-ppa-ubuntu)

---

### Post by ubudog on 2010-09-21
Yeah, that may work.

---

### Post by slughappy1 on 2010-09-22
I'm running 1.7.6 actually. It turns out it's a bug with dbus. If you load it using ```
banshee --disable-dbus
``` then it stops freezing.

---

### Post by ubudog on 2010-09-22
Hmm, are there any updates that may fix it?

---

### Post by slughappy1 on 2010-09-22
I think so. The developers seem really engaged at finding out what my bug was. I would think when the final stable build is released it will hopefully be fixed. Right now you can load it by using the *banshee --disable-dbus* and it should work. Just most of the plugins wont :-(

---

### Post by ubudog on 2010-09-22
That's good.

---

### Post by slughappy1 on 2010-09-24
I just got an email from the bug reporting thing. One of the developers said he has patched that bug and it will be fixed in the next major release. So the one next month or so. I forget exactly when it is supposed to be released.

---

### Post by ubudog on 2010-09-24
Just a little while longer...

---

### Post by SynonM on 2011-06-05
I tried 

```
sudo apt-get install aptitude
```

then
```
sudo aptitude reinstall banshee
```

that worked for me...

also for some reason starting banshee from terminal en debug-- seemed to make it freeze less
it also gave me an idea of what was going wrong or if banshee was doing too much at once.



**banshee --debug**

---

### Post by dave2001 on 2011-10-10
Banshee was crashing for me, instead of freezing. About 3 seconds after being run. I've tried many other "fixes" that did nothing. Removing extensions, as the OP suggested, fixed the problem for me. 

In my case, the only offending extension was the Banshee.Podcasting.dll 

I did not need to remove any others.

---

