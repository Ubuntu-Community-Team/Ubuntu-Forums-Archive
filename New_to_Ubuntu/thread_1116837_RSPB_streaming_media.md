---
title: "RSPB streaming media"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by lift_test on 2009-04-05
Is there a codec in Ubuntu for the RSPB's streaming media ie live Loch Garten cam?  If not, how can this be viewed?

---

### Post by Jose Catre-Vandis on 2009-04-05
I couldn't get it working through my Firefox and plugins setup, but tracked down the feed in the page source and loaded this into vlc and this works fine.

Open up that page source for the web page and search for mms, you should find a link like this: mms://wms.carnyxlive.co.uk/abernethy. Open vlc andenter link under the network tab.

Next write and complain to the RSPB webmaster about poor uniformity!

---

### Post by Zill on 2009-04-05
The live video on page [http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp]("http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp") plays fine on my Dapper(!) system.

mms video seems to be a Windows format, so if you have all the relevant codecs installed it *should* work.

[This link]("http://kb.mozillazine.org/Testing_plugins") should help to check all your plugins.

If any codecs are missing I suggest you checkout [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") and install if necessary.
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by scratman on 2009-04-05
if you're talking about this link,

[http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp](http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp)

it works just fine for me.  Have a look at this page, [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
it's what I used to set up all of the codecs on my machine.

hth

---

### Post by lift_test on 2009-04-05
Thanks for all the info, will try the suggestions.  This is the URL I'm talking about  [http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp](http://www.rspb.org.uk/webcams/birdsofprey/lochgartenvideo.asp)

---

