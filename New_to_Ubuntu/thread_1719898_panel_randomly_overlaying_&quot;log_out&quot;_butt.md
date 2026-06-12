---
title: "panel randomly overlaying &quot;log out&quot; button with duplicate user button"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by crochambeau on 2011-04-02
10.04

Pics are worth 1000 words:

[IMG]http://i7.photobucket.com/albums/y273/earthman606/after.png[/IMG]

This is how the upper right of my panel *should* look.

[IMG]http://i7.photobucket.com/albums/y273/earthman606/before.png[/IMG]

THIS keeps happening. Randomly, it won't for many days, then it will. I share this machine with my wife and we've separate accounts, so the logout/switch button is used constantly.

I can't pin down what I'm doing to trigger it, I believe it's even happened while no processes (browser, etc) are running.
It doesn't happen on the other account.
Everything is "locked" in place.

I know the ```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

``` quick fix.

At this point I'm more interested in prevention, any ideas? THANKS!

---

### Post by Daniel0108 on 2011-04-02
Hi!

I don't think that there's a solution for this "problem", because it's a bug.

Please report this bug here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Here's a tutorial on how to submit bug reports: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Thank you for your bug report,
Daniel

---

### Post by crochambeau on 2011-04-02
Ah. Damn. OK.. looks like a distraction free morning with fresh coffee is in order to peruse the submitted bugs so I don't duplicate someone else's efforts.

Any technical terminology for the issue I can use to refine my search? I feel my description above is woefully devoid of a nice concise synopsis.

---

### Post by Daniel0108 on 2011-04-03
> **crochambeau said:**
> Ah. Damn. OK.. looks like a distraction free morning with fresh coffee is in order to peruse the submitted bugs so I don't duplicate someone else's efforts.

Any technical terminology for the issue I can use to refine my search? I feel my description above is woefully devoid of a nice concise synopsis.

Just report the bug :) There are bug triagers like me, who are looking for duplicates.
It's just stupid to have the same bug reported 10 times.

If you don't find duplicates after searching for them, report the bug.

Yours,
Daniel

---

### Post by crochambeau on 2011-04-16
I found what appears to be the same bug.

[https://bugs.launchpad.net/ubuntu/+source/edubuntu-meta/+bug/558466?comments=all](https://bugs.launchpad.net/ubuntu/+source/edubuntu-meta/+bug/558466?comments=all)

I have indicated that it effects me as well, and am waiting for a recurrence of the fault to run Apport and submit a report. Many thanks!

---

### Post by Kururu Souchou on 2011-04-16
> **crochambeau said:**
> Ah. Damn. OK.. looks like a distraction free morning with fresh coffee is in order to peruse the submitted bugs so I don't duplicate someone else's efforts.

Any technical terminology for the issue I can use to refine my search? I feel my description above is woefully devoid of a nice concise synopsis.
Just reboot, I've had the same problem before, there's not much of a way of preventing it

---

### Post by oklokl on 2011-04-16
Panel bug
Right-click (spacing)
 Remove the existing panel
 Please register manually

Start on the right end
1234 (&#50864;&#52769; &#45149; &#50640;&#49436; &#47560;&#50864;&#49828; &#50864;&#53364;&#47533; &#54616;&#49884;&#44256; &#49884;&#51089; &#54616;&#49464;&#50836;.. &#49692;&#48264;&#51008; &#51060;&#48120;&#51648;&#50640; &#45208;&#50728; &#44163;&#44284; &#44057;&#51060; 1 2 3 4 &#49692;&#51077;&#45768;&#45796;.. &#45796; &#50756;&#47308; &#54616;&#49884;&#47732; &#51104;&#44552; &#54616;&#49884;&#47732; &#46121;&#45768;&#45796;)

 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=189220&stc=1&d=1302974286[/IMG]

end...

Panel Locks

---

