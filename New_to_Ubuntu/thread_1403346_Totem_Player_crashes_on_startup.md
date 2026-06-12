---
title: "Totem Player crashes on startup"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by Ajay Ramaseshan on 2010-02-10
Hello 
I was using Totem Movie player on Ubuntu 9.04 for quite sometime But suddenly it has stopped working.
It now crashes on startup with the message 
Failed to execute child process totem ( No such file or directory)
I have no idea what this is about,.
Should I try uninstall and then reinstalling it?

---

### Post by mwcrowley on 2010-02-10
If this is a file or file format that you have not played before, try VLC.  Xine or mplayer are also good alternatives.  
It is also possible that the file is corrupted and will not play in any player.
If it is a file that you have successfully played before, totem probably did not exit correctly.  Open a terminal and enter killall totem and try it again.

---

