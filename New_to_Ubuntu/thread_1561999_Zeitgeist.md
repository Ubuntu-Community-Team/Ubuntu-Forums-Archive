---
title: "Zeitgeist?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by vivek40 on 2010-08-27
Hii ..I am using Lucid and  I just installed Zeitgeist using the below commands:-
sudo add-apt-repository ppa:zeitgeist/ppa
sudo apt-get update && sudo apt-get install zeitgeist gnome-activity-journal

and I went to accessories>activityjournal and there it was... but the activity journal was empty.. I mean the dates are shown but there is nothing under them. I have never used Zeitgeist and dont know how to use it.. could someone please help me with installing it .. am i doing something wrong or is it supposed to be like this ...
Regards
Vivek

---

### Post by Deadite81 on 2010-08-27
You have to give it data to collect. If you just installed it then it hasn't had time to collect any information.  try opening a few text files and movies then open the activity journal.  They should be there.

---

### Post by vivek40 on 2010-08-27
Ok fine that worked.. but does it not log any website activity and how does it enable tagging and all

---

### Post by Deadite81 on 2010-08-27
It's still a new program under heavy development.  With the vanilla Activity Journal it will only log regular local files for now.  However, you can set it up to log all kinds of other stuff.  If you use Chrome/Chromium or Firefox you're in luck, but it's a little tougher because you have to compile each extension.  There is a whole bunch of these extensions, called "Data Providers", for a bunch of programs.  A good place to start is here, which is where I learned about them.

[http://www.webupd8.org/2010/07/install-sezen-applet-zeitgeist-search.html](http://www.webupd8.org/2010/07/install-sezen-applet-zeitgeist-search.html)

[http://www.webupd8.org/2010/07/chrome-extensions-for-sezen-zeitgeist.html](http://www.webupd8.org/2010/07/chrome-extensions-for-sezen-zeitgeist.html)

You will need the "Sezen" panel applet, which you can get from the WebUp8 "Unstable" PPA.  (It also has the updated versions of other programs, like Rhythmbox, Audacious, and Midnight Commander).  I use both their repos and rarely have issues.  Anyway, tool around that website and get aquainted with the command line and Bazazr.  Better sooner than later!

I'm not sure what you mean by tagging.  If this is a feature you've heard about it might not be implemented yet, because as far as I know there's no tagging, like you would tag a bookmark.  It does integrate with other programs automatically though, like gnomenu, AWN, Docky, and DockbarX to name a few.

---

### Post by Rytron on 2011-02-15
Hi. Does Zeitgeist automatically update after each reboot or login?

---

