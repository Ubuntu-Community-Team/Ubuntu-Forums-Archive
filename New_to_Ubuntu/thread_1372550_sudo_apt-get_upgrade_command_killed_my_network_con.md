---
title: "sudo apt-get upgrade command killed my network connection"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by akira2501 on 2010-01-04
Still having network problems – fixed one thing broke another.
 
Here’s what I did:
 
Installed Ubuntu 9.10
Created a folder, right-clicked and shared. This propted a download of Samba which I did.
 
When I tried to share the folder again I get the message "Failed to execute child process "testparm" (no such file or directory)
 
After a search I discovered this command as a fix: sudo apt-get upgrade
 
That did the trick, and everything seemed to work. My share was working and my Vista machines could see the Ubuntu share and Ubuntu could see the Windows share.
But then I ran into another problem, Firefox stopped working because of the upgrade. 
 
I restarted the computer. Now I have no internet connection or network connection.
Any idea what happened and how to fix it?

---

