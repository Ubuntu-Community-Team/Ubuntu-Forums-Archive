---
title: "Emergency for an upgrade (SMB)"
date: 2018-06-13
forum: Networking &amp; Wireless
---

### Post by trevorlowe97 on 2018-06-13
Hello everyone I am trying to make this quick I hope i can get some help from the grand masters! I started a new job and they're computers were running SOO SLOW. So I installed Ubuntu 16.04 (side loaded) to a couple of the desktops, they love it! The only problem is that, they all use the same printer/scanner. I have installed the correct printer drivers with the PPD file so we can print just fine!!! But the scanner used SMB EX: "Bob goes to scan paper, the scanner forwards it to a folder for them.".  I got $200 for speeding up there work! But there scanner uses a windows SMB server type deal locally. And i just need to connect it. PLease guys im sorry about this post. But hey I plan on helping back when i can.

---

### Post by Autodave on 2018-06-14
What printer are you using?  Wired, wireless, ethernet?

---

### Post by SeijiSensei on 2018-06-14
So how do Windows users access the folder?  Presumably they have some connection like \\server\share, where "share" could be the folder of scanned documents, or perhaps its parent.  Try opening Nautilus and entering "smb://server/share" in the address bar.

---

