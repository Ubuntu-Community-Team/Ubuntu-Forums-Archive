---
title: "possible to record a quicktime webcast?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by treesurf on 2009-01-06
I'm wondering if it's possible to record a quicktime live webcast.  I'm using mplayer to view the webcasts and would like a way to record them for later viewing.

Thanks.

---

### Post by HotShotDJ on 2009-01-06
> **treesurf said:**
> I'm wondering if it's possible to record a quicktime live webcast.I've had good luck with [DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006")

If that doesn't work, try doing it from the command line using -dumpstream... something like this:```
mplayer -dumpstream mms://some.site.com/stupid/proprietary/file/format.asf
```

---

### Post by handydan918 on 2009-01-06
> **treesurf said:**
> I'm wondering if it's possible to record a quicktime live webcast.  I'm using mplayer to view the webcasts and would like a way to record them for later viewing.

Thanks.

Not sure about quiktime, but you can find out easy enough. Open Nautilus, and navigate to /tmp.
Make a mental note of the files there. Start a quicktime, and see if a new file appears. 

If so, you may be able to capture it by the same means I use with flash videos. 

As soon as the video is done downloading, but before it's done playing, reame the file from /tmp/weird_filename to /home/myusername/weird_filename.
You should then be able to view the saved file later on.

---

