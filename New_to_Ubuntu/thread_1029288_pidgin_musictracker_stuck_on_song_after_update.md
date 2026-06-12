---
title: "pidgin musictracker stuck on song after update"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by cisforcojo on 2009-01-03
I recently upgraded my pidgin version to the version on GetDeb and that broke my musictracker plugin. I then removed it (sudo apt-get remove --purge pidgin pidgin-data pidgin-musictracker) and reinstalled from the repos. For some reason, my music status refuses to change. I should also note that it doesn't completely purge the software. It always remembers my pidgin and musictracker settings. Any ideas???

---

### Post by khc on 2009-01-03
Because of the numerious bugs that musictracker has, I've written a dbus script that listens for changes from rhythmbox/quodlibet and updates such info to pidgin, it can be found at [http://pidgin.im/~khc/now_playing.py.txt](http://pidgin.im/~khc/now_playing.py.txt)

I don't use it myself, but feel free to let me know if there are bugs. I am khc on #pidgin.

---

### Post by cisforcojo on 2009-01-11
*Bump*

Thanks for the python script but I'm looking for a direct solution. I'm pretty curious to figure out where pidgin is being told that I'm playing the same song.

---

