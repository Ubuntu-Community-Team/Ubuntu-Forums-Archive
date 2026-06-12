---
title: "wireless security at bootup + roaming"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by tctimmeh on 2007-06-13
Our network setup here requires that our wireless network connection be established **before** login because we use ldap for authentication and network-mounted home directories and all that good stuff.  It took a lot of sweat to finally get it mostly working, but I still have a couple of questions:

1) I was only able to get it working using tips from [this guide]("http://ubuntuforums.org/showthread.php?t=202834").  This works, but it's kind of a hack, what with having to restart networking, and makes my boot times a little excessive, especially on the older machines.  I'd much rather use the (k)ubuntu network managers and tools.  Is it not possible, using the graphical tools, to configure a wifi adapter to connect to a preferred network at boot time, rather than at login time using the wallet?

2) Half the advantage of wifi is roaming.  With a statically configured interfaces file roaming becomes a PITA.  Is there any way I can automatically connect to my preferred network(s) when available but still leech onto anything else available at all other times?  The thought of supporting off-site workers who need to edit an interfaces file to connect to a someone else's network gives me nightmares.  :(

Any advice, suggestions, or just a man page shoved in my face would be really appreciated.

---

### Post by tctimmeh on 2007-06-14
bump <wow this thread moves fast>

---

### Post by dardack on 2007-06-14
I'm a begginner myself, but i use WICD instead of network-manager to connect to automatically to my preferred access point and also it has scanning, i can see all networks out there.  wicd.sourceforge.net i believe.  

As far as LDAP.  I looked at that guide it didnt' show me anything on ldap, mainly just WPA/security setting up.  AFAIK wicd has that part built in (at least for me i just set up WEP and tested WPA on my dad's and everything worked inside wicd).    And i know there are LDAP guides out there.  I personally don't use so can't be of much help there.  I'm sorry if i'm misunderstanding what you're asking.

PS< yes this forum moves very fast>

---

