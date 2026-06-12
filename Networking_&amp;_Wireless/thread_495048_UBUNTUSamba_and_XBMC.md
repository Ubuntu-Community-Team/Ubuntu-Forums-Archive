---
title: "UBUNTU/Samba and XBMC"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by grate on 2007-07-07
Hi all,

I've followed the instructions for installing Samba and enabling a share for Xbox Media Center from the following URL:

[http://ubuntuforums.org/showthread.php?p=2758412](http://ubuntuforums.org/showthread.php?p=2758412)

It looks like XBMC can find my newly created share, however upon accessing the directory it just gives me a ../ instead of the list of the files.

Dose anyone have any idea what may have gone wrong?

I am really new with Ubuntu and Samba! :(

Thanks for helping a novice out.

---

### Post by broncavfan on 2007-07-19
Hmmm, those instructions are pretty straight forward.  I used them to get samba working with my xbox.  You can also share files by right clicking them and selecting Share Folder...  Then, from the dropdown menu select "Windows Networks (SMB)".  That's the quick way to add files.  You can also edit your shared folders by selecting System->Administration->Shared Folders.  There you should double check your settings and make sure your shared folders are in the list.

If all that still fails I'd guess that you're not logging in to your computer correctly from your xbox, and instead of giving you an error message the xbox just gives you a root folder and nothing else.  XBMC is full of little bugs and glitches like that, so it wouldn't surprise me.  You'd be best just dropping the yourusername:yourpassword from the 

add this
"smb://yourusername:yourpassword@yourcomputerIPaddress/MyFiles/"

part of the tutorial and then logging in with the prompts.  If you still can't get it working let me know and I'll try to help.

---

