---
title: "Undependable wireless connection"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by sjmorris on 2008-01-01
I'm having a real problem establishing a reliable and persistent wireless network connection.  I&#8217;m running Ubuntu 7.10 on an old but capable Micron laptop with a Linksys WPC54G wireless card.  The initial setup of this system, just a couple of months ago, was relatively simple and smooth, notwithstanding a bit of tinkering required to make the initial network connection with this card.

The issue since then is that I can&#8217;t seem to keep that connection alive.   It may stand up for a few hours or even a day, but eventually it falls down.  Getting the connection back is also a small challenge; since Net Manager sometimes works, simply by re-entering the WPA key, and sometimes doesn&#8217;t.  It&#8217;s not uncommon that the only means of restoring the connection is to re-boot and reset Net Manager, though often even that fails to work at the first attempt.

I&#8217;m running four other computes on this same wireless network (2 Vista, 1 XP and 1 Win2K) and all remain steadily connected.

Any help or advice will be appreciated.

Thanks.

---

### Post by ModelM on 2008-01-01
First let's see if there are any clues in the log file. Get the connection up and, when it dies, look at the last few lines of the log file. The command "tail" is designed to show the last lines of a file - the default number is 10 lines. (And yes, you're right, to see the *first* few lines of a file the command is "head".)

There are lots of log files, but the one we want to see in this case is at:

/var/log/messages

So you'd bring up a terminal window and type:

tail /var/log/messages

...to see the last 10 lines of the file.

In order to see the last 25 lines of the file you'd add that number to the command like this:

tail -25 /var/log/messages

You might glean some clues by reading this to see what's happening when the connection drops. And, if there is no mention of the wireless connection loss in the log, that's a clue, too.

---

### Post by sjmorris on 2008-01-02
As such things happen, I can't get it to fail when I'm around to check the log.  I have, however, noticed that when I re-boot the log indicates that both wirelss and wired connections were attempted, though no wired connnection is configured in Net Manager.  When manually configureing the wireless connection, the log indicated one attempt to connect the wireless and four attempts at wired connection, whether or not the connection ultimately succeeds.

Is this a normal Net Manager behavior?

---

