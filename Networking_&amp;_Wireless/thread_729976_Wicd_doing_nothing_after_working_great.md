---
title: "Wicd doing nothing after working great"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by reindling on 2008-03-20
Hi!
As an somehow experienced newbie (when it gets to the guts), i mangaged to get wireless conn. working with the help of this great forum.

Wicd was working well (besides dropping the conn. recently), but now: nothing.
In the meantime, nothing was changed on the machine than running automated updates for Gutsy.
Trying to start /opt/wicd/tray.py - nothing
When trying to start /opt/wicd/gui.py from alt-f2, the correct wicd-symbol ist shown before execution, but then again: nothing. No app, no tray.

Now i reinstalled the network manager to get wired - works ok. The wg111 stick is ok, it pops up fine in XP, and in Gutsy, ndiswrapper states the device as present and working.

Thx for any hints, or is it better to un/reinstall it?
chris

---

### Post by imdano on 2008-03-20
I would guess something happened to the wicd daemon.  Try running "sudo /etc/init.d/wicd start", then try opening the tray.  If that doesn't work, delete /opt/wicd/data/wired-settings.conf (sometimes it gets corrupted), and try the command above again.

---

### Post by reindling on 2008-03-21
Thanks for your answer, it lead me on some good trails!

There was some strange behaviour following your tips: 
Starting the daemon gave me a positive starting info with an pid.
Launching tray or gui - nothing.

rm 'wired-settings.conf' (you really mean wired? :) ), starting wicd daemon, startup ok, pid. 
Starting tray or gui - nothing.

Then i removed 'wireless-settings.conf' ......change!
Starting daemon ok, pid...  But starting the tray now comes up with:
'...start daemon first'  (AAAAHH!).
It turns out, that the pid of the wicd daemon startup "never exists", it seems to start into nirvana. (from my newbie pov)

Just before i wanted to trash wicd, i tried rm the 'manager-settings.conf' 
as mentioned in this thread i found:
[http://ubuntuforums.org/showthread.php?t=730047&highlight=wicd+daemon&page=1](http://ubuntuforums.org/showthread.php?t=730047&highlight=wicd+daemon&page=1)

Works! (until now...:) )
...guess you're right with 'corrupted settings', but how come...?
Thx very much
chris

---

### Post by imdano on 2008-03-21
Most of the time it's wired that gets corrupted, there's a bug with profile removal (I think, I never figured out the root cause of the bug before just adding a workaround for it) that causes an sectoin with an empty label to get added to the configuration file.  A config section with no name makes the ConfigParser blow up, and the daemon crashes.

In your case I'm not sure sure what happened, unfortunately.  If it happens again we can figure it out by starting the daemon a different way and reading it's debugging output.  Most likely something got written to the config that couldn't be read in correctly by the daemon for some reason.

---

