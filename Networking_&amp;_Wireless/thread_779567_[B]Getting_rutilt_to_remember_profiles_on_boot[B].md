---
title: "[B]Getting rutilt to remember profiles on boot?[/B]"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by guildofghostwriters on 2008-05-02
I'm running rutilt with rt73 dongle under Hardy and it's working fine except it doesn't remember profiles. Whenever I exit or launch it from terminal pointing to a profile, it gives me error 37, a profile could not be recorded. Messing and looking around led me to try sudo su, going to root/.config and creating a rutilt folder. In that rutilt folder there xml files with the profiles but if I do either rutilt -dp profilename or sudo -dp profilename (with or without the dp or tp, makes no odds) I get the error 37 message. If I go to terminal and sudo su then sudo rutilt -dp profilename, it works but I can't get that to work from the sessions manager - is there a way of making a script, or of booting as root, so that this works? It's not the worst thing in the world to have to enter a key and create a profile every time but what with ff3 launching in offline mode, the start of every session is full of little irritations!

---

