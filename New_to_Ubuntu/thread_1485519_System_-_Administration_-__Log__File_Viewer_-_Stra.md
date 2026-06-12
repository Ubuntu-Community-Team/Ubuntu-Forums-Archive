---
title: "System - Administration -  Log  File Viewer - Strange Entries?"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by Hagler on 2010-05-16
[FONT=Book Antiqua][SIZE=3]Hi everyone.  I've been using Ubuntu (9.10 Karmic) since late last year without any real problems.  As I'm still trying to get to grips with Ubuntu, I generally poke about a bit in the [/SIZE][/FONT][FONT=Book Antiqua][SIZE=3]System - Administration -  Log  File Viewer[/SIZE][/FONT][FONT=Book Antiqua][SIZE=3] after each start up to check if all is as it was at the previous start up.

This evening I noticed that the System - Administration -  Log  File Viewer - Messages file had some previously unseen entries noted -:

[FONT=Arial Narrow][SIZE=2][SIZE=1]type=1505 audit(1274058386.247:13): operation="profile_replace" pid=1262 name=/usr/share/gdm/guest-session/Xsession
type=1505 audit(1274058386.251:14): operation="profile_replace" pid=1268 name=/sbin/dhclient3
type=1505 audit(1274058386.251:15): operation="profile_replace" pid=1268 name=/usr/lib/NetworkManager/nm-dhcp-client.action 
type=1505 audit(1274058386.251:16): operation="profile_replace" pid=1268 name=/usr/lib/connman/scripts/dhclient-script
type=1505 audit(1274058386.255:17): operation="profile_replace" pid=1271 name=/usr/bin/evince
type=1505 audit(1274058386.263:1: operation="profile_replace" pid=1271 name=/usr/bin/evince-previewer
type=1505 audit(1274058386.267:19): operation="profile_replace" pid=1271 name=/usr/bin/evince-thumbnailer
type=1505 audit(1274058386.275:20): operation="profile_replace" pid=1273 name=/usr/bin/freshclam
type=1505 audit(1274058386.279:21): operation="profile_replace" pid=1274 name=/usr/lib/cups/backend/cups-pdf
type=1505 audit(1274058386.279:22): operation="profile_replace" pid=1274 name=/usr/sbin/cupsd
UDF-fs: No VRS found
UDF-fs: No partition found (1[/SIZE])[/SIZE][/FONT]
[/SIZE][/FONT] [FONT=Book Antiqua][SIZE=3]
I did make some changes to the system today when attempting to use digital camera software (gphoto, pmount, usbmount and pysdm) via Synaptic Package Manger, which [/SIZE][/FONT][FONT=Book Antiqua][SIZE=3]I then uninstalled, as they did not seem to recognise my camera.  I also updated the clamav engine and definitions.  

I'm really worried about the "profile replace" entry in the messages log, and also about the entires marked UDF as they sound more than a bit spooky to a complete novice like me.  I'd be very grateful if anyone can shed any light on why these entries have come up, what they mean, and whether or not I should be worried.

Thanks,

Hagler[/SIZE][/FONT]

---

### Post by BoneKracker on 2010-05-16
I use a linux distribution other than Ubuntu and am not familiar with this specific auditing output, so it would be helpful if an Ubuntu user would confirm what I'm saying here.


It's very good that you are looking at your log files.  Bonus points for that.  I think this is nothing to worry about.

The profile-update entries look to me like they're related to routine updates.

UDF is the filesystem used for DVDs.  The "VRS" is the "Volume Recognition Sequence".  It looks like something was attemping to load a DVD that isn't there (or maybe you have a CD or a movie DVD in your DVD drive).  This looks like a normal operation.

---

### Post by Hagler on 2010-05-16
[FONT=Book Antiqua][SIZE=3]Thanks [/SIZE][/FONT][FONT=Book Antiqua][SIZE=3]for the reply BoneKracker[/SIZE][/FONT][FONT=Book Antiqua][SIZE=3].  I am a bit concerned however that [/SIZE][/FONT][FONT=Book Antiqua][SIZE=3]i've rebooted several times since the initial changes first appeared in the logs and they still seem to be enter in the same fashion.  If it is an update issue do you think that the "profile replace" entries will eventually sort itself out?

Thanks,

Hagler[/SIZE][/FONT]

---

### Post by BoneKracker on 2010-05-17
Are they actually new entries in the log, or are you looking at the same entries from before?

If they are new entries, it's possible that they are startup-related (the auditing system taking snapshots.  Hopefully another Ubuntu user will chime in and tell you they have the same entries.

I use kernel auditing on two of my machines (non-Ubuntu), but I don't have those particular messages).

However, when I quickly Google for profile_replace, I see many log excerpts from ubuntu users, and in the few I looked at, people are asking about entries other than those (the profile_update entries seem unrelated to what they are discussing).

So I wouldn't worry.  It's probably normal startup activity.  (My guess is the system is updating security hashes of key binaries, used to prevent hackers from replacing or altering them, but I really don't know.)

Hopefully an Ubuntu user will chime in and confirm this is normal (or normal after an update).  I only answered because it's late, your post was unanswered, and you sounded concerned.

---

### Post by Hagler on 2010-05-17
[FONT=Book Antiqua][SIZE=3]They are new entries at each start up, but other than that the system seems to be working fine[/SIZE][/FONT][FONT=Book Antiqua][SIZE=3] (touch wood).

Thanks for putting my mind at rest.[/SIZE][/FONT]


[FONT=Book Antiqua][SIZE=3]Hagler[/SIZE][/FONT]

---

### Post by BoneKracker on 2010-05-17
You're welcome.  Auditing systems generate a lot of log entries.  The basic idea is to create a record of significant changes, particularly if they might have been made with malicious intent.

Obviously, something like mounting a partition or replacing a file "might" be done with malicious intent, and such things are logged by many systems.  However, that doesn't mean they _were_ done so.

There appears to be a lot of information regarding the auditing configuration used by Ubuntu (Google "ubuntu auditing system").  Also, there is apparently a GUI for end user configuration of it (probably accessible through your administration-related menus; if you can't find it, I would expect you can type "sudo system-config-audit&" in the terminal to bring it up).  Browsing the information it displays might give you some insight into what these profile-related entries are.

Enjoy.

---

### Post by Hagler on 2010-05-17
[FONT=Book Antiqua][SIZE=3]Many thanks, I'll check your suggestions out.

Hagler[/SIZE][/FONT]

---

