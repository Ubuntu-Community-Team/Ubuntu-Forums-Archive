---
title: "No Thunderbird sound"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by csacpt on 2010-12-12
[SIZE=2]Using TB 3.1.7 and Ubuntu 10.10 and can't get sound notification. When I  try to browse for a sound file nothing happens. This shows up in the  error console but I have no idea what it means.Selecting default sound or custom generates the error. Browse button does not work and cannot manually enter anything into the box for file location either.

Error:  [Exception... "Component returned failure code: 0x8000ffff  (NS_ERROR_UNEXPECTED) [nsIFileProtocolHandler.getFileFromURLSpec]"   nsresult: "0x8000ffff (NS_ERROR_UNEXPECTED)"  location: "JS frame ::  chrome://messenger/content/preferences/general.js :: anonymous :: line  63"  data: no]
Source File: chrome://global/content/bindings/preferences.xml
Line: 406

Error:  uncaught exception: [Exception... "Component returned failure code:  0x8000ffff (NS_ERROR_UNEXPECTED)  [nsIFileProtocolHandler.getFileFromURLSpec]"  nsresult: "0x8000ffff  (NS_ERROR_UNEXPECTED)"  location: "JS frame ::  chrome://messenger/content/preferences/general.js :: anonymous :: line  63"  data: no]

I can play sound files outside of TB so I don't  think it is an OS problem, but I am a total newbie so what do I know?  Not a terrible problem, but I am trying to learn how this all works. It is probably telling me what the problem is but I am too ignorant at this point to understand. Thanks for any help.[/SIZE]

---

### Post by stmiller on 2010-12-12
I don't think it has ever worked, despite long time chatter about this:

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/292676](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/292676)

[https://bugzilla.mozilla.org/show_bug.cgi?id=579877](https://bugzilla.mozilla.org/show_bug.cgi?id=579877)

---

### Post by Rex Bouwense on 2010-12-12
I have been using Thunderbird for years and never got any sound to accompany the arrival of new email.  I tinkered with it but it never uttered a peep so I resigned myself to not having an auditory notification.  It really isn't a big thing for me but I can see that for some people it would be important.

---

### Post by csacpt on 2010-12-12
Not really a problem, I am running Mail Notification outside of TB and it works. Just "bugs" me when something is there and it doesn't work, especially when it does work in Windoze! :roll:

---

### Post by Michael Dooley on 2010-12-12
This troubled me at one time. I found this suggestion

[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8534880&postcount=9](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8534880&postcount=9)

to be of assistance. 

Instead of using Thunderbird's "Use the following sound file", I checked the "Default system sound for new mail" box/dot. I then downloaded Temujin's file, set up a System, Preferences, Sound menu entry using my retrieved /usr/local/bin/32-bit-x86/gnome-sound-properties command and, using the new Sound Setting ability, selected an appropriate sound. In my case, it was KDE-Im-Low-Priority-Message.ogg, which seems to work faultlessly.

YMMV.

---

