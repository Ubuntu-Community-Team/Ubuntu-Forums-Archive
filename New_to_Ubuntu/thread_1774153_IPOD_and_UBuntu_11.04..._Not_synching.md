---
title: "IPOD and UBuntu 11.04... Not synching"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by berberry08 on 2011-06-02
having problems getting my ACER netbook to read my IPOD 6th or 7th gen 8 gb. Not sure what to do! It lights up but its not reading it in Banshee... Suggestions?

---

### Post by lifelike27 on 2011-06-02
Use Rhythmbox. Not sure about Banshee's support for iPods.

---

### Post by berberry08 on 2011-06-02
that isn't working either.....

---

### Post by wolfen69 on 2011-06-02
Install ifuse and gtkpod. Gtkpod is the app used for syncing.

---

### Post by moboticdes on 2011-06-03
You should be more specific on the model, you should open it as a usb drive and read the file DeviceInfo.xml in the System folder of the ipod.

Anyway let's clear this once and for all:

Banshee, Amarok and GtkPod cannot sync library with generation 6th 7th or 8 ipods!
Banshee can mostly only play the music already in the ipod!
For some compatible ipod players see this compatibility list: [http://wiki.songbirdnest.com/Docs/IPod_Device_Support](http://wiki.songbirdnest.com/Docs/IPod_Device_Support)

You won't get any better than that. THAT'S WHY YOU SHOULD AVOID APPLE STUFF EVEN MORE THAN WINDOWS ONE! THEY HAVE NOT YET LEARNED TO PLAY ALONG WITH OTHERS...

Now to the solution, forget banshee gtkpod or amarok or rhythmbox as they all don't support syncing, forget about using wine to install iTunes and sync as wine doesn't support usb tethering.
The only working solution is:

1. install windows xp in virtualbox
2. activate usb detection
3. install iTunes and sync from there.

I know it sucks using an entire virtual machine for such a stupid job but again thank those people who dont want to make life easier but only to earn some big money with their proprietary software! 
Hope this has finally cleared the state of things

---

### Post by robsoles on 2011-06-03
+1

Apple's EULA comes across as, at least, slightly more *limiting* than Microsoft's as well. Been a while since I read either though!

---

### Post by mbroshi on 2011-06-10
I had problems with my iPod after switching to 11.04 and Banshee, too.  If you have access, I restored my iPod through iTunes on a friend's Windows machine...but still had problems.  Then, I re-restored it and also added a song through iTunes,  Now it works.  Hope that helps.

---

### Post by Macskeeball on 2011-06-11
> **moboticdes said:**
> You should be more specific on the model, you should open it as a usb drive and read the file DeviceInfo.xml in the System folder of the ipod.

Anyway let's clear this once and for all:

Banshee, Amarok and GtkPod cannot sync library with generation 6th 7th or 8 ipods! [...]

The OP wrote 8GB, so that was the storage capacity, not the model number. There's no such thing as a 7th gen iPod. It may be a 6th gen nano, which is the current model. Very small (not much bigger than a shuffle), with a square touchscreen (4 icons) instead of a clickwheel. No camera and no video.

 Does that description sound right, berberry08? If not, follow moboticdes' instructions above.

---

### Post by deckoff on 2011-07-07
Floola works for me for iPod 6gen 120 GB.... Works fine except the sync option, You can add music manually in a way no worse than iTunes

---

### Post by moorer21 on 2011-08-04
The problem is not just with iPod (even though I don't like apple either).  I have a Philips GoGear Raja.  It is having the same issues as described above.  Ubuntu 11.04 mounts it, but neither Banshee 2.0.0 or Rhythmbox 0.13.3 recognize it.  Nor, does my iPod.  They do recognize my Droid X though.

Any thoughts?  Running iTunes in any way as a work around is just a stupid idea, as it is just as limiting as not being able to use the device at all.

---

### Post by moorer21 on 2011-08-04
Floola works if you're music library is smaller then 10 songs.  Anything larger than that and it chokes.

---

### Post by wildflower1975 on 2012-02-19
I'm using Banshee 2.2.1 and can manage to drag and drop tracks from Banshee onto my ipod 4-5th gen  (it has a video camera on it).

I can drag and drop a Banshee playlist on to the Ipod too.

I can't get the automatic Sync option in banshee to work though,
I've got this bug/problem with the display of Playlists which may have something to do it
[https://bugzilla.gnome.org/show_bug.cgi?id=639947](https://bugzilla.gnome.org/show_bug.cgi?id=639947)

---

### Post by |{urse on 2012-02-19
I know i'm not helping you by telling you this but ipod support is so hit or miss with ubuntu, it either works the first time or sporadically works and you end up having to factory reset.

I have a ipod touch 4g (ios 5.0.1) I would love to see it work with Ubuntu but I don't feel like installing a bunch of weird depends that work only halfway or mangle my db.

XP in a vm or dual boot.

:(

---

