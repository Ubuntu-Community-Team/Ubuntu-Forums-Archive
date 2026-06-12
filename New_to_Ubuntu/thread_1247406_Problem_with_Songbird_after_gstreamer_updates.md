---
title: "Problem with Songbird after gstreamer updates"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by catzlai on 2009-08-22
Songbird doesn't start after my system updated the gstreamer plugin to 1.0:

```
(songbird-bin:5091): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgsthdvparse.so': /usr/lib/gstreamer-0.10/libgsthdvparse.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:5091): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstmpegdemux.so': /usr/lib/gstreamer-0.10/libgstmpegdemux.so: undefined symbol: _gst_debug_dump_mem

(songbird-bin:5091): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type

(songbird-bin:5091): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:5091): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libresindvd.so': /usr/lib/gstreamer-0.10/libresindvd.so: undefined symbol: gst_navigation_event_parse_command
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

Any help?

---

### Post by misterniark on 2009-08-24
Same problemes :

```

(songbird-bin:10054): GStreamer-WARNING **: 
invalid name template vc3_video_sink_%u: conversion specification must be of type '%d' or '%s' for GST_PAD_REQUEST padtemplate

././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type

Could not initialize GStreamer: Erreur lors de la nouvelle analyse du registre , child terminated by signal
```

---

### Post by Codix121 on 2009-08-24
Try this:

```
sudo apt-get remove libvisual-0.4-plugins
```

Tell me if you get any luck with it.

---

### Post by misterniark on 2009-08-24
No changes

Thanks

---

### Post by Codix121 on 2009-08-24
Have you tried removing gstreamer and reinstalling?
Not sure what's causing the error, I have gstreamer0.10 and songbird
works just fine.

Try uninstall gstreamer0.10 and reinstalling it.
Are you using Alsa or PulseAudio?

---

### Post by grimblecrumble on 2009-08-24
got the same problem here since the last update
(songbird-bin:12020): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstlibvisual.so': /usr/lib/gstreamer-0.10/libgstlibvisual.so: undefined symbol: gst_adapter_prev_timestamp

(songbird-bin:12020): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstapp.so': /usr/lib/libgstapp-0.10.so.0: undefined symbol: gst_buffer_list_get_type
././songbird-bin: symbol lookup error: /usr/lib/python2.6/dist-packages/gst-0.10/gst/_gst.so: undefined symbol: gst_task_pool_get_type
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by homemadejam on 2009-08-27
Has anyone got a fix for this yet?
I have tried re-installing gstreamer, and songbird, but still no luck at all...

thanks,
Jam

---

### Post by mpurses on 2009-08-29
Hey guys,

You can find the possible workarounds over at the Get Satisfaction thread here:
[http://getsatisfaction.com/songbird/topics/new_ubuntu_gstreamer_stops_sb_from_starting#reply_1336572](http://getsatisfaction.com/songbird/topics/new_ubuntu_gstreamer_stops_sb_from_starting#reply_1336572)

---

### Post by nobodysbusiness on 2009-08-31
Thanks for the link! This got it working on my Ubuntu 9.04 system:

sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad

---

### Post by grimblecrumble on 2009-09-07
> **mpurses said:**
> Hey guys,

You can find the possible workarounds over at the Get Satisfaction thread here:
[http://getsatisfaction.com/songbird/topics/new_ubuntu_gstreamer_stops_sb_from_starting#reply_1336572](http://getsatisfaction.com/songbird/topics/new_ubuntu_gstreamer_stops_sb_from_starting#reply_1336572)

Thanks for that info Michael,removing Gstreamer made it work, no other problem with any other programs.

---

### Post by rockstarmode on 2009-11-03
On Fedora Songbird is distributed with it's own version of gstreamer, look in Sonbird/lib for files that start with libgst*  Removing these files forced Songbird 1.2 to startup and work just fine with the version of gstreamer that I already had installed.

I also posted this proposed solution here:

[http://ubuntuforums.org/showpost.php?p=8229658&postcount=4](http://ubuntuforums.org/showpost.php?p=8229658&postcount=4)

The original source:

[http://changelog.complete.org/archives/1081-songbird-how-to-make-great-software-unpopular](http://changelog.complete.org/archives/1081-songbird-how-to-make-great-software-unpopular)

---

### Post by gfxmonk on 2009-11-21
For me, removing libvisual-0.4-plugins had no effect. I remembered that the only new package I installed today was python-dev (which is a metapackage for python2.6-dev). Uninstalling that did the trick here.

---

### Post by Mattevt on 2009-12-21
> **nobodysbusiness said:**
> Thanks for the link! This got it working on my Ubuntu 9.04 system:

sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad

Thank God! This worked for me!

---

### Post by shiroyoshida on 2009-12-26
I've been having the same problems with the latest version of Songbird (1.4.3) and found this very helpful post: [http://www.jonathanmoeller.com/screed/?p=1228&cpage=1](http://www.jonathanmoeller.com/screed/?p=1228&cpage=1)

On my machine Songbird was installed by using the tarball from the official website. I never had installed Songbird before on my Ubuntu installation. Then extracted the contents to my home folder. After that, I started a new terminal session and did: 

```
cd /home/myUsername/Songbird/lib 
```and then did: 

```
sudo rm -rf libgst* 
```Everything worked perfectly after that. Please note that if you have previously installed Songbird, it will have created the ".songbird2" folder in your home folder. You have to remove that folder first and then execute the commands above. 

**NB**: This is not guaranteed to work on machines that already had a Songbird installation in the past and only refers to new installations. If you want to try any of the above commands, please make sure you have backed up your ".songbird2" folder first.

---

### Post by dalesd on 2009-12-27
Thanks, shiroyoshida, I remember I had to remove those files last time I installed Sonbird, ver 1.2.0.  I did it again and it worked like a charm.

---

