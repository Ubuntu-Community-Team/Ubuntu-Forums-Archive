---
title: "Getting iPhone 2G 3.1.2 to sync"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by thejakeman on 2010-04-29
Can it be done? I'm running Ubuntu 10.04 and am willing to install anything that will enable iPhone support. I don't care about apps or photos or anything, just music and movies.

I haven't tried this yet for fear of something bad happening to the iPhone filesystem.

Thanks!

---

### Post by aysiu on 2010-04-29
I thought 10.04 comes with libimobiledevice

I don't know about syncing, but you should be able to add songs and files to your iPhone.

---

### Post by thejakeman on 2010-04-29
I tried using RhythmBox to add a file but it didn't show up in the iPhone's iPod program... What do I do?

---

### Post by aysiu on 2010-04-29
From [the libimobiledevice website](http://www.libimobiledevice.org/): > **I can see my iPhone/iPod Touch in Rhythmbox, move over music and I know it is was copied to the device but it never shows up on the device!**
Make sure you see the "Sync in Progress" screen on your device before unplugging it. It is that screen which will make your device recognize the tracks you copied over. Unplugging the device earlier will leave the files on the device, however never update the device media player's music database. Currently Rhythmbox does not have an optimal workflow syncing the changes and this is being worked on (like syncing directly after all tracks are finished copied). Also make sure you have an "iTunes_Control/Device" folder. If not, follow step 5 from here.

---

### Post by ttshivers on 2010-04-29
> **thejakeman said:**
> Can it be done? I'm running Ubuntu 10.04 and am willing to install anything that will enable iPhone support. I don't care about apps or photos or anything, just music and movies.
 
I haven't tried this yet for fear of something bad happening to the iPhone filesystem.
 
Thanks!
 
So you can manage your iPhone with Ubuntu.  I though that iPhones only worked with Windows.
[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

