---
title: "Bluetooth interfering with streaming video?"
date: 2016-08-02
forum: Networking &amp; Wireless
---

### Post by driebel on 2016-08-02
Last night, I upgraded my System 76 laptop from 14.04 to 16.04.  The upgrade has gone mostly smoothly, but I am having some problems with my wireless headphones.  I recently purchase a pair of Skullcandy grinder bluetooth headphones, and had been using them with no issues for about a week.

Since the upgrade, if I attempt to watch a youtube video while using the headphones, the video will not play.  It plays fine with wired headphones, and with the laptop speakers, but the bluetooth headphones cause the video to stop loading, and no longer play.  Local files on my own hard drive also seem to work with no issues.  I can go to other web pages, so it's not a complete breakdown of all internet connection, but youtube, vimeo, and cnn videos fail to play.  Those are the only specific sites I have tested it on, I assume the same is true for all streaming video.

Turning off bluetooth and refreshing the page gets the video working again.

I'm rather ignorant when it comes to networking and video playback.  Any help is appreciated.

---

### Post by driebel on 2016-08-03
BUMP

Anyone?  I found and implemented this fix:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1438510)

But it didn't work.  In fact, following these instructions made my situation worse.  I am able to switch to A2DP mode just fine, if I only watch local files.  It's something about streaming that causes my issue.  Changing these files made it so that my headphones could not switch to A2DP mode at all.  

I went back to my original configuration.  I'm out of my league.  I don't understand what the files in that bug fix do, so I can't begin to guess why it didn't work.  :confused:

---

