---
title: "Multiple app install, how do I remove them?"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by quantum11 on 2011-05-30
Hey,

I recently tried in install Buzan's imindmap on Ubuntu 11.04, I downloaded the .sh file from the website, and when I tried to install it it told me I needed /usr/share/ThinkBuzan with full permissions. I'm a newbie at this and ran the installer multiple times.. now it seems to have installed it multiple times as there are 5 imindmap icons in the unity application search function. How can I remove the other 4? :(

---

### Post by I8NY on 2011-06-02
there should be a uninstall sh file that they offer.  if they don't have one then you will have to look through the sh and remove all the files it creates.  now for the full permissions issue.  run "sudo chmod 777 /usr/share/ThinkBuzan" and that will give root, you, and guest (so full access) full persimmon on that folder.

---

### Post by rogere84 on 2011-10-26
> **quantum11 said:**
> Hey,

I recently tried in install Buzan's imindmap on Ubuntu 11.04, I downloaded the .sh file from the website, and when I tried to install it it told me I needed /usr/share/ThinkBuzan with full permissions. I'm a newbie at this and ran the installer multiple times.. now it seems to have installed it multiple times as there are 5 imindmap icons in the unity application search function. How can I remove the other 4? :(

I know this might be WAY too late for a reply, but just found this post. It's easy. I just did it myself:

Run this in terminal:
> sudo rm -rf /home/YOURUSERNAME/.local/share/applications/iMindMap*

This basically removes all files starting with iMindMap in the applications folder where these icons reside.

---

