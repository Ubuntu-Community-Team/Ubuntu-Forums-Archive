---
title: "Flash Alpha 10 kills firefox"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-11-01
So I upgraded to Ubuntu 9.10.  Kept getting npviewer crashes from firefox 3.5 and randomly flash videos would stop responding to click input.  

So I installed the flash Alpha 10 plugin for firefox instead.  And now everything flash works fine.   But for some odd reason, when I load up gmail and log in, it crashes firefox every time.  It happens as soon as the little chat window loads up.

If I disable the flash plugin, gmail works fine with no crash.  I've seen similar reports of this elsewhere and running from the terminal yields nothing but a segmentation fault error message.

So I was wondering if anyone here had found a fix?  So far 9.10 has given me all sorts of wonderful kernel crashes and it would be nice if I could at least lay this one to rest.

---

### Post by HotShotDJ on 2009-11-01
Odd.  I can't replicate the crash on my system.  How did you install the 64 bit flash?  I did experience some crashing using the debian package from Sid.  But I've had no issues when using [Get64bitFlash]("http://ubuntuforums.org/showpost.php?p=7904240&postcount=1").  It is helpful to use Synaptic Package Manager to remove all traces of Flash from your system before running that script, though.

---

### Post by CryptiniteDemon on 2009-11-01
I just downloaded it from adobe.  It had one file libflashplayer.so.  I dropped it into /usr/lib/mozilla/plugins

---

### Post by CryptiniteDemon on 2009-11-01
I guess I should mention I'm using the 64 bit version.

---

### Post by HotShotDJ on 2009-11-01
> **CryptiniteDemon said:**
> I just downloaded it from adobe.  It had one file libflashplayer.so.  I dropped it into /usr/lib/mozilla/pluginsI highly recommend that you remove the file that you copied to /usr/lib/mozilla.  Next, open Synaptic Package Manager and make sure that all traces of flash have been completely removed from your system.  Next, run the Get64bitflash script that I referenced above.  This SHOULD solve your crashing issue -- but as with all things, your mileage may very.

---

### Post by michaelzap on 2009-11-01
Same thing happened to me. I ended up removing it and installing the standard Flash plug-in using Synaptic. That one has mouse issues with controls in Flash movies if you run Compiz, but at least Gmail works again.

---

### Post by CryptiniteDemon on 2009-11-01
I tried that script.  Yields the same gmail crash that I described in the first post.

---

### Post by HotShotDJ on 2009-11-01
> **CryptiniteDemon said:**
> I tried that script.  Yields the same gmail crash that I described in the first post.Crap.  I was so hoping that it would work for you.  Since I can't replicate the issue on my system, I can't really offer any other advise.  I'm sorry.

---

### Post by michaelzap on 2009-11-01
> **CryptiniteDemon said:**
> I tried that script.  Yields the same gmail crash that I described in the first post.

That script installs the same alpha version of the Flash plugin that you can get from the Adobe site.

---

### Post by HotShotDJ on 2009-11-01
> **michaelzap said:**
> That script installs the same alpha version of the Flash plugin that you can get from the Adobe site.Yes, it does.  However, it also checks for conflicts on your system and sets up some extra links which sometimes solve problems with the 64 bit plugin.  But clearly, it doesn't solve them all. :(

---

