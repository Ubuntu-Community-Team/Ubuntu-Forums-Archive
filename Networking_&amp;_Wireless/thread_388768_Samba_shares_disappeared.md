---
title: "Samba shares disappeared"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by quiller on 2007-03-19
I've recently found that my Samba shares disappeared, at least on the Windows side. The shares are still configured on the Linux side, although from my notebook (Ubuntu) to server (Ubuntu), I get a "wrong fs type" error when trying to mount the shares via fstab. The *only* thing that has changed was that I installed and configured NFS on the server, mostly to deal with the fact that the Samba shares disappeared and I relied on those shares for several MythTV frontends to work...

To be specific: the Ubuntu server shows up in Network Neighborhood, but with only "Printers and Faxes" as an option. The shares don't respond through Explorer, typing the address directly or with net use on the command line.

I'm sure there are plenty of details I'm leaving out. Ask and I'll provide what I can.

---

