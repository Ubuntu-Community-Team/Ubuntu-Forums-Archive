---
title: "Samba network shares asking for passwords?"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by m0u53m4t on 2008-05-27
When I try and browse any share on my Windows network it asks for a username and passwords and rejects anything I give it.

I'm running Hardy Heron.

Also, whenever I try to edit my samba shares I can add them and stuff, but as soon as I close the dialogue it crashes so I've had to add them by editing the conf file manually.

Help?

---

### Post by sisco311 on 2008-05-27
Setup a samba password.
Open a terminal:
```
sudo smbpasswd -a *your-username*
```Add a new user and setup a smbpasswd:
```
sudo useradd windowsusername
sudo smbpasswd -a windowsusername
```

You can use your-username and samba password or windowsusername and samba password to access the shares.

---

