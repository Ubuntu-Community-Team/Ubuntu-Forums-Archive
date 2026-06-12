---
title: "ok ok how ARE deamons loaded inet or xinet or sane"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by doccpu on 2007-06-17
i am trying to get samba to work and it says (hah hah ) that it needs to have smbd and nmbd loaded. Probly in inet.d or inetd.conf or xinetd.conf or saned.conf or...... ok where does ubuntu load them?
[email]dhorner@usa.net[/email]
where can i get real manuals for ubuntu?

---

### Post by spd106 on 2007-06-17
The Ubuntu Samba packages contain the daemons you require to allow smb/cifs shares. They are stand alone daemons and should start up without the need for any inet super server. Though you may have to edit the /etc/samba/smb.conf to work with your Windows Domain/Workgroup.

The best information resource for Ubuntu is the Wiki and you will probably find the community help docs to be useful in this case.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

