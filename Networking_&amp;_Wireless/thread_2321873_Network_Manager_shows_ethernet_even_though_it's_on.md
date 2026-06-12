---
title: "Network Manager shows ethernet even though it's on wifi?"
date: 2016-04-25
forum: Networking &amp; Wireless
---

### Post by lauricat on 2016-04-25
Hello.

I am having the same problem with my clean installed Ubuntu MATE 16.04

The screen-shot is attached; indicator showing a wired connection, when indeed it's connected via wireless.

[ATTACH=CONFIG]268605[/ATTACH]



Also, the list of wireless networks detected has disappeared, see next screen-shot.

[ATTACH=CONFIG]268604[/ATTACH]

I am also attaching the output of my wireless-info.tar.gz

Previously I had issues with my wireless driver, Intel centrino advanced-n 6205 in my X220 Thinkpad., and sorted that out by disabling wireless N as per here:

[http://ubuntuforums.org/showthread.php?t=1984317&page=2[](http://ubuntuforums.org/showthread.php?t=1984317&page=2[)

Finally, to further confuse things, I also have a related problem where if i disable networking, and re enable (tried this as a workaround to see my available wireless network(s) again) the x220 will not connect to anything at all - wireless networks - and the only solution is reboot.

It seems that the "indicator-applet_complete" is corrupt somehow.

The problem I have is i use the X220 to connect to many different wireless networks and need to know if i am connected or not and what are the available WiFi networks!

Thanks very much in anticipation.

~L.

---

### Post by QIII on 2016-04-25
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=2321694](http://ubuntuforums.org/showthread.php?t=2321694)

Please do not hijack the threads of others.  It is not polite to the original poster, it causes confusion for both of you and anyone who might attempt to help you and your issue might not, in fact, be at all the same.

---

### Post by lauricat on 2016-04-25
Mods, apologies my intention was to add to the existing thread with same name.

But somehow I managed to start new thread with same name.

Please feel free to merge..

Thanks.

~L

EDIT. Just read mod post and understand. Sorry about that.

---

### Post by lauricat on 2016-04-28
After a lot of experimentation and research, I stumbled onto this:

[http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade](http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade)

I ran the script, and automated it.

I have just resumed from suspend quite a few times and my wifi network list was refreshed everytime.

So I can say if you have any sort of problems with connection/seeing AP's after suspend try this out.

Thanks.

:D

---

### Post by lauricat on 2016-05-24
Please note this fix NO LONGER works for me - from yesterday - after a  month or so or working absolutely perfectly fine. (X220 Lenevo Laptop,  16.04 MATE edition.) ie. back to the same problem of NOT indicating  Networks available on Resume, and connecting to Wireless showing  connected to an unknown network via ethernet connected symbol.
  I suspect it broke yesterday after a rather larger system update that was pushed out yesterday.
  Could others please check if the same happens to their system?

EDIT: also tried this fix with no luck..

[http://askubuntu.com/a/768268/535455](http://askubuntu.com/a/768268/535455)

Mods; please removed the solved notation from this thread. Thank-you.

---

### Post by cdysthe on 2016-06-19
I am having the exact same problem on my Lenovo Thinkpad X1 Carbon. Something broke in the 16.04 update which messes up wifi and networking after resume. In previous versions of Ubuntu this worked fine.

---

### Post by jeremy31 on 2016-06-19
Try this code in terminal ```
systemctl restart NetworkManager.service
```

---

### Post by cdysthe on 2016-06-19
Restarting network-manager with that command fixes it until next suspend. It's a workaround for now, but not a fix. This has been working flawlessly in several previous releases of Ubuntu. It's a bug which will probably be fixed since many see the same problem: [http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade/788964#788964](http://askubuntu.com/questions/761180/wifi-doesnt-work-after-suspend-after-16-04-upgrade/788964#788964)

---

### Post by jeremy31 on 2016-06-19
There are a few bug reports and it is awaiting verification from those that submitted the reports

---

### Post by lauricat on 2016-06-19
[[COLOR=#000000]cdysthe[/COLOR]]("http://ubuntuforums.org/member.php?u=216640")

There are a few bug reports concerning this condition. I actually think it's getting a bit confusing;

Here is one; this towards the end explains ther was a fix rolled out, but some users bug was NOT fixed, so a new one was opened:

[https://bugs.launchpad.net/oem-priority/+bug/1574347](https://bugs.launchpad.net/oem-priority/+bug/1574347)

Another one, the 'new' bug report from last.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589401](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589401)

So from what I can gather a fix was rolled out, worked for some, not others, and another bug report opened as a result.

I honestly think it's a systemd thing.

PS. here is GNOME Bug report:

[https://bugzilla.gnome.org/show_bug.cgi?id=767317](https://bugzilla.gnome.org/show_bug.cgi?id=767317)

Cheers

---

