---
title: "&quot;Transport endpoint is not connected&quot;"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by suitedaces on 2009-03-27
Hi, I'm getting this error with my samsung yp-k3 mp3 player:

Error stating file '/media/samsung/Music': Transport endpoint is not connected

I originally connected it using this post: > **MicahCarrick said:**
> Here's some of what I've learned in Ubuntu 8.04 with my Sansa View...


**MTP Mode**
To use the default MTP (Microsoft Transfer Protocol) mode, you need to download libmtp. It might be useful to download mtp-tools and easytag in case you have problems or want to fine-tune things.

```
sudo aptitude install libmp3 easytag mtp-tools
```

Then, you can use it with Rhythmbox by enabling the 'MTP Portable Devices' plugin. This is in 'Edit' > 'Plugins'.

The mtp-tools will give you command-line access to your device. This is a good way to make sure libmtp is working. Type 'mtp-detect' to get a bunch of info about your device. Type 'man mtp-connect' to see a list of all the commands you can use.

If you want to actually mount the device like a filesystem in MTP mode, you can use mtpfs. When I tried this, it was kind of buggy but worked. 

```
sudo aptitude install mtpfs
```

Mount your device:

```
mkdir /media/SansaView
sudo mtpfs -o allow_other /media/SansaView
```

Unmount your device:

```
sudo fusermount -u /media/SansaView
```

I have had trouble working with playlists and albums using MTP mode with Rhythmbox, Amarok, etc. Aside from that, I kind of what an interface to directly organize the Sansa View, without syncing it or including it with my computer's media (mainly because it allows my girlfriend to manager her playlists without effecting my stuff--she's not computer savy). 

Therefore I'm currently working on a GTK-based music organizer for MTP based devices; create and edit playlists, specify album art, etc. (testing it with my Sansa View) It is going well and should have some downloadable files within a couple weeks. I'll update when the project page is up.


For a while it was great, I could mount and unmount using the commands, and successfully drag and drop tracks. Now I think I can still mount it (the player says mtp connected, and I can access all the files. However, when I try to do anything, I get the "Error stating file '/media/samsung/Music': Transport endpoint is not connected message"

I can't think off-hand of anything I have done differently.

---

### Post by suitedaces on 2009-03-27
Oh, and I should add, after saying mtp connected, when I get the error, it has changed to just "usb connected, charging".

---

### Post by stderr on 2009-03-27
I have no experience with that mp3 player, but I bumped into [this]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/181977") which looks quite similar. The last posts hint at some possible success using newer versions of libmtp8 and mtpfs (at least 0.3.3 and 0.9 respectively). I think Intrepid is using 0.3.0 and 0.8.something at the moment, so this may help. You'll probably need to grab latest versions from CVS/SVN and build them from source though.

---

### Post by suitedaces on 2009-04-02
How would I do that? I thought I had got it sorted. I dragged a folder of music across, then halfway through the transfer I suddenly didn't have permission again, and it gave me the same enddpoint error message. But funniy enough the player now says "synchronising"

---

### Post by suitedaces on 2009-04-20
Was offline for a few weeks. Can anyone help me with this yet?

---

### Post by kevin01123 on 2010-04-19
Doesn't work for me either. Same error.

---

