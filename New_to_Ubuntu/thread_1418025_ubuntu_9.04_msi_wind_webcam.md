---
title: "ubuntu 9.04 msi wind webcam"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by fryc86 on 2010-02-28
I am installing ubuntu 9.04.  I was going to do karmic but I was finding that there might be compatibility issues with the webcam on the MSI wind u-100.  But I can't get it working in 9.04 either.  I've tried a couple of different things and it isn't recognized by Cheese and not recognized in terminal.  Fn-F6 doesn't seem to do anything at all.  Is there anything I can do, or not? 

also, if there is a fix for msi wind webcam in karmic, that would be helpful also. thanks

---

### Post by tr333 on 2010-02-28
From the Ubuntu 9.10 (karmic) release notes: [http://www.ubuntu.com/getubuntu/releasenotes/910#bison%20webcam%20in%20MSI%20Wind%20netbook%20causes%20USB%20errors%20if%20not%20disabled](http://www.ubuntu.com/getubuntu/releasenotes/910#bison%20webcam%20in%20MSI%20Wind%20netbook%20causes%20USB%20errors%20if%20not%20disabled)

From the associated bug report ([https://bugs.launchpad.net/bugs/435352](https://bugs.launchpad.net/bugs/435352)) it appears that the issue has been resolved in a post-release update.  I would suggest installing 9.10 and doing a full system update to see if that resolves your issue.

It shouldn't matter whether you are running normal Ubuntu or the netbook-specific Ubuntu-Netbook-Remix.

---

### Post by fryc86 on 2010-02-28
> **tr333 said:**
> From the Ubuntu 9.10 (karmic) release notes: [http://www.ubuntu.com/getubuntu/releasenotes/910#bison%20webcam%20in%20MSI%20Wind%20netbook%20causes%20USB%20errors%20if%20not%20disabled](http://www.ubuntu.com/getubuntu/releasenotes/910#bison%20webcam%20in%20MSI%20Wind%20netbook%20causes%20USB%20errors%20if%20not%20disabled)

From the associated bug report ([https://bugs.launchpad.net/bugs/435352](https://bugs.launchpad.net/bugs/435352)) it appears that the issue has been resolved in a post-release update.  I would suggest installing 9.10 and doing a full system update to see if that resolves your issue.

It shouldn't matter whether you are running normal Ubuntu or the netbook-specific Ubuntu-Netbook-Remix.

thanks.  Where do I go to apply the update?

---

### Post by tr333 on 2010-02-28
You just need to run the [Update Manager](https://help.ubuntu.com/9.10/keeping-safe/C/updates.html) to check for new updates.  If there are no updates that fix the issue you might want to wait a bit as the bug report still has the status for Karmic (9.10) as "Fix Committed" (ie. still waiting to be uploaded to the Ubuntu package repository).

---

### Post by fryc86 on 2010-03-01
ok thanks.  I ran it and restarted and still didn't work.  So guess I'll just wait and see if a fix presents itself sometime.  Is it just the MSI version cam or can I get another camera to attach?  If so, is there a particular one that will work for sure?

---

### Post by no2498 on 2010-03-02
did you do this in the terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2 click the bottom test button for each 1

---

### Post by fryc86 on 2010-03-03
yes thanks.

"Video for Linux 2 (v4l2): Could not open device '/dev/video0' for reading and writing."

Same for (v4l)

---

