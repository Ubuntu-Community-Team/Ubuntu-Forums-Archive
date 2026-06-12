---
title: "Hardy upgrade broke Kaffeine? Kaffeine and Samba problems."
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by JillSwift on 2008-04-26
When I try to open a media file from an unmounted share on a windows machine, Kaffeine says:```
11:38:20 PM: xine: cannot find input plugin for MRL [smb://server/J/HouseM.D.%2520Complete%2520Season%25201/House%2520MD%2520-%2520108%2520-%2520Poison%2520-%2520hdtv-lol.avi]
11:38:20 PM: xine: input plugin cannot open MRL [smb://server/J/HouseM.D.%2520Complete%2520Season%25201/House%2520MD%2520-%2520108%2520-%2520Poison%2520-%2520hdtv-lol.avi]
11:38:20 PM: xine: found input plugin : CIFS/SMB input plugin based on libsmbclient
```VLC can open files on the share, so can Totem movie player. Konqeror copies the files to local storage fine, too. Kaffeine *will* play the file if copied over or if I mount the share.

Upgraded to Hardy Heron yesterday, prior to the upgrade I could play files on the share in Kaffeine without problem.

Kubuntu 8.04
Pentium D, 2gb
100Mbps network

Pwease hep? =^_^=

---

### Post by bwp_88 on 2008-04-27
Same problem here. I've searched high and low on Google for a solution, but no luck.

In the end, I just set up a permanent smbfs mount in /etc/fstab. Not an ideal solution, but it works.

---

### Post by JillSwift on 2008-04-27
[COLOR=Silver]Well, while messing around with a sound problem (far too late at night, too tired, to frustrated... in other words getting ready to make a mess) I managed to maul my installation.
So, this morning I re-installed Kubuntu and... Kaffeine now plays off an un-mounted share without a hitch.
Go figure.

I'm still interested in what may have gone wrong, and bwp_88 can't be the only other one who had a similar problem. Anyone? Bueller? Bueller?

[SIZE=1][COLOR=Black](Bad info, ignore. Sorry).[/COLOR][/SIZE]
[/COLOR]

---

### Post by JillSwift on 2008-04-28
oops.

Strike that, my bad. Kaffeine plays any file on the share fine, unless the folder and/or file name has any URL escapable character in it (like a space). Then it chokes. Sorry. :oops:

---

### Post by JillSwift on 2008-05-13
BUMP of DESPERATION

---

### Post by danramos on 2008-05-17
It appears to be docuemented as a bug here:
[https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/85049](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/85049)

But disappointingly, its 'importance' is set to 'undecided.'

---

### Post by irrobert on 2008-07-06
same problem here with Kaffeine: unable to play music-files or video-files from Sambaserver.

can anyone give an indication if solution is to be expected? If not I'll try some other program to play music / video. Rhythmbox works though it cannot play video...

I hope to read something... I would be grateful.

Robert

---

### Post by patsissons on 2008-10-07
pretty sure this problem lies somewhere in the dcop server.  You can indeed play files from samba shares which are unmounted and have spaces in them, you just have to avoid the dcop server.  The dcop server is used when you double click a file in konqueror (for example), to avoid dcop simply drag the file from konqueror to kaffeine's playlist (for example).  You can also use kaffeine's built in browser, which seems to work fine.

I also experienced issues playing DVD's.  My workaround for this problem was to drag the dvd to the playlist, usually after having browsed to media:/ in the internal browser.

Hope this helps people out, i know it saved me a lot of grief! :)

---

