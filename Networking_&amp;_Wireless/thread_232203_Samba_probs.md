---
title: "Samba probs"
date: 2006-08-08
forum: Networking &amp; Wireless
---

### Post by Phixion on 2006-08-08
Hello, I am trying to share some files from my Ubuntu Box on my Network, but I've encountered some problems.

When I choose to share a folder it brings the config window up, I choose to use SMB, allow browsing folder and in the advanced options I set the name of my network.

Now when I try access the folder on a Windows PC it asks for a username/password. I've tried using my Linux Username and Password but no luck.

What am I doing wrong here? :)

Cheers

---

### Post by jogeer on 2006-08-08
Have you tried just leaveing them blank, or just the password field blank?

---

### Post by gario on 2006-08-08
By default samba authenticates users against a separate smbpasswd file (instead of the system passwords).

Try adding your account to the smbpasswd file on your server, using:

```
sudo smbpasswd -a <username>
```

Then try connecting again from windows.

---

