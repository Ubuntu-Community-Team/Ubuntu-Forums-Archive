---
title: "[SOLVED] Samba and .dmrc issues"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by JawsThemeSwimming428 on 2007-09-21
For the past two days I have been trying to get my two PC's (one running Feisty and a brand new Vista Home Premium machine) able to see eachother over my Linksys Wireless network. I followed Stormbringer's Samba guide ([http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)) and was able to see my Feisty share from my Vista machine. After a Vista and Feisty reboot, I can not access the mapped drive or even browse to my Feisty machine to remap it (they both have Static IP's). One thing I did notice... I tried to share my home folder, but when I rebooted I was presented with the following message onces I typed my password and hit Enter to log in:

" User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

I am not quite sure what that means or what I should do to fix it (or if it has anything to do with my network folder access problem above... In smb.conf I elected to share /home/willy which is my home directory).

I have not been able to resolve this issue, anyone that can help me out I would be  VERY grateful!! Thanks.

---

### Post by JawsThemeSwimming428 on 2007-09-21
I reset my permissions for my home directory according to Stormbringer's post on his Samba guide (page 4 right before the smb.conf). I am still getting that .dmrc error, how do I get rid of it?

---

