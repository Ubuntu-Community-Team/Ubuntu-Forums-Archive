---
title: "“Folder contents could not be displayed” – Samba"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by Quicky on 2007-01-12
Thought I'd share a potential solution to specific file sharing issue that may have been experienced by some users.

*Short version:*
If you receive an error similar to the title of this post when attempting to access shared folders on a Windows PC from an Ubuntu machine, it could well be firewall related. And your wife's fault.

*Long version:*
Up until recently I'd been happily sharing files between an Ubuntu machine and an XP machine, primarily for backing up photos and so forth. About two weeks ago, I was suddenly unable to access shared folders on the Windows PC from my Ubuntu laptop. While the laptop could see the XP machine appearing in the mshome network of Network Servers, every time I tried to access the Windows machine the only response I got was a dialogue stating that the 'Folder contents could not be displayed'.

What initially set me down the wrong path when trying to resolve the problem was that the XP machine had no trouble accessing and writing to shared folders on the Ubuntu machine, so I assumed the problem was to do with Samba.

For the life of me I had no idea why it was happening, and after adjusting various settings within smb.conf to no avail, I tried searching on Google to find that plenty of people had encountered this issue, but saw almost nothing in the way of solutions.

Last night however, when a mate came round with her Windows laptop, I had no trouble accessing the shared files on her computer – therefore the problem must actually have been my XP computer rather than Ubuntu. 

After some fruitless fiddling with various network settings in XP, my missus eventually wandered in and told me offhand that she'd recently purchased and installed a new virus protection suite. As it turned out, the default settings for the security system (F-Secure) included a software firewall which blocked Windows file sharing despite what options were selected elsewhere. After adding a rule to the F-Secure firewall that allowed the function, the samba sharing issue miraculously disappeared.

Obviously there's a lesson for me to learn here, and it isn't computer related.

---

