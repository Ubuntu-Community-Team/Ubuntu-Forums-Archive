---
title: "nextcloud webdav"
date: 2020-07-01
forum: Networking &amp; Wireless
---

### Post by jduns on 2020-07-01
I used to connect to my nextcloud server with Dolphin; this was (and is) the entry: webdav://ecloud.global/remote.php/webdav/.
In these last times I am asked every time for user and password, and this is very annoying.
I tried to creare an account network, following [https://docs.nextcloud.com/server/16/user_manual/files/access_webdav.html](https://docs.nextcloud.com/server/16/user_manual/files/access_webdav.html), 
but unsuccessfully.
I'd like to use Dolphin, and not another app (like nextcloud client). There is a way? I think something like webdav://ecloud.global/remote.php/webdav/ + user and password: but how?
Thanks!

---

### Post by SeijiSensei on 2020-07-01
You could try including the username and password in the URL:
```
webdav://username:password@server/
```

However, unless you're using the secure version of the webdav protocol, or connecting over a secure link like a VPN, this transmits your credentials in the clear.

Are you running Kubuntu?  Are you using the KDEWallet to store usernames and passwords? (System Settings > Account Details > KDE Wallet)

---

### Post by jduns on 2020-07-01
Thank you. Yes, Kubuntu. And yes: maybe the problem is that I had disabled KDE Wallet. Now I will try.
EDIT
Unfortunately no, even enabling KDE Wallet the problem is still there.
I tried your tip, but unsuccessfully: I mean I didn't get any error message, but the tab remain white, empty. Maybe the problem is that my username in /e/ is an e-mail account (wirth an "@"), so or I put the whole e-mail name, and therefore I have two "@", or I omit "@e.mail" in my username but this makes incomplete the username. :(

---

### Post by SeijiSensei on 2020-07-01
You can try
```
webdav://'user@email'@webdav_server/
```
but I have no idea if that will work.  If it does, you should be prompted for the password.

---

### Post by TheFu on 2020-07-01
There is a documentation link for nextcloud: [https://docs.nextcloud.com/server/18/user_manual/files/access_webdav.html](https://docs.nextcloud.com/server/18/user_manual/files/access_webdav.html)
It says the URL for **Nautilus** is: dav_s_://example.com/nextcloud/remote.php/dav/files/USERNAME/
or
dav://example.com/nextcloud/remote.php/dav/files/USERNAME/ if HTTPS certs aren't setup.

For **Dolphin**: webdav://example.com/nextcloud/remote.php/dav/files/USERNAME/ They ignore the http or https aspects completely in that section. For my username, webdav://example.com/nextcloud/remote.php/dav/files/TheFu/

There are warnings and common issues in the link too.

---

### Post by TheFu on 2020-07-01
I tested using the Mate Caja file manager and it connected quickly using the davs:// URL. 

A popup username+password dialog was displayed that asked how long to remember the credentials - forever, this session, until reboot.  It looked like a gvfs dialog from Gnome.  It doesn't use a "real mount", so the /etc/mtab wasn't modified and nothing was shown under /media/{userid}/ or in /var/run/user/1000/gvfs

The problem is that opening data files (music or photos) fails to probably work. I think it is that the players don't know how to handle DAV URLs. I suppose if drag-n-drop file management is the purpose, then the file manager would be fine. If direct access to the files is desired, then using the webdav mount technique via an fstab or autofs mount would be more useful.  Perhaps.

---

### Post by jduns on 2020-07-03
Thank you, but your tips didn't work. Eventually I stored the nextcloud password as automatic text...

---

### Post by TheFu on 2020-07-03
> **jduns said:**
> Thank you, but your tips didn't work. Eventually I stored the nextcloud password as automatic text...

Perhaps you could be more vague?  Please?  ;)
There were about 10 "tips" provided.  I doubt davfs failed.

---

