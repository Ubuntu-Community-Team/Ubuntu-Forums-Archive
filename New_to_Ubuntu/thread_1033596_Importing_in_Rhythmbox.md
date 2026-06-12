---
title: "Importing in Rhythmbox"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by intense.ego on 2009-01-07
I recently corrupted my computer but I managed to salvage the rhythmboxdb.xml document with the whole rhythmbox database. I reinstalled the OS and put the XML file in the appropriate folder. Rhythmbox will load the database, but will start afresh when I try to play a song and then start scanning for music. I checked the XML document and it seems to add the newly scanned music to the existing database because the document doubled in size after scanning was finished.

I wouldn't normally mind it having to scan the folders again, but I had all the song ratings and I don't want to go through my whole library (40,000+ songs) rating the songs as I go. What do I do? All the song locations are the same as before, so that can't be the problem. Maybe the version I had of rhythmbox earlier is not the same as the one I have now (though it looks the same and I always updated before)?

---

### Post by blueridgedog on 2009-01-07
Just a wild idea: Is the file owned by you and writable?

---

### Post by intense.ego on 2009-01-10
The owner of the file (my previous username) is the same as my current username, and it is set to read and write.

---

### Post by mkvnmtr on 2009-01-10
Maybe I just don't understand but I don't know why you need to save files for configuration. If you have the music files. I just click on import and tell it what files to import and it does it. If I want to move my music directory to another partition or disk I just move it and then open rythembox. It soon finds there are no files. Then I import them again. Am I missing something? Is there something else to save besides the music?

---

### Post by miqu on 2012-09-02
Well the database that has all your ratings and play counts is one thing you want to migrate too when transferring files to a new computer etc.

I had this problem just today. I just copied all the music, the configuration and the database from home/YOU/.local/share/rhythmbox. Then I opened the database file in gedit and find/replaced the file path parts that had changed. 

Now I am waiting on the copy to Finnish, but feel confident that I can soon just continue listening to music on the new computer.

---

