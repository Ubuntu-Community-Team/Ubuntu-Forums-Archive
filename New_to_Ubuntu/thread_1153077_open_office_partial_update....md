---
title: "open office partial update..."
date: 2009-05-08
forum: New to Ubuntu
---

### Post by mustard greens on 2009-05-08
I am getting the partial update message for some open office updates.  their updates always seem to have problems ie: partial update, non authenticated etc.  what is the deal?  should I accept the partial update?  might this screw with my office suite?

---

### Post by sports fan Matt on 2009-05-08
I did and it wiped it out..id hold off for now, trying to find a solution

---

### Post by Spooky5 on 2009-05-08
I got the same but when I tried to do the partial update, it would not load. :?

---

### Post by robc02 on 2009-05-10
Likewise, I tried to do the partial update and it wouldn't do it.

I should add that I am not using the version from the official Hardy repository. I changed my sources.list so that I can use the most recent Open Office. However, I did that about six months ago and have had no problems until now.

---

### Post by robc02 on 2009-05-11
This worked for me:

Open Synaptic and go to "openoffice". All my installed items had green blocks, but also had stars within those green blocks, which meant that there was an upgrade. So I clicked one (can't remember which one), and then clicked on "Mark for Upgrade". It marked all the dependencies and installed everything. 

This is a slightly shortened version of a post on another thread.

Hope that helps you.

---

### Post by mustard greens on 2009-05-11
thanks robc02, that worked for me, but I would still like to know ***why*** this works and why open office has so much trouble providing updates.  also, can you post a link to the original thread.

---

### Post by robc02 on 2009-05-11
I'm not sure why it works, but I think it is something to do with the release of Open Office 3.1. My installed version was 3.0 but the descriptions on Synaptic referred to 3.1. Interestingly, when I launch Open Office the panel containing the progress bar still says "Open Office.org 3.0", but clicking on "Help - About Open Office.org" the bottom line in small text says 3.1.

The original thread is:

[http://ubuntuforums.org/showthread.php?t=1153159&highlight=open+office+update]("http://ubuntuforums.org/showthread.php?t=1153159&highlight=open+office+update")

If you find out any more I'd be interested to hear it.

---

### Post by robc02 on 2009-05-29
The latest OOo updates, via Update Manager, appear to have solved my remaining problems - I now have working help files.

---

### Post by mustard greens on 2009-05-29
I had not noticed any problems since the last update. though I may not be very astute, I have been using OO without issue since applying the fix you suggested.  I did get the updates the past two days, also without issue.

---

