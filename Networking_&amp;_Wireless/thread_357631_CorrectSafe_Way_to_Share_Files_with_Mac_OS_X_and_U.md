---
title: "Correct/Safe Way to Share Files with Mac OS X and Ubuntu"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by blankartist on 2007-02-09
Hi - I'm trying to setup Ubuntu to network with a wireless MacBook and a wireless Windows XP machine. I managed to get Samba working and share the mounted drives. They're formatted as ext3 and physically installed in the Ubuntu (6.10) machine.

Now I'm reading that SMB sharing can screw up metadata, permissions etc. stored in the Mac files when things get copied. I want a solid backup solution, and can't afford to lose photo metadata, modification dates and whatever other hidden files the Mac needs for a seamless (but not necessarily bootable) restore.

I'm thinking of reformatting the Ubuntu drives to HFS+. Will that alone solve the problem, or do I need to be networking with a different protocol? I've just about installed everything in Ubuntu - Bonjour, Netatalk, Samba, CUPS etc. I wanted to go with Bonjour, but the Windows XP machine doesn't seem to see the Ubuntu printer (apparently Bonjour ONLY works if served from a Mac, even though Ubuntu has it installed).

Thanks in advance!

---

### Post by blankartist on 2007-02-09
I forgot to mention the Windows XP machine has Bonjour installed as well.

---

### Post by cdeel77 on 2007-03-15
I'm interested in this topic too.
Do I need to be using AFP to store a reliable backup of my Mac laptop on my Ubuntu server?
I've seen some old posts about netatalk losing data ... is that still an issue?
Thanks a bunch for any guidance.

---

### Post by ericdfields on 2007-03-26
I got the netatalk server up and running pretty easily on my Ubuntu Edgy box. I can connect to my ubuntu machine in OS X via afp://192... in Finder. I feel like this was an issue for a lot of people. Reply if you need this explained... i'm not sure if that's what people are getting at [in]("http://www.ubuntuforums.org/showthread.php?t=138364&highlight=netatalk") [these]("http://www.ubuntuforums.org/showthread.php?t=357631&highlight=netatalk") [posts]("http://www.ubuntuforums.org/showthread.php?t=301504&highlight=netatalk").

**However**, I can only connect to my user's home directory, and i'd like to have some more intricate volumes set up. This is with completely out of the box settings. I've looked into configuring netatalks conf files, but none of the available options seemed like they would have solved my issue, which is thus:

I've declared the following in /etc/netatalk/AppleVolumes.default:
```

~/                      "Home Directory"
/media/media            "Media" allow:eric

```

As i stated I can connect to the home directory in Finder. When I try to connect to Media, though, finder bombs on me with an afp -5014 error. Look it up... it apparently is a 'misc' error. Not too helpful at all, Apple :-P.

I played with permissions of /media/media and such, still no good. I've circumvented the issue by placing a soft link to /media/media in my home directory. This way, I can browse it just fine. Works for now but if anyone experienced a similar situation with netatalk before, I'd love to hear you share.

---

