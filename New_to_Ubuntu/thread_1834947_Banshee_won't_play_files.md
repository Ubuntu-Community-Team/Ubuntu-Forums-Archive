---
title: "Banshee won't play files"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by pckrfan75 on 2011-08-28
So when I open up Banshee, all my music is there. I have mp4, mp3, and just about all types of music file but none of them will play. I have done everything I have found in other threads, the dependency tree, the codecs, plugins, restricted extras. Not sure what to do anymore. It doesn't give me any errors, it just doesnt play. I double click and nothing happens. Any tips?

---

### Post by mr_bigmouth on 2011-08-28
I have almost the exact same problem. Help???????

---

### Post by kyletstrand on 2011-08-28
Hello,

Are you getting an X next to the file you are trying to play?  

Try opening banshee in a terminal and post the output there, we can see if it's getting any errors from start up.

```
$banshee-1
```

---

### Post by mr_bigmouth on 2011-08-28
This is the error I'm getting, and it shows up whenever I press play on ANY music file (none of them have red X's next to them btw)

```
[Error 10:14:32.243] GStreamer resource error: NotFound

```

---

### Post by kyletstrand on 2011-08-28
Try deleting your banshee database file located in 

```
~/.config/banshee-1
```

Then re-import your files and reboot.

It seemed to solve that error in this thread:
[http://forum.foresightlinux.org/index.php?topic=445.0](http://forum.foresightlinux.org/index.php?topic=445.0)

---

### Post by mr_bigmouth on 2011-08-28
I tried that and it didn't do anything.

EDIT: Never mind. I somehow tricked it into working.

---

### Post by kyletstrand on 2011-08-28
Do you have any other media players? Do those play files?

---

### Post by Cloudy Brain on 2011-08-28
Hi, I had the same problem on my laptop, Natty 11.04 64bit. This was the first time I used banshee on it today. I imported ~3000 files over nfs and it was happy to show file properties but not play. I could play files through Totem Movie Player so it wasn't a general problem with audio or (presumably) codecs . I installed ubuntu-restricted-extras just in case but this didn't make a difference.

Starting banshee on the command line I got the following:
```

mike@Artemis:~$ banshee
[Info  20:36:49.152] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, x86_64) @ 2011-06-28 05:39:10 UTC]
[Warn  20:36:49.589] No player engines were found. Please ensure Banshee has been cleanly installed. - Using the featureless NullPlayerEngine.
[Warn  20:36:49.608] Service `Banshee.Hardware.HardwareManager' not started: No HardwareManager extensions could be loaded. Hardware support will be disabled.
...

```I went to the banshee website and saw that there is a slightly newer version, so following their advice added the Banshee Team PPA:
```

sudo add-apt-repository ppa:banshee-team/ppa

```Then when I forced an update check through the Update Manager a load of dependencies popped up, some from the ppa. I just updated everything and now I've got a working banshee 2.0.1:
```

mike@Artemis:~$ banshee --version
Banshee 2.0 (2.0.1) http://banshee.fm
Copyright 2005-2011 Novell, Inc. and Contributors.

```Hope that ramble helps someone :)

---

### Post by pckrfan75 on 2011-08-29
```
[Info  23:46:24.351] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  23:46:28.864] Updating web proxy from GConf
[Info  23:46:28.935] All services are started 3.82385
** (Banshee:3490): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3490): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:3490): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/joe/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:3490): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:3490): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:3490): DEBUG: Loading the real store page

** (Banshee:3490): WARNING **: Got less number of items in credentials hash table than expected!
[Info  23:46:31.742] nereid Client Started
[Info  23:46:31.998] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  23:46:32.120] AppleDeviceSource is ignoring unmounted volume OS

```

---

### Post by john3paul on 2011-10-20
I had the same problem,Banshee wouldn't play the songs that were clearly in its library, running Natty Narwhal on a 1005HAB eeePC. I erased all the songs (within Banshee), then re-imported the song files, and it worked immediately. thanks, everyone, for your help and input! JP

---

### Post by sporksrule on 2012-01-01
I tried multiple different ways to fix the problem. Not sure which one did the trick, but when I deleted the files from banshee and then imported them again it worked!

---

