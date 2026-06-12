---
title: "[SOLVED] Secure WebDAV issues with Nautilus"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by windfix on 2008-11-29
I have several shares on a server which I can access easily via XP's Network places, simply by using the https address provided to me - and they work normally.  I USED to have fluid access to them via Nautilus under Intrepid.  I used Connect to Server, Custom Location, replaced https: with davs: plus the server address, included a bookmark and username/password.  I can not figure out why the following inconsistent behaviours:

5 of 6 shares still connect, however some subfolders display as "(empty)", when I know files exist there.  I can use a browser interface to display them.  Nautilus must be logging in OK, because it displays the root folder contents OK.  It also displays Dav | Davs | Foldername correctly in the status bar.

The 6th share connects, but does not display any contents at all.  The status bar shows Dav | Davs | Foldername; and it doesn't ask for credentials - so I assume it connected OK.  It returns this error, however, instead of folder contents:  "Sorry, could not display all the contents of "My Workspace": Could not parse response"

Of course, the only two shares I need regular access to are the ones not working in Nautilus.... Any ideas?

---

### Post by windfix on 2008-12-04
Anyone?  Seen this message from Nautilus?

"Sorry, could not display all the contents of "My Workspace": Could not parse response"

My Workspace is the folder name on the server I try to connect to, so it's reading that much - but won't display contents

---

### Post by windfix on 2008-12-07
I finally found a solution to this issue.  Nautilus can not handle the ampersand sign (&) in a filename or a folder name.  I connected to my secure WebDAV shares from Windows XP and changed the filenames that included an ampersand - instantly resolved the issues.

---

### Post by sellwowgold2 on 2008-12-07
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com),[sell ffxi gil](http://www.virdeal.com),[sell maple story mesos](http://www.virdeal.com),[sell gaia gold](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

