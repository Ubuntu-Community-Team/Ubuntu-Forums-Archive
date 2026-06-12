---
title: "Samba server not working"
date: 2013-09-28
forum: Networking &amp; Wireless
---

### Post by andrewkirk on 2013-09-28
I have set up Samba server working on my laptop running Ubuntu 13.04, and I have shared the folder /media/Data, with full read-write permissions for all network users including guests. I did that through the Properties>Sharing GUI from Nautilus, run as root ('sudo nautilus' from command line in terminal).

However, when I try to access the folder from networked computers I get errors. THey can see the shared folder, but won't open it.

From an Android device I get this:

[INDENT]Login failure. This may be caused by: - the account has no permissions.[/INDENT]

From a Windows XP PC I get this:

[INDENT]U:\ is not accessible. Access is denied.[/INDENT]

From a Mac Mini running OS X I get this:

[INDENT]The operation can't be completed because the original item for "Data" can't be found[/INDENT]

These other devices all share perfectly happily with one another, in both directions, so it's the Ubuntu 13.04 laptop that is at fault.

I noticed something else and I don't know if it's relevant:
The subfolders of /media/Data have the sharing box unchecked when in Nautilus I inspect Properties>Sharing. This, despite the fact that it asked me, when I first told it to share /media/Data, if I wanted to apply permissions to its contents and I said yes, and it then did some processing that took a little while, which I presumed was resetting permissions for everything in the folder.

I would be grateful if anybody can tell me how I can make the Ubuntu laptop share properly.

Thank you

The laptop is HP EliteBook 2530p Intel x86 32 bit. The Ubuntu is 13.04 32-bit.

---

### Post by TheFu on 2013-09-29
Nautilus sharing ... arrrg.  Lots of issues using that.  Use Nautilus as a client, but not as a server ... until they fix this aspect at least.

If you really want to share storage, modify the /etc/samba/smb.conf file with an editor as you want, restart samba.  Lots of examples on how to do this on the internet. The version of samba running could be important.  Things chnaged drastically in samba4, which I don't have **any** experience using.

---

