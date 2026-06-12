---
title: "Having trouble upgrading/updating from 9.04"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by The_Proffessor on 2011-08-25
Hi there. Not sure why but I never really got the memo to upgrade my distro. And then for a while I kinda didn't care. But since I've yet again decided updating stuff is important I'd like to go up to this fancy new 11 version. However the automatic update program isn't working, probably because it's trying to upgrade my system to 10.04 which is no longer supported. 

Anyone got any terminal magic that can fix this? preferably in a way that let's me keep my files?

---

### Post by akoskm on 2011-08-25
It is working, and that is the way how it works! You have to upgrade incrementally, from 9.04 there is no direct update according to the wiki:
[https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes")
Upgrading information in the link above ^^.

---

### Post by kmsalex on 2011-08-25
You relay might be better off backing up your files and reinstalling 11.04. upgrading would drag your systems packages though 4 releases errr... relay a clean install might be best.

P.S. You might want to read/watch up on unity which replaces the gnome 2.3x interface in your previous ubuntu. you may like a derivative (kubuntu, xubuntu, lubuntu) better.

---

### Post by 3rdalbum on 2011-08-25
9.04 is well and truly out of support now, so I don't think an upgrade would work without changing your software sources to point to the 9.04 archive. Updating from 9.04 to 10.04 and then to 11.04 will take a fair amount of time and a lot of downloading, and the possibility of a botched upgrade is twice as big as just one upgrade.

My advice would be to download the 11.04 CD and use the "Upgrade" option in the installer. It will preserve your /home directory including your settings, and install the repository software that you currently have installed, assuming it's available in 11.04.

---

### Post by oldos2er on 2011-08-25
> **The_Proffessor said:**
>  However the automatic update program isn't working, probably because it's trying to upgrade my system to 10.04 which is no longer supported. 


10.04 is most certainly still supported. Did you mean to say 9.10?

---

