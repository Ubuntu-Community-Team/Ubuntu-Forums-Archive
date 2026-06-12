---
title: "SAMBA &amp; Ubuntu for dummmieesssss??????"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by klgsx on 2007-05-24
his is killing me.. i have been reading and following every single post out there.  This is like the post # 9999999999 on this problem.. so maybe one of the Ubuntu experts can trow me a bone.

I have 2 pc:

1) win xp
2) ubuntu desktop

they are both within the same network (yes.. i configure the samba.conf) and restarted the ubuntu box using

sudo /etc/init.d/samba restart.

the windows xp machine see the Ubuntu box - where i have a share folder

my problem is that whenever i double click on the ubuntu box i get prompted for a user name and password.

I entered username+password (yes.. an admin account that i have created in ubuntu) BUT i can not log in to the box or see the files there..

Suggestions??

Thanks

---

### Post by croquagei on 2007-05-24
i'm having the same problem.  When i connect into my ubuntu machine with windows \\laptop\ i get prompted for a username and password

---

### Post by JSThePatriot on 2007-05-24
Fellas,

Here is a link to a post I made that helped someone else out with their Samba configuration and setup. I hope it will help you two as well.

[http://ubuntuforums.org/showpost.php?p=2700153&postcount=9](http://ubuntuforums.org/showpost.php?p=2700153&postcount=9)

I am able to connect very easily with Windows XP, I do sometimes have some issues with Vista and the Username/Password box coming up.

If my solution doesn't work then maybe you could try some of the other links I posted. My solution is a mixture of all the links.

JS

---

### Post by anarchyreigns on 2007-05-24
It wants a Samba password, not your logon user name and password. See below to create.
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

---

### Post by JSThePatriot on 2007-05-25
> **anarchyreigns said:**
> It wants a Samba password, not your logon user name and password. See below to create.
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username

I had tried some similar lines, but I may give them another shot. Thanks for that information.

JS

---

### Post by AsGF2MX on 2007-05-26
One very under-estimated thing which you haven't posted is simply, right after your failed login attempt:

- from your ubuntu box,  at the prompt, type "tail /var/log/samba/log.smbd"

Can't remember if you have to sudo or not (I run Debian on my little NSLU2;)). If you post that here, at least we'll have some idea of why your authentication is failing.

---

