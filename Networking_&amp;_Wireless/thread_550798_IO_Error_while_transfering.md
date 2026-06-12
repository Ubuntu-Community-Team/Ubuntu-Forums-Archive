---
title: "I/O Error while transfering"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Carl_Barks on 2007-09-14
I have setup a LAN between Ubuntu(main pc) and Xp (on my laptop)
While i do copy-paste the files i wanna transfer, in most of them i get an I/O Error.

Any ideas? Thnx. 

Also, how can I access my Ubuntu pc through Xp? I always get a password prompt. I tried editing samba.conf but with no luck ...

---

### Post by Carl_Barks on 2007-09-14
Anyone ??!

---

### Post by Zorael on 2007-09-14
In either case, you're not going to get an answer in 21 minutes, unless perhaps you lurk IRC channels.


Now, for some basic troubleshooting.
[LIST]
[*]Do you have another machine in your network you could try copying to? If it only happens towards one machine, likely the issue resides in either how the share is mounted (ie, which options used), or in the target computer.
[*]Are you copying towards a dirty NTFS share?
[*]Does it only happen when copying and pasting, or also upon drag and drop, or perhaps when doing a terminal cp as well? Could be some elusive bug, heck if I know. As I understand, there's some protocol involved with dragging and dropping, which Nautilus thus far lacks, making dragging and dropping from Archive Managers (and similar applications) impossible. Perhaps there's something wrong there.
[*]When it does happen, is there something added to the end of the output of dmesg? (Type dmesg in a terminal.)
[/LIST]

Basically, pin-point.

---

