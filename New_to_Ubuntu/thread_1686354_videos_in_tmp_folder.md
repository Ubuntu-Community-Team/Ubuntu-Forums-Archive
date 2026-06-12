---
title: "videos in tmp folder"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by emt_90 on 2011-02-12
The other day I discovered the .thumbnails folders where all the pictures I viewed were saved in this folder, there were 70,000 pictures in the folder and I did a big clean out of it. 

I searched on google to see what's the best way to stop those thumbnail folders from saving pictures everytime I view one and I found that this code: "find ~/.thumbnails -type f -atime +7 -exec rm {} \;" would help clear the .thumbnail folders after 7 days. I also went into edit>preferences and changed some options in the preview tab making sure files smaller than 500KB would show.

This I'm happy with. But usually I go into the tmp folder and save videos I watch on my browser. Now after changing those options and putting that code in the terminal, the videos won't seem to show up in tmp folder now after I made some changes. I'm not sure if it's related to the changes I made, but I went back to file management preferences and changed the options to the way it was before as default. But I don't know anyway to take back the code I put in terminal.

Can anyone tell me what I can do to be able to view videos in tmp folder again please?

---

### Post by Vaphell on 2011-02-12
these 2 are completely unrelated.
which browser? firefox? videos like youtube? Some time ago default directory storing temporary files has changed, possibly after some flash update.
Check if the videos don't appear in ~/.mozilla/firefox/<gibberish>/Cache by any chance (.mozilla is hidden so ctrl+h to see it in your home directory)

---

### Post by emt_90 on 2011-02-12
Oh wow I never discovered this folder, it's got the videos saved that I'm currently watching on youtube! I just remembered something, the update manager box popped up the other day and there's been some updates on there, so I guess the changes were made after having that done. Thanks a lot Vaphell! :D

---

### Post by Paqman on 2011-02-12
One thing to be aware of is that the behaviour of /tmp and your home folders is different. /tmp gets wiped clean every time you boot up, so it won't have anything in it from the last time you had the machine on (unlike your .thumbnails folder, which will)

---

### Post by chetancrasta on 2011-02-24
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

