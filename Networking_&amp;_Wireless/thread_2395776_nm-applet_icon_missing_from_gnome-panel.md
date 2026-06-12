---
title: "nm-applet icon missing from gnome-panel"
date: 2018-07-06
forum: Networking &amp; Wireless
---

### Post by nilandj-nilandsplace on 2018-07-06
There are many post on this problem, but for 4 years I have not found a solution to my specific problem
During an ordinary update the nm-applet went missing and every solution I found was at best a hack to replace what was missing.
I did finally find the error and I offer this as one more solution. Seems the files in ```
/etc/dbus-1/system.d had somehow been changed
``` A file had been added ```
nm-openconnect-service.conf
``` that had the lines in it
```
<policy context="default">
        <deny own="org.freedesktop.NetworkManager.openconnect"/>
        <deny send_destination="org.freedesktop.NetworkManager.openconnect"/>
    </policy>
```
Removing this file did in fact restore the **nm-applet** to it's correct position in the **gnome-applet-complete**
Not sure how or why, but I suspect a package was installed in 2013, **OpenConnect**, that is it seems for a Cisco AnyConnect for there routers, ASA5500 series.
The thing is I don't have anything like this, so I am sure it did not install it, so it must have been add by so other package I suspect.
If you have a backup, I have many, a meld comparer found it.
I check the install history, but it does not give much of a clue as to how or why. I have not removed this package yet as I wanted to make this post first and I alway want to run a backup first, just in case something goes FUBAR. My favorite is > Timeshift or > Back in Time as is is easier and faster then deja-dup. Beyond this I can browse the files for a comparison.

---

