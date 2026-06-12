---
title: "Newbie question - permission"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by rmadams1 on 2010-10-14
I've tried to figure this one out on my own but am having an issue. I've installed 10.10 and am trying to copy a downloaded folder from /downloads/ to ../opt/ but the /opt/ file is owned by root and my user account doesn't have permissions.
 
I've ckd [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) for info, and have also done a comparison between my 10.10 box and the 9.04 I've got running that lets me copy stuff around. I've also gone into Users & Groups and given my user Administrator permissions and added it to the admin group.
 
I know I have to run sudo chown -r, but apparently I'm confused on the correct syntax after this because it keeps failling. 
 
Any help would be appreciated. 
Thanks~

---

### Post by tgm4883 on 2010-10-14
you could copy the file on the command line using sudo

or you could chown the directory 

"chown --help" is your friend

---

### Post by rmadams1 on 2010-10-14
Got it while you were typing. I needed to just keep looking a bit.
 
Thanks!

---

