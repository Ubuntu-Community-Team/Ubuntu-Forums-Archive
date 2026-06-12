---
title: "Access problem from Windows"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Heicron on 2008-08-28
I have been able to share files among  Vista, XP and Ubuntu boxes on a home wired network. Recently I cannot access Ubuntu files from the two Windows boxes. I get a message saying "the account is not authorized to log in from this station". I can access the shared Windows files from Ubuntu. (804) I do not have passwords activated for the Windows boxes. Also I noticed that when I first launch Evolution and click to download mail I get a dialog box about a key ring. I then type in my Ubuntu password and mail is then downloaded.
What setting could I have messed up to have this problem?

Thanks.

---

### Post by amedac on 2008-08-28
Open terminal, and type:
```
sudo gedit /etc/samba/smb.conf
```

and in GLOBAL section add this line:
```
usershare owner only = False
```

after that open terminal:
[CODE] sudo /etc/init.d/samba restart [CODE]

---

### Post by Heicron on 2008-08-30
Thanks but that didn't work. Any other setting to check?
It seems that this happened after I ran an update but I'm not sure.

---

### Post by Heicron on 2008-08-31
I got it working again.I re-entered the user names and passwords. I don't know how I broke it though.

---

