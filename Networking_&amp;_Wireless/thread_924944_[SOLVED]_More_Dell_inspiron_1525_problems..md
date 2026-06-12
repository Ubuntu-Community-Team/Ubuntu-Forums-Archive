---
title: "[SOLVED] More Dell inspiron 1525 problems."
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by sTpny on 2008-09-20
Ok, I got a bit of a wireless problem here.  The computer is a dell inspiron 1500.  I installed using the iso from dell, but I booted into a live session and installed by hand, wiping out all the existing partitons and creating three new ones. / and /home and a swap partition. I then connected an ethernet cable and, after enabling the backports repositories and installing all of the recommended updates, the wireless starting working. I think a reboot was required, but I'm not sure. Anyhow, while the install seemed to go ok, the computer would often fail to complete its routine fsck check of the root partition.  Should I have used the automatic dell-install option for my graphics card? There was an option for it on the disk, but I wanted to make sure I could wipe out those partions, and once they were gone completely, I thought it would be safe to just install from the live session. Was i wrong? For those of you who are unaware, the inspiron 1525 has a problem with corrupting the root partion when people push the little button with the house on it. It quick loads some crappy windows thing, and breaks windows systems, hence, the iso from dell. Anyhow, Something screwed up, and the user, not me, did a forced shutdown, and afterwards, couldn't login, or rather, the session wouldn't finish loading. It would load the cube, which worked, and the active screenlets, but no panels or icons, and no left click either. Being much of a n00b myself, I fixed it by making a new temporary user, then I moved the users pics and photos into the new users home folder with a sudo nautilus. Then I deleted the broken user account and its home folder, rebooted, and then added it again as a new user. Then I moved Photos and Pictures back into the account and deleted the temporary user. Ugly, I had to chown, which was a first for me, and all the settings were lost and needed to be reset, but the user can now login again with his username, which was kind the point.  Only thing is, now the wireless doesn't work. It seems to be working, but when I scan for networks with the kwifi manager, it finds none. So, questions...

Should I have used dells default install for this machine? Should I install again using that option? Are the drive errors reported by fsck happening because I didn't use the dell specific install option? Will they go away? I've been saying yes to everything after manually running fsck from the shell it dumped me into. I think the drive is failing, is there a way I can check? 

How would you have fixed the users session? How can I see what actually happened, to see what was actually broken? (all the files still exist in a root trash can) What were my other options? 

Most important?? How do I get the wireless working again? and less important, why isn't it working? Could I have accidently turned it on only for that one user? Should I follow the howto for using ndiswrapper? I shouldn't have too, because it was already working. 

Anyhow, for now the cable stays connected, anchoring my poor friends laptop to his telus wireless modem. Help is most appreciated in this matter, and all who are of assistance will be thanked. I don't mind reading either, so bring on the links as well.  ;)
 

Thanks.

sTpny

---

