---
title: "Playing music on Rhythmbox from NSLU2 running Debian"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Lowcountry on 2009-12-14
Hello.
I have only one linux problem and it is really got me down.

I use a NSLU2 running Debian ARM as a music server(among other things) for my LAN.
On my Windows boxes, I use WINAMP to access these files.
On my linux boxes, I use Rhythmbox--and I really like it!

On a fresh install, I open Rhythmbox, naviagate to preferences, click the music tab, and select the folder on the NSLU2 where my music is located.
This works perfect on windows.
THis works perfect on Debian Testing.
But, for some reason, ever since 9.04(maybe 8.10), when I do this, nothing happens.  NO songs show up.

What could be the difference between the last few Ubuntus & Debian testing.

If I could fix this, I would be very happy!
Any ideas?
Thank you.

EDIT--BTW, I can get the folder to share.  It mounts on the desktop with no problem.  I can access the files and play them individually with movie player.
Here's what it looks like in Rhythmbox:
> smb://nslu2/guest share/

---

### Post by tgalati4 on 2009-12-14
rhythmbox uses avahi to see music shares.  It's possible that samba shares were either broken (through a regression) or dropped.

Can you run an avahi daemon on your slug?

Check your log files (/var/log/samba) on both the slug and on your remote machine.

Also, as Ubuntu matures, it's security policies have become more restrictive.  Check the control panel, users and groups, privileges.  Make sure you have the appropriate boxes checked.

---

### Post by Lowcountry on 2009-12-14
> **tgalati4 said:**
> rhythmbox uses avahi to see music shares.  It's possible that samba shares were either broken (through a regression) or dropped.

Can you run an avahi daemon on your slug?

Check your log files (/var/log/samba) on both the slug and on your remote machine.

Also, as Ubuntu matures, it's security policies have become more restrictive.  Check the control panel, users and groups, privileges.  Make sure you have the appropriate boxes checked.
Thanks for the help.

I don't see how it could be my NSLU2, as Debian sees the share just fine.

I tried the privileges, checked everything, but still nothing.

Any other ideas?

---

### Post by Lowcountry on 2009-12-15
My Debian box shows it as
```
smb://nslu2/guest**%20**share/
```

But even when I add the "%20", it still won't pick it up.

---

### Post by tgalati4 on 2009-12-15
Make sure that you as a user belong to audio and video user groups.

man groups

---

### Post by Lowcountry on 2009-12-15
> **tgalati4 said:**
> Make sure that you as a user belong to audio and video user groups.

man groups

I am.

What is "man groups"?

---

### Post by tgalati4 on 2009-12-15
In a terminal run the following:

groups

man groups   (spacebar to move forward, q to quit)

Could be a parsing problem.  Try creating a small share directory without any spaces:

Instead of

smb://nslu2/guest%20share/

How about

smb://nslu2/guest_share/

---

### Post by Lowcountry on 2009-12-15
> **tgalati4 said:**
> In a terminal run the following:

groups

man groups   (spacebar to move forward, q to quit)

Could be a parsing problem.  Try creating a small share directory without any spaces:

Instead of

smb://nslu2/guest%20share/

How about

smb://nslu2/guest_share/

I REALLY appreciate all the help with this.  

I renamed "guest share" to just "share"...I thought that would be it, but still nothing:(

```
davisaw@EeePC:~$ groups
davisaw adm dialout fax cdrom tape audio dip video plugdev fuse lpadmin netdev admin sambashare

```

---

### Post by tgalati4 on 2009-12-17
I am at a loss as to what the problem is.  I would search for an arm-compiled version of avahi-daemon.  If you get that running on your slug then rhythmbox will pick it up automatically as a music share.

Do any errors show up in /var/log/samba?

---

