---
title: "samba pdc win7 Windows cannot update your roaming profile completely"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-07-22
I get the error message "Windows cannot update your roaming profile completely. Check previous events for more details." when shutting down or rebooting my windows 7 client.

used to get win7 on domain [http://wiki.samba.org/index.php/Windows7](http://wiki.samba.org/index.php/Windows7)
used
[https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/11.04/serverguide/C/samba-dc.html) and [http://www.youtube.com/watch?v=8MWBhlaLIxQ](http://www.youtube.com/watch?v=8MWBhlaLIxQ)
to conifgure samba

sudo chmod -R 1777 /home/lance/500gb/mombackup/samba/profiles
sudo chmod -R 1777 /home/lance/500gb/mombackup/windows/profile.V2

I have a file in my netlogon
called leanne.cmd it contains
@echo off
echo off
NET USE J: \\192.168.2.7\leanne

The file has been unix2dos /samba/netlogon/logon.cmd




my smb.conf, samba log files and windows 7 log files are in the folder called files.zip

---

