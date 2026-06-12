---
title: "ubuntu tries to destroy my ipod when connected"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-14
sometimes when i try to plug in my ipod to the computer via USB, nothing happens. if i put my ear up to the ipod, i can hear the hard disk inside beating itself up. 

this **never** happens when it's not connected to the computer,
so therefore, this is not a "failing hard disk" issue

what could possibly be causing this? it happens right after the ipod mounts. i am then forced to unplug my ipod before it gets destroyed. 

any ideas???

---

### Post by asuastrophysics on 2009-04-14
i have narrowed it down to rhythmbox. 

i can open up my ipod in nautilus just fine. adding and deleting files works seamlessly.

when i do it in rhyhmbox, some faulty line of code sends a signal to my ipod telling the hard disk to self destruct. (hard disk spins up, disconnects. spins up, disconnects)

---

### Post by aktiwers on 2009-04-14
It's probably just rythembox indexing the files on the drive? Never happend to my old Ipod though, but Rhythembox does this to my HD as well. (loads of reading)

---

### Post by asuastrophysics on 2009-04-14
it doesn't sound like it's indexing anything. that distinctive "loading" noise is absent. it just sounds like the read/write head inside the disk is being thrown around. 

this is the output of rhythmbox:

```
girdy@girdy-desktop:~$ rhythmbox

(rhythmbox:29434): Rhythmbox-WARNING **: Could not open device /dev/radio0
WARN  coherence                   Apr 14 17:09:58  Coherence UPnP framework version 0.5.6 starting... (coherence/base.py:237)
WARN  webserver                   Apr 14 17:09:58  WebServer on port 53951 ready (coherence/base.py:106)
WARN  rb_media_renderer           Apr 14 17:09:59  __init__ RhythmboxPlayer {'shell': <rb.Shell object at 0x24c5e60 (RBShell at 0x1bd80b0)>, 'no_thread_needed': True} (coherence/MediaPlayer.py:33)
WARN  rb_media_renderer           Apr 14 17:10:00  get_volume 0.52631580829620361 (coherence/MediaPlayer.py:357)
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/twisted/internet/gtk2reactor.py", line 226, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.5/site-packages/twisted/internet/base.py", line 705, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 243, in callback
    self._startRunCallbacks(result)
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 312, in _startRunCallbacks
    self._runCallbacks()
--- <exception caught here> ---
  File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 328, in _runCallbacks
    self.result = callback(self.result, *args, **kw)
  File "/usr/lib/python2.5/site-packages/louie/plugin.py", line 103, in called
    return receiver(*args, **kw)
exceptions.TypeError: detected_media_server() takes exactly 3 non-keyword arguments (2 given)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
**
ERROR:gsttagdemux.c:418:gst_tag_demux_trim_buffer: assertion failed: (out_size > 0)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/smil decoder|decoder-application/smil
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/smil decoder|decoder-application/smil (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
**
ERROR:gsttagdemux.c:418:gst_tag_demux_trim_buffer: assertion failed: (out_size > 0)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/x-gst_ff-vc1test decoder|decoder-application/x-gst_ff-vc1test
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing

```

---

### Post by Saghaulor on 2009-04-14
I highly doubt that your Ipod will self destruct.

You may be correct in that unnecessary spinning of the hard disk can diminish its lifespan, but I doubt that it's going to explode or crash into the platter.

Also, more specific information is helpful in diagnosing your problems.

What Ipod do you have?
What version of Ubuntu are you running?
What version of Rhythmbox are you running?

I don't know if I can help you, but the above questions might be helpful to others in diagnosing your problem.

---

### Post by asuastrophysics on 2009-04-14
> **Saghaulor said:**
> I highly doubt that your Ipod will self destruct.

You may be correct in that unnecessary spinning of the hard disk can diminish its lifespan, but I doubt that it's going to explode or crash into the platter.

Also, more specific information is helpful in diagnosing your problems.

What Ipod do you have?
What version of Ubuntu are you running?
What version of Rhythmbox are you running?

I don't know if I can help you, but the above questions might be helpful to others in diagnosing your problem.

sorry i probably should've posted that first. :roll:
BTW, every time it happens, i am forced to unplug the USB cord from it without ejecting it (won't eject; says another application is "using" (abusing) it. 

Ubuntu 8.10;  2.6.27-11-generic 64-bit
Ipod Photo 20GB 90% full
Rhythmbox 0.11.6

Update: Rhythmbox crashed after attempting to delete an album off the ipod
10 seconds later: nautilus has just crashed and i have no desktop icons.

---

### Post by asuastrophysics on 2009-04-14
my ipod just about became a huge paperweight. 

it would show the apple logo, and then start "thunking" again. then it would show the folder with an exclamation point. 
i had to take the ipod apart and physically disconnect and then reconnect the battery. 

after the ipod booted back up to the home screen successfully, i checked the music folder to make sure everything was still there...it was.
i then plugged it into the computer and started rhythmbox. 
i deleted the artist "digible planets" to make room for the "Phish - farmhouse" album. the transfer was successful. 
errrm....dying hardware???   :sad:

would you like me to test this on a different model ipod to confirm
(another non-flash version)?
similarly, should i test my ipod on a windows machine to try to replicate the result? 

now if i could only convince my room mate to lend me his after he just witnessed what happened to mine...:lolflag:

---

### Post by Paqman on 2009-04-14
You could try a different music player (eg: songbird, amarok) and see if it plays a little more nicely with your iPod.

Have a look in Add/Remove, there'll be a whole bunch of music players in there.

---

