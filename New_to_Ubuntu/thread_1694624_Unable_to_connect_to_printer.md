---
title: "Unable to connect to printer"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by col48 on 2011-02-24
Hardy 8.04, but I suspect it applies generally, subject to changes to the menu system!

[B]Problem:
[/B]USB Printer used to work fine.

Booted up on one occasion without the USB lead plugged in.  Usually just plugging it in allows printing to take place, but this time got the above message.

Reboot.  No difference.

**Solution:**

System>Control Panel>Printing  (NB there are two identical icons - you want the one with 'Configure your printers' not 'Configure printers' when you hover the cursor over it).
This shows (as labelled icons) the set of printers which have been defined.
Right-Click on the one which is having problems and Click on Properties.
Click on the Tab labelled Connections.

There are two radio buttons
'Local or Detected Printer'
'Network Printer'
(and other stuff which can be ignored)

The first needs to be clicked.  The second was showing as pressed instead.
*Hint:* if you have two printers defined (even if they are the same physical device) and one works but the other doesn't see what differences there are under the Control Panel Printing icons and think about them.

I have a local printer not a network one, and I don't guarantee there are no other necessary assumptions for this to work.

This post builds on a number of other posts and internet snippets.

---

