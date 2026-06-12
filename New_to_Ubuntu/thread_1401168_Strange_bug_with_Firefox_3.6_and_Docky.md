---
title: "Strange bug with Firefox 3.6 and Docky"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by angrybanana5000 on 2010-02-07
[http://i47.tinypic.com/311rup4.png](http://i47.tinypic.com/311rup4.png)

This has been annoying me for some time now. If you look in the picture my dock says 'Shiretoko' when I am running Firefox 3.6 (Which is Namaroka). I have tried removing Firefox and Docky completely many times but it just keeps doing this and I have no idea what could be causing this. Help?

---

### Post by nhasian on 2010-02-07
your right shiretoko is firefox 3.5.  Namaroka is Firefox 3.6  it probably has something to do with how you installed firefox 3.6

with docky, if you want to keep the firefox icon on the dock even when its not running, first launch firefox then right click on the icon and choose "pin to dock"

---

### Post by angrybanana5000 on 2010-02-07
> **nhasian said:**
> your right shiretoko is firefox 3.5.  Namaroka is Firefox 3.6  it probably has something to do with how you installed firefox 3.6

with docky, if you want to keep the firefox icon on the dock even when its not running, first launch firefox then right click on the icon and choose "pin to dock"

I've installed the Firefox 3.6 package (which installs Ubufox, Firefox-branding, and Firefox) through Synaptic as same as any other package. :/

---

### Post by nhasian on 2010-02-07
Firefox 3.6 is not part of Karmic, you must have added a PPA or installed it with a deb package?

> **angrybanana5000 said:**
> I've installed the Firefox 3.6 package (which installs Ubufox, Firefox-branding, and Firefox) through Synaptic as same as any other package. :/

---

### Post by lovinglinux on 2010-02-08
> **angrybanana5000 said:**
> I've installed the Firefox 3.6 package (which installs Ubufox, Firefox-branding, and Firefox) through Synaptic as same as any other package. :/

I guess I know what's going on. Due to new major-minor updates policy, the PPA doesn't install firefox-3.6 side-by-side with firefox-3.5, but updates firefox-3.5 package. To launch Namoroka from command, you can use either *firefox %u* or *firefox-3.5*, but not *firefox-3.6*. I don't know how docky detects the application version, but perhaps it is getting confused about which version is installed, since Namoroka was just an upgrade of firefox-3.5.

---

### Post by lmellor on 2010-07-12
any updates on how to fix this? It's been annoying me for quite some time now.

---

### Post by Kellemora on 2010-07-12
I don't what Docky is, but Firefox has released several new BUGS recently.

The last known fully functional version of Firefox was version 3.6.3

When they released version 3.6.4 it had numerous problems.
They tried to fix it by quickly releasing 3.6.5 a couple of days later, and then followed up with 3.6.6 which actually made matters worse for many folks.

I'm using 3.6.6 on here right now, because I forgot it was hidden in the update package with the new Kernel.  So will probably have to figure out how to get back to version 3.6.3 if I plan on doing any serious stuff using Firefox with Flash.

In a nutshell, FireFox is no longer compatible with Flash and causes a Major Memory Leak if you have version 3.6.4 or above!

TTUL
Gary

---

### Post by fooman on 2010-07-12
no comment

---

### Post by lovinglinux on 2010-07-12
> **Kellemora said:**
> The last known fully functional version of Firefox was version 3.6.3

That is not true. I have been using Firefox 3.6.4, 3.6.6 and 3.6.7 and they all work perfectly. Your situation is completely different, because you are running Hardy Heron, which had an usual major upgrade from Firefox 3.0.19 to 3.6.4, because Mozilla stopped supporting Firefox 3.0 series.

I have already tested Firefox 3.6.4 compiled from source, 3.6.6 for the repositories, 3.6.6 and 3.6.7 from the daily PPA, 3.6.4 and 3.6.6 from Mozilla and ALL work perfectly in Lucid Lynx.

> **Kellemora said:**
> When they released version 3.6.4 it had numerous problems.
They tried to fix it by quickly releasing 3.6.5 a couple of days later, and then followed up with 3.6.6 which actually made matters worse for many folks.

Firefox 3.6.6 was released because a single problem with the plugin isolation timeout, which was too short, causing Firefox to detect a plugin as crashed prematurely. There is no such thing as Firefox 3.6.5. It was never produced or released.

I guess you missed [my reply on your thread](http://georgia.ubuntuforums.org/showpost.php?p=9546722&postcount=6) complaining about Firefox.

> **Kellemora said:**
> In a nutshell, FireFox is no longer compatible with Flash and causes a Major Memory Leak if you have version 3.6.4 or above!

Perhaps for Hardy users, since flash from Hardy repositories is still version 9, but not for everyone. I have no memory leak problems and haven't seen posts complaining about that.

Have you tried to download Flash 10 from Adobe? If you are using 32bit system, then you can get the deb, otherwise you will need to download the tar.gz file and replace the plugin manually.

---

### Post by lmellor on 2010-07-12
> **Kellemora said:**
> I don't what Docky is...

Then anything you say after this quote will not help fix the problems described in this thread, perhaps you should start/hijack another one.

> **fooman said:**
> using 64bit ubuntu lucid with nvidia 8800gt, i have had no issues with flash and namoroka (version 3.6.8 i have been using it through all the latest versions without issues).

Neither has the original poster, whatever you did will NOT solve our problems, once more, you have the wrong thread

> **lovinglinux said:**
> That is not true. I have been using Firefox 3.6.4, 3.6.6 and 3.6.7 and they all work perfectly. Your situation is completely different, because you are running Hardy Heron

and the situation the thread was begun about was not at all anything to do with Hardy Heron, again, try a different thread.

Would anybody care to chip in with some excellent deals on car insurance? Or better still, help with the problem ORIGINALLY being discussed (way back when Adam were a lad)

Sorry for the sarcasm, I just really would like to get this problem solved once and for all.

---

### Post by lovinglinux on 2010-07-12
> **lmellor said:**
> and the situation the thread was begun about was not at all anything to do with Hardy Heron, again, try a different thread.

Would anybody care to chip in with some excellent deals on car insurance? Or better still, help with the problem ORIGINALLY being discussed (way back when Adam were a lad)

Sorry for the sarcasm, I just really would like to get this problem solved once and for all.

I have mentioned Hardy because that is the version of Kellemora, has.

I don't like your sarcasm. You are the one that started hijacking a DEAD thread that was posted when Karmic was the current version. So please create your own thread and stop whining.

I will ask a moderator to lock this one, since it makes no sense to continue it.

---

### Post by drs305 on 2010-07-12
Thread closed. If the OP wants more inputs let us know via the Resolution Center.

---

