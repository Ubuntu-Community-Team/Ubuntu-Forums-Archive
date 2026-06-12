---
title: "Sound working but not the best quality"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by ChemShock on 2009-03-24
First off, this is my absolute first post and I installed Wubi about 2 days ago.

I found articles and some forum posts about sound packages to be installed but I still have an issue with sound playback.

There is a "snow" type sound coming from my speakers, mostly from my left. I adjusted the PCM in the volume control options, but it only rid most of it. The more complex the sound is (ie Evanesance, Green Day, and others) the music sound like crap.

Also, Wubi install 8.10.

---

### Post by markbuntu on 2009-03-24
If your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```


You should also check that your users and root are members of the following groups which you can check in System/Administration/Users and Groups since these sometimes are removed with updates.
pulse
pulse-rt
pulse-access

There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you.

---

### Post by mgmiller on 2009-03-24
For the benefit of the OP who seems to be a newbie, a little clarification of the previous posters instructions may be helpful.

There are 2 methods, the first is quick and easy, the second is a little less quick and a little less easy, but not by much.

First Method:
Bring up the run command by hitting alt/F2

in the command box at the top, enter the following:
```
gksu gedit /etc/pulse/daemon.conf
```

Give it your regular password when prompted.

The lines you want to change are at the very bottom of the file.

Just click save and you should be done.  You may need to log off and back on to get it to work right.


2nd Method:
If you really want to get safe about the whole thing, with a failsafe backup, here is what you do instead:

Open a terminal:
Applications > Accesories > Terminal

In the terminal, first we create a backup of the original file:
```
sudo cp /etc/pulse/daemon.conf /etc/pulse/daemon.conf.backup
```

Next, in the same terminal, you can edit the file:
```
gksu gedit /etc/pulse/daemon.conf
```

Save it and log off and back on as before.

If things get really frakked, then in the terminal, restore the backup by entering:
```
sudo cp /etc/pulse/daemon.conf.backup /etc/pulse/daemon.conf
```

---

### Post by ChemShock on 2009-03-24
Thanks for the fix. Unfortunately, that fixed the output but my left sound quality is poor. In a way it got worse, I can live with it but it would be nice to have stereo sound. I didn't create a backup.

---

### Post by mgmiller on 2009-03-24
I don't know what your original values were, but this is what I use and my sound is perfect:
```
default-fragments = 8
default-fragment-size-msec = 10

```

The other thing you can try is going to: System > Preferences > Sound and in the drop downs for sound events, music and movies and audio conferencing, instead of the default of "Autodetect" try changing it to Alsa and then hit the Test button.  That clears up a lot of sound things for people.

There are also a lot of other choices in the drop downs that you can try as well.

That being said, pulse audio is the future and it would be nice if you could get that to work properly.  You may find it gets fixed for you in 9.04.  

For me it was horrible in 8.04, but was perfect in 8.10.

---

### Post by ChemShock on 2009-03-26
Hey mgmiller, those are the default settings. 

I found some fixes and I haven't gotten to them all to see what works. So far the fixes here have steadily gotten better.

I found this post: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

This weekend I might try it.

---

