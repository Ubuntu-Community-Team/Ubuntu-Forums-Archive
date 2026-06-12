---
title: "Chromium Browser doesn't start up"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by life_pudding on 2010-04-09
When I click to start the Chromium Browser, a tab opens up on the bottom of the screen, the pointer turns to a timer, and about 15 seconds later both the timer and the tab go away.  No screen is opened up.  While I would like to fix this, I especially would like to get a record of my bookmarks.

I am using Ubuntu 9.04.  It has been doing this for about 10 days.  I have updated the browser with update manager a few times and no change.  I have not looked at an errorlog because I am not sure where it is.  So I would also like to know where the errorlog is.

I have been using the browser without problems for about 6 months

Thanks.

---

### Post by Paqman on 2010-04-09
Open up a terminal and launch it with the command:
```
chromium-browser
```
then copy and paste the errors it spits out into a post here.

---

### Post by life_pudding on 2010-04-09
> **Paqman said:**
> Open up a terminal and launch it with the command:
```
chromium-browser
```then copy and paste the errors it spits out into a post here.

chromium-browser
[30746:30761:77897120192:FATAL:chrome/browser/sync/syncable/directory_backing_store.cc(193)] file is encrypted or is not a database
Aborted


The response was immediate

---

### Post by life_pudding on 2010-04-09
> **life_pudding said:**
> chromium-browser
[30746:30761:77897120192:FATAL:chrome/browser/sync/syncable/directory_backing_store.cc(193)] file is encrypted or is not a database
Aborted


The response was immediate


Doing this allowed me to search on chrome/browser/sync/syncable/directory_backing_store.cc to locate this:

[http://www.google.com/support/forum/p/Chrome/thread?tid=76aeb4b5296d4441&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=76aeb4b5296d4441&hl=en)

In this thread it said to do this

rm -rf ~/.config/google-chrome/Default/Sync\ Data/ 

That did not work but something very similar did

Basically I went to this directory

~/.config/chromium/Default/Sync\ Data

and did this to delete one of the files:

rm Sync*



And now it works.

Thank-you for the command line suggestion.

---

