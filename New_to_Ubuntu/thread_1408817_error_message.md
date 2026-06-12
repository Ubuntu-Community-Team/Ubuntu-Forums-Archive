---
title: "error message"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by misswham on 2010-02-16
I have tried to turn off the update notification but cant.  Still every 10 mins a red circle with a black exclamation point in the middle shows up in my toolbar at the bottom.  When I double click, the update screen pops up and when I click on update it tells me system is up to date.  This has been going on for 3 weeks now and I noticed that when this started happening my system has been acting funny.  It seems to run slower from time to time, pages closing at random, pidgin turning off at random etc.  Now this time this error message came up when I double clicked the red circle

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/hardy/Release](http://repository.cairo-dock.org/ubuntu/dists/hardy/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

What does it sound like is going on?  It is acting as if I have a bug or something.

---

### Post by bwhite82 on 2010-02-16
The cairo-dock repository has changed to glx-dock.org, check this page in the wiki to update your sources.list:

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

