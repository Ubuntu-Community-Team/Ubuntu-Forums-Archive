---
title: "Problem with opening webpages, but only with 9.10"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-11-18
Greetings,

I've tried a few times to install 9.10 on my Dell Mini 9.  Each time, I fix the wireless network card issue (installi[COLOR=Black]ng bcmwl-kernel-source with Synaptic), but I am having a problem loading pages.

I've tried on multiple networks, but it's always the same. Firefox reports, "Looking up <insert web address>..." for several seconds, and then eventually it begins to load the page (eventually sometimes being more than 30 seconds, but usually around 15).  I have tried enabling the broadband about:config options (from [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)).

I downgraded to 9.04 to see if the problem would be similar, but no. Pages load immediately with Firefox, and even faster with the pipelining and other broadband about:config options enabled.

I even tried changing my DNS servers to OpenDNS ones, and it didn't really change.  I also have AdBlock Plus and Flashblock enabled, which helps a bit, but doesn't actually solve my original problem.

Any suggestions?

Regards,
Red

PS: This problem happens with both wired and wireless connections.
[/COLOR]

---

### Post by QIII on 2009-11-18
First guess would be ipv6 setting in about:config.  ipv6 probably should be disabled.

But please read lovinglinux great tutorial here:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Redmage913 on 2009-11-18
Is my problem related to sqlite files? That is what most of that FAQ is about.

I was sure to disable ipv6 along with all the other optimizations.  I have not run the sqlite-related things yet.

Should I downgrade back to 9.04? I do not see any reasons to keep using 9.10 right now.  Any suggestions or comments are appreciated.

---

### Post by QIII on 2009-11-18
I think there is more there than sqlite...

There is no problem with going back to 9.04 (except that there is no "downgrade path").  Use what works!  Choice is great!

However, a lot of us are using 9.10 without FF problems (I also use Lucid without any).  It would be helpful to the community if we could figure out why you are having problems...

What are the specs on your wireless card and router?

It could be that there are bugs reported on launchpad.  There may be work arounds, or it may be that there has been no resolution for Karmic.

---

### Post by Redmage913 on 2009-11-19
Is the info you were looking for?

```
$ lspci -nn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

BTW, I downgraded back to 9.04, and am not having any problems.  If you wish to continue diagnosing this, I can reinstall 9.10 and see if this can be worked out.  This is my 'toy' computer, I've reinstalled the operating system about ten times if not more after playing with various operating systems (mainly flavors of Ubuntu), deleting the partition, and doing it again.

---

