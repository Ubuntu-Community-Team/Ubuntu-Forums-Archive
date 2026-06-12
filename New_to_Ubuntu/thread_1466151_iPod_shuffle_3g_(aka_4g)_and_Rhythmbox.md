---
title: "iPod shuffle 3g (aka 4g) and Rhythmbox"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Rusty023 on 2010-04-30
Hi.

I'm running Lucid, and Rhythmbox recognizes my iPod shuffle, however it displays no songs.  I can look through the filesystem to find tracks, Floola sees them (but floola won't play audio on my 64-bit system), and gtkpod sees them (but it's bad as hell for playing audio).

Does anyone know how I can get Rhythmbox to find the tracks on the iPod?

Thanks.

---

### Post by madjr on 2010-04-30
you may want to check if it has already been reported :)

and
[http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html](http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html)

---

### Post by Rusty023 on 2010-04-30
> **madjr said:**
> you may want to check if it has already been reported :)

and
[http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html](http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html)

I did check.  Someone must have some solution for this.

---

### Post by Jason Quinn on 2010-06-06
I was having many troubles with my 3g Ipod Shuffle. Rhythmbox saw the Ipod but wouldn't let me see the files or copy files to it. In desperation, I tried Floola. Floola was able to read the device but couldn't play the files. But afterwards -- wa-la! -- Rhythmbox was able to operate on the Ipod without trouble! Try running Floola and see if it just fixes whatever problem you have.

---

### Post by Jason Quinn on 2010-06-16
> **Jason Quinn said:**
> I was having many troubles with my 3g Ipod Shuffle. Rhythmbox saw the Ipod but wouldn't let me see the files or copy files to it. In desperation, I tried Floola. Floola was able to read the device but couldn't play the files. But afterwards -- wa-la! -- Rhythmbox was able to operate on the Ipod without trouble! Try running Floola and see if it just fixes whatever problem you have.

I was wrong about this. It fixed only the read-problem. I was able to copy songs to the device and play them using Rhythbox but the iPod does not function as a mobile music device. If you try, it say that you need to sync the music with iTunes.

---

### Post by kelvin.illa on 2010-07-04
> **Jason Quinn said:**
> I was wrong about this. It fixed only the read-problem. I was able to copy songs to the device and play them using Rhythbox but the iPod does not function as a mobile music device. If you try, it say that you need to sync the music with iTunes.

Yeah, me too. I got really excited by the Floola thing. It generated a music library similar to how the 3g does it, so I thought "wow, this is sure to work" -- it didn't work. Like you said, it's just a 'read' issue; the iPod won't play because it's says it's not synced to iTunes.

I'm sure this'll get fixed, if not soon, then eventually at least. Floola was close but the iPod refuses its configs. Too bad it won't be much help to the development of similar projects as it's 'closed-source' (correct me if I'm wrong).

---

### Post by Neobuntu on 2010-12-30
By downloading a i-tune "fudged" control folder first, and replacing the brand new one with it (and clearing the entire drive), I was able to get (STABLE) Floola to work (play a song portably), by adding one song, and then restarting it. 

However, it's buggy and does NOT really work; because it will not speak the title names, and it's a pain in the ice, to add songs. Also, the Floola conversion did NOT work on all files, in an album.

Then, Rythmbox trashed it. (Because Apple keeps altering the I-pod data format) 

Just not, worth the time.

---

### Post by Neobuntu on 2011-01-09
..but I made the #@%# thing work (no title voice).

I think the "Go get reamed with itunes" message (on the portable player) comes back, if you don't unmount the idiot-Pod.

Rather than put Floola on the Ipod itself, Just put it on the computer you use. If you find yourself on a Windows, or Mac box, you'll need to download those versions, of Floola, anyway. this way, you can hold down shift when you close Floola, and that will unmount the ipod for you. 

What's cool then, is you can set your Ubuntu computer to auto-load Floola; from it's new home. It's quite entertaining to just insert the ipod (shuffle) and see Floola, just pop-up. Floola lets you copy songs, in and out; working around the stupid proprietary ipod (NEW) song library system.

You can make play-lists, and they do read as voice; the last one you make, saying,"Play list 1", etc... 

Plus it has a fix the (proprietary and fragile) library utilities, in the advanced menus.

The new Shuffles still don't have a read out, radio reception, and mainly, not even default MP3 playing (without prep). 

i-pods suck; ...DRM pieces of poo.

---

### Post by Bernhard.Wernitznig on 2011-02-10
I had the same problem with shuffle 3g. In  amarok I can't access the files and gtkpod refused to do 
anything on the itunesDBfiles. 
 
As soon as I succeeded adding files to the ipod (in software under linux), it won't work any more stand alone. . 

Any news about this issue?
I should use it as an expensive memory stick then.. 

best b.

---

### Post by Neobuntu on 2011-07-22
I've managed to get them to work (no song title voice) just fine (and with play-lists), with Floola, as describe above. It's just ridicules, that one has to do it. 

Apple stinks, and clearly, is not in a consumers best interest. We should be able to drag over songs, and be done. However, Floola lets you convert them over, anyway. 

Again, I got around, the need to plug it into itunes by down loading that already "ituned" control folder, and with one song, to start. 

Plus, hold down that Shift-key (a shortcut), as you close Floola, to make sure the device, is unmounted properly. Else, it will start (only) asking you to put it into itunes, again!

If you put it into itunes, there no telling what apple will do to it. If you test with Rhythmbox, and it's not fixed yet (it may be fixed now), it will trash you ipod files! This is due to Apples constant format changes.

**Note:** Once you get it right, you can back up the whole (drive) mess. This will allow you to quickly transfer it to another, twin ipod, or quickly restore, the one you've got, without all the fuss.

---

### Post by videonaut on 2011-09-24
Hi,

I've tried Floola as well as Rhythmbox to get a 4th gen shuffle to work. Rhythmbox sees the iPod but won't let me do anything to it, and Floola doesn't see it at all.

What steps did you take to get Floola working? 

Also, how do you set Ubuntu to "auto-load" Floola?

Thanks.

---

