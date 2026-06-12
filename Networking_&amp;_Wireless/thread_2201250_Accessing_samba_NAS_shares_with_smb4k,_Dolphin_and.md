---
title: "Accessing samba NAS shares with smb4k, Dolphin and Nautilus"
date: 2014-01-23
forum: Networking &amp; Wireless
---

### Post by royleith on 2014-01-23
For many versions of Kubuntu and Ubuntu Studio I have been unable to access my samba shares on my Network Attached Servers whether via Thunar, Nautilus, Dolphin or smb4k. However, in Dolphin, typing the (static) IP address brought up the shares. For the last few years, nothing has worked with smb4k. As a short term solution I put a shortcuts in Dolphin Places which accessed the NAS devices via the static IP addresses.

A little while ago I found a post here with the solution. I cannot find it a second time and so I give the originating link with the solution.

[http://ubuntuswitch.wordpress.com/2010/02/05/nautilus-slow-network-or-network-does-not-work/]("http://ubuntuswitch.wordpress.com/2010/02/05/nautilus-slow-network-or-network-does-not-work/")

In summary:

> Edit /etc/samba/smb.conf (as root) and change the following line

*; name resolve order = lmhosts host wins bcast*

 into this (delete semicolon and move host to the end)

* name resolve order = lmhosts wins bcast host*

Now restart your PC (restarting samba and killing nautlius does not work).

I am in Kubuntu ATM and have only checked Dolphin and smb4k (specially installed for the test). smb4k worked out of the box and with no changes to the options. The NAS shares appeared immediately in Network Neighbourhood. In Dolphin, the workgroup appeared immediately and contained the NAS and, within it, the shares.

I have accessed anonymous shares and shares with the ID and password entered in System Settings - Network and Connectivity/Sharing and both work. However, the traditional ID and password requester fails to show up on other accounts.

I have searched for solutions over the years and I would point out that early comments about smbd and nmbd seem no longer to be relevant. I believe that Linux distributions changed to SMB/CIFS protocol. I have seen similar problems going back as far as 2008.

Roy Leith

---

