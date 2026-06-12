---
title: "Can't print with Netgear PS121v2"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by kansley9549 on 2008-05-19
Hi,

I've been trying to print to my Canon PIXMA mp530 via my Netgear PS121v2.  I have Hardy Heron on an old Dell laptop that is wireless via a Netgear PCMCIA card.  The PS121v2 is attached to a D-Link router and the Canon.

I tried adding it with the CUPS site; but then figured out that that's on Ubuntu.  So I've been trying that with no success.

I found the ps121v2 IP address, and the server name with that.  So with those I put the Device URI in as lpd://192.168.0.204/PS0CADBE.  I chose the Make and Model as "Canon PIXMA MP500 - CUPS+Gutenprint v5.0.2 Simplified, which seemed to be the closest I could find (after a thorough search).

I really thought I had it, but it doesn't print a test page (let alone print from open office or gimp or firefox.

Help?

---

### Post by jpnuzzo on 2008-07-15
I eventually purchased and use TurboPrint.

If you don't want to do that, try using socket/jetdirect instead of lpd. I've gotten it to work (Canon MP610) using uri:
[COLOR="Blue"][socket://192.168.0.204:9100/?bidi]("socket://<your-ps121-ip>:9100/?bidi")[/COLOR]

---

### Post by Hatfield on 2008-07-23
> **kansley9549 said:**
> Hi,

I've been trying to print to my Canon PIXMA mp530 via my Netgear PS121v2.  I have Hardy Heron on an old Dell laptop that is wireless via a Netgear PCMCIA card.  The PS121v2 is attached to a D-Link router and the Canon.

I tried adding it with the CUPS site; but then figured out that that's on Ubuntu.  So I've been trying that with no success.

I found the ps121v2 IP address, and the server name with that.  So with those I put the Device URI in as lpd://192.168.0.204/PS0CADBE.  I chose the Make and Model as "Canon PIXMA MP500 - CUPS+Gutenprint v5.0.2 Simplified, which seemed to be the closest I could find (after a thorough search).

I really thought I had it, but it doesn't print a test page (let alone print from open office or gimp or firefox.

Help?

I have EXACTLY the same problem.  Ubuntu 8.04 to DLink router to Netgear PS121 print server to Canon MP530 printer.  How do we set it up?


EDIT:  This worked for me!
[http://ubuntuforums.org/showthread.php?t=458376&highlight=ps121](http://ubuntuforums.org/showthread.php?t=458376&highlight=ps121)
The only thing is MP530 is not an option in CUPS so I chose MP600 and it worked.  The IP address of my print server was 192.168.0.2.

---

### Post by jpnuzzo on 2008-07-23
> **Hatfield said:**
> I have EXACTLY the same problem.  Ubuntu 8.04 to DLink router to Netgear PS121 print server to Canon MP530 printer.  How do we set it up?


EDIT:  This worked for me!
[http://ubuntuforums.org/showthread.php?t=458376&highlight=ps121](http://ubuntuforums.org/showthread.php?t=458376&highlight=ps121)
The only thing is MP530 is not an option in CUPS so I chose MP600 and it worked.  The IP address of my print server was 192.168.0.2.

I ended-up buying TurboPrint, which made the printer setup much easier. TurboPrint also has a bunch of additional drivers.

I strill haven't gotten the scanner portion installed on linux. I've found a couple of similar devices (Keyspan and one other), they have utilities to 'reserve' the device for Windows and OS X, but not linux.

---

