---
title: "I cant login?! I think somthing deleted my users file!"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by rhcm123 on 2009-01-05
I recently went on a vacation. I left my home server on at home, as usual, and went on my business. It was fine when I left - in fact, i ssh'ed to it the night before i left. I am running 8.10 headless.

Now, i cant login. On any account. ussr and cccp are my main accounts, and i get zip. root dosen't work either. nor does nobody. (I have the passwords for all of these accounts.) I cant get onto my webmin panel or my music sharing system.

I rebooted, and saw a whole host of error messages flooding through the boot screens. Apparently, other users (like dhcp and avahi) have been deleted too! Fortunatley, basic functions like DHCP still work.

DOES ANYBODY KNOW WHAT THE HELL HAPPENED AND WHAT I CAN DO TO FIX MY SYSTEM?


EDIT:
Btw, incase this turns up nothing, i am using the cd and attempting to rescue my system. will post results.

EDIT AGAIN:
I fixed root, at least. I don't know why or how, but I managed to get the recovery kernel working, and then i dropped down to root shell prompt. I belive root is now working, but I tied to change the passwords on all my other users, and it gave me "user not found errors", even for system users like nobody. However, other users like DHCP and ftp (a generic user running the ftp daemon and owning the ftp directories) are existent and i can change their passwords. Ill see if I can't add back my other users.

---

### Post by bumanie on 2009-01-05
You could try resetting your password and trying to reconfigure from within ubuntu once you have access. [This may]("http://www.psychocats.net/ubuntu/resetpassword") help, I hope it does.

---

### Post by rhcm123 on 2009-01-05
> **bumanie said:**
> You could try resetting your password and trying to reconfigure from within ubuntu once you have access. [This may]("http://www.psychocats.net/ubuntu/resetpassword") help, I hope it does.

This is actually exactly what i just did. However, the only user I could get working was root. (Don't tell me it's unsafe, I know the dangers and I am glat to just be able to login. :D ) Now I have to go make a copy of my other machines passwd file and copy it onto my malfunctioning server. I need to make system users like nobody, avahi-daemon, dhcpd, and my main login names. Crap, i sense a long night, or a complete system reinstall. 

Those system users don't go away lightly. Does anybody have any, and I mean any idea why those usernames vanished, and why the frequently login'ed users have vanished?

---

