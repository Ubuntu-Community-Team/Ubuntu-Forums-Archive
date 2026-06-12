---
title: "Looking for a command"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by Speedwagon on 2010-11-10
I have a bunch of flac files on my computer.  I couldn't find anyway for Rythmbox to convert them on the fly to sync them with my phone.  Instead, I found the program SoundConverter, and converted all the flacs to MP3 files.  My goal here is to have the FLACs as backups, should anything happen to my CDs.

However, apparently I did something wrong in the settings, and instead of putting all the MP3 into a different folder, it intermixed the MP3 files with the FLAC files.

My question:  Is there a command that I can use in a terminal window, that will go through the FLAC folder, and move all the MP3 to a different folder?  It needs to search subfolders too.  But I'm ok with it putting all the MP3s into the same folder.

---

### Post by SlugSlug on 2010-11-10
find . -name '*.mp3' -exec mv '{}' ../mp3/ \;

you'll need to make a folder called mp3 next to your flak folder (on same level)

---

### Post by Speedwagon on 2010-11-10
That worked beautifully, thank you!

---

