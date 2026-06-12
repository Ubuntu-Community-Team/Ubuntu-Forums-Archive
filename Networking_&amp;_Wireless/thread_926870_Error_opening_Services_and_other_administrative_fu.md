---
title: "Error opening Services and other administrative functions"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by numberwhun on 2008-09-22
Hello everyone!  My appologies right off if this is not the correct forum to post this in, but I wasn't certain as to what category it falls under.  

I have having an issue on my Ubuntu 8.04 Hardy Heron system.  I go select System->Administration->Services and right after clicking on Services, I get a pop up error box that reads:

**The configuration could not be loaded**
You are not allowed to access the system configuration.

I had done a google search to try and find a resolution to this issue and came across a couple of posts here in the Ubuntu forums.  Unfortunately, the forum system would not let me reply to those posts so here is what I did.

The first post I found was [this one]("http://ubuntuforums.org/showthread.php?t=645404").  In erfahren's post (#3), I did the first thing suggested and nothing changed.  I tried to get into users and groups to do the second thing, but just like Services, I am getting the same error for users and groups as well. 

Another post I found here was [this one]("http://ge.ubuntuforums.com/showthread.php?t=824769").  I read down all the way to where iponeverything suggested setting the group on the file "dbus-daemon-launcher-helper", but that was no good as it is already set correctly.  

At this point, I am kind of at a loss and looking to see if anyone knows WHY this is happening?  Other than installing some things like php, apache, perl 5.10, and mysql, I have not made any real sys admin changes to this box as of yet.  Any assistance would be greatly appreciated!

Thank you in advance!

Best regards,

Jeff

---

