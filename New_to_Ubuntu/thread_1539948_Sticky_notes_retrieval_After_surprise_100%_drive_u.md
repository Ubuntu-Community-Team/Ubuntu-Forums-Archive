---
title: "Sticky notes retrieval? After surprise 100% drive usage warning"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by simontaylor on 2010-07-27
Hi Ubuntans,

It appears it is a registered bug (#61570 in gnome applets) but annoying nonetheless and if anyone knows how to retrieve Sticky Notes please reply:

My disc scan - I was moving material from Home dir to another larger drive at the time - suddenly showed 100% usage... I rebooted, lost connectivity - this is with 10.04 - and all connection settings (shared WEP) - and Computer Janitored and cleaned, autocleaned and autoremoved and went through dependencies and repeated the process to make sure I was not going crazy. No. In fact there were 4 gigabytes free of the 12. 

Other settings were affected, to do with display - sidebars added - and folders were added to Home, both empty, Video and Podcasts, for no apparent reason, but the chief loss was of all my Sticky Notes, which held material I had not replicated elsewhere, having come to rely on what I thought was a dependable tool.

I have looked in /gnome2/applets with gedit but found no clue as to whereabouts of the missing Stickies. Are they gone forever?

Best,
Simon

---

### Post by CharlesA on 2010-07-27
Everything related to your profile is stored in your home directory.

It's likely that they are whereever you moved the files from the home directory.

Did you edit fstab to point to the new location?

---

### Post by simontaylor on 2010-07-27
I was moving files to a Media file and there's no sign there.

Show hidden files>

.gnome2/stickynotes_applet 

shows:

> This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
<stickynotes version="2.30.0"/>

---

### Post by CharlesA on 2010-07-27
What do you mean you were moving them to a media file?

---

### Post by simontaylor on 2010-07-27
196 GB Filesystem

- my partitions are set up very strangely

---

### Post by CharlesA on 2010-07-27
it's more then likely that the notes were moved along with some of the other files in your home directory.

If you really want to move your /home directory to a different disk, check this out:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by NFblaze on 2010-07-27
Hey simontaylor, I've had this problem twice or three times now. Stickynotes has on many occcasions disappeared or deleted my notes for no apparent reason. Though at least the current version it has done that yet, though it would be best if you migrate to Tomboy. It's a lot less instant, but it's much better for backups. Plus, you'll have a second failsafe to sync them to UbuntuOne


The first thing I do in these instances is download photorec [sudo apt-get install testdisk]

In the program lauch photorec from a terminal. I'm not in front of my PC right now, but you can navigate how to use it. It would be best if you disable trying to recovery of everything that isnt an textfile,html,or xml. I'm not sure which one it is. 

Anyway recover it up to something like an external hard drive (in my case it's /media/TOSHIBADRIVE/). 

Once the program is done you should see alot of recup_.dir. Count em change. In my instance, I had 14 (hence line 6). Though you can modify that. 

You can then try running this script (no guarantees that it will function properly you might have to tweak i, as I havent used it in a while).

```

#!/bin/bash

n=1
recpath=/media/TOSHIBADRIVE/recup_dir.

while [ $n -lt 14 ]
do
   currdir=$recpath$n
   
echo "THIS IS THE CURRENT DIRECTORY ~~~~~~\n $currdir ~~~~~~~" >> ~/greppdnotes.txt
   
cd "$currdir"

cat *.xml | grep -Hn stickynotes >> ~/greppdnotes.txt

done
```

In essence if I remember correctly, this script should iterate thru all the xml files in the "recup_dir" directories. It will then cat each file for the stickynote heading and should spit out the path to your home directory greppdnotes.txt

You can then manually inspect each file and copy it to a backup.

---

### Post by Leeteq on 2010-12-10
Ref. this ongoing issue: "All sticky notes are erased"
[https://bugs.launchpad.net/gnome-applets/+bug/61570](https://bugs.launchpad.net/gnome-applets/+bug/61570)

---

