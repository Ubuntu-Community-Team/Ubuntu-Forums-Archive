---
title: "Samba shares are accessible, but not visible in Nautilus"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by mb_webguy on 2008-07-16
Recently, Nautilus has stopped displaying my Samba shares, though I can still access them by typing the full address of the share.

I have three computers on my local network: two running Ubuntu Hardy Heron, and one running XP.  Everything works fine from XP, but neither of the Ubuntu machines show any shares in Nautilus (though the workgroup is visible, and I can still access the shares by typing the full address).

Since everything works fine from XP and I can see all shares using smbclient from the terminal, I don't think this is a problem with my Samba configuration (though I'm attaching the smb.conf file for the computer I'm currently using just in case).  If this is a problem with Nautilus, however, I'd think that a lot of other people would be having the same problem.  OTOH, if it were a configuration problem, it seems odd that I'd suddenly be having the problem on both of the Ubuntu systems at the same time.

Any ideas?

---

### Post by peakshysteria on 2008-07-16
Can you give newbie an example of what you refer to as full address? Browsing the forum for a solution to the same problem it seems. I started this thread: [http://ubuntuforums.org/showthread.php?t=861315](http://ubuntuforums.org/showthread.php?t=861315)

---

### Post by mb_webguy on 2008-07-16
OK, let me try a more specific example.

My two Ubuntu systems are named the-tardis and access-mundi.

If I open Nautilus on access-mundi and go to Network, I see the icon for Windows Network.  If I double-click Windows Network, I see the Workgroup icon.  If I double-click Workgroup, I get nothing -- no error messages, just no icons.  I should be seeing an icon for each of the three computers.  For that matter, I should have seen those icons under Network.

However, if I type "smb://the-tardis/music/" (which is the address of a particular Samba share on that computer) in the Nautilus address bar, I can access all of the files and folders in that share.  In other words, the shares are all there, but I simply can't see them in Nautilus unless I'm directly accessing the shared folder.

The same is true if I try to pull up the access-mundi shares from the-tardis, but from my XP system I can browse to the-tardis and access-mundi with no problems.

---

### Post by peakshysteria on 2008-07-16
I got the same problem as you. Only if I try to type in the path to the share I get:
[[img]http://bildr.no/thumb/228030.jpeg[/img]](http://bildr.no/view/228030)

So for the time being I can only access my media center by ftp. More than a bit irritating.

---

