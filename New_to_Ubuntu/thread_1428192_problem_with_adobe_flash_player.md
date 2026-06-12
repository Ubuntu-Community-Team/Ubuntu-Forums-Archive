---
title: "problem with adobe flash player"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by hortstu on 2010-03-12
I'm using hardy.

I have some version of flash player but not the latest so I can't see some videos.

I went into the synaptic package manager searched for adobe and manually selected the version that these videos say I lack.  I restarted firefox and they still don't work.

I have restricted extras selected.

What do I have to do to get/install the flash player I need to watch these videos?

---

### Post by audiomick on 2010-03-12
That is a bit of a wide topic. Go an have a look here for starters
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by hortstu on 2010-03-12
Thanks audio... I've been through that.  It's the only reason I even have some videos working here. 

I've also searched on this topic which is why I pointed out that I've tried some of the solutions suggested in other threads.

---

### Post by philinux on 2010-03-12
> **hortstu said:**
> I'm using hardy.

I have some version of flash player but not the latest so I can't see some videos.

I went into the synaptic package manager searched for adobe and manually selected the version that these videos say I lack.  I restarted firefox and they still don't work.

I have restricted extras selected.

What do I have to do to get/install the flash player I need to watch these videos?

Open a terminal and post back what this says.

```
sudo updatedb

The above just updates the search index, then 

locate libflashplayer.so

```

---

### Post by desnaike on 2010-03-12
> **hortstu said:**
> I'm using hardy.

I have some version of flash player but not the latest so I can't see some videos.

I went into the synaptic package manager searched for adobe and manually selected the version that these videos say I lack.  I restarted firefox and they still don't work.

I have restricted extras selected.

What do I have to do to get/install the flash player I need to watch these videos?


I made sure adobe flash 10 is installed then go to usr/lib/adobe-flashplugin and copy/paste libflashplayer.so into all my browsers plugin folder and renamed flashplugin-alternative.so to 1flashplugin-alternative.so, to ensure no conflicts, or to easily re-enable if needed have been doing this for years flash works all the time no conflicts I do this because I think the symlinks don't always work.

---

### Post by Tikkyca on 2010-03-12
I think you need to download firefox flash player plug-in,or mabie java script isn't activated,you can find how to activate it on linux with google.

---

### Post by hortstu on 2010-03-12
Thanks for the help Phil

```
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
```

---

### Post by hortstu on 2010-03-12
Anyone know what I'm supposed to do with those results phil asked for?

---

### Post by audiomick on 2010-03-12
What it is telling you is that you have an adobe flash player installed and another one as well, I think. I don't know what Philinux was getting at, but I am sure he will come back to check. I see him around here a lot. I is now 10 to 1 in the morning for him, so he is hopefully in bed getting a good nights sleep.

---

### Post by hortstu on 2010-03-13
OK thanks audio... if anyone knows what to do with this info please let me know... I'd love to mark this thread solved.

---

### Post by harrybrion on 2010-03-14
I also have a problem with Adobe Flash Player but only when trying to watch NBCs "Who do you think you are?"
Other videos play OK.

---

