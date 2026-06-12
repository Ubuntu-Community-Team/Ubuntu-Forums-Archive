---
title: "network password"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by danip on 2007-08-31
Ok ive searched the forum for this answer but nobody seems to be able to give one but ill give it another try.  ive got my computer set up to share and my windows computers can see this ubuntu laptop but it asks for a password to get on here.  ive tried using my username and password and nothing.  the sudo password is the same and that doesnt work.  i cant even get into my windows computers either, they also ask for a password that ive no idea of its existence.  how can i get rid of the passwords? or what are they supposed to be by the default? i honestly dont want any passwords set up at all.

---

### Post by spd106 on 2007-08-31
I'm going to assume that you have already installed the samba server package. Have you added any users to the smbusers group. This is done with the following command, then you enter the user's password.
```
sudo smbpasswd -a username
```

To get access to your users home directory from a remote computer I usually edit the /etc/samba/smb.conf file by uncommenting the "security = user" line under Authentication.

---

