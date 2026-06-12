---
title: "Connecting to Windows network"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Theophylact on 2007-10-30
I just did a nice clean uneventful installation of Ubuntu 7.10 on my oldest machine (an Athlon 1500+). I have a Windows network at home, and Gutsy recognizes it by name but won't display the contents. I've looked at some of the other threads and they suggest[ something about a Samba password]("http://ubuntuforums.org/showthread.php?t=558852"):> I have just had a hellish 12 hour ordeal doing this.

I started with this how to:-

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

The real break through was when I did

$ smbpasswd -a [username]

This added the samba password for each shared account and got me up and running!The link to that howto is dead.  As an absolute Linux noob, it's not clear what I should do. The comments in the thread I linked to are quite opaque:> still sounds like a samba synching thing with unix users.

Did you do the $ smbpasswd -a [username] bit?

do you have firewalls running on the machines?

If you have firstarter on the feisty machine you can monitor any rejected ip addresses, might help. In Windows, it's a matter of enabling file and printer sharing (the latter is what I really want to do). Am I a unix user? I do have firewalls (OneCare on one machine, ZoneAlarm on the other), but file sharing is enabled on both.

---

