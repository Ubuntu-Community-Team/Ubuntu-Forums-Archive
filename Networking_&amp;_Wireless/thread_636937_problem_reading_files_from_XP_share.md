---
title: "problem reading files from XP share"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by ubimal on 2007-12-10
Here's a brief description of a simple LAN:

New install of Gusty Gibbon 7.10 on amd64 clean new PC
2 network cards, one for outside, one for LAN w/ XP PC attached
Firestarter used to set up firewall  & set up ip forwarding for the LAN, all LAN PC's are trusted

Had a few problems getting samba to work to start with, reboot of both PC's helped - perhaps restarting smbd and not nmbd was a mistake.

Now, after adding users and passwords that match i can read files off the ubuntu share on the XP but reading files from XP on ubuntu is flaky:

- using places/network i get a 'windows network' icon, click that get to the workgroup icon and click the workgroup icon and it says "The folder contents could not be displayed".
- yet if i choose Places/ connect to server and enter the name of the PC it mounts the share for me instantly and i can copy files.

What can i do to make the network browser display the workgroup?
--
thanks

---

