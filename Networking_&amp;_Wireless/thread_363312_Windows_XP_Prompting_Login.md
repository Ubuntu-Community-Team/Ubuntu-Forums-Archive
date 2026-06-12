---
title: "Windows XP Prompting Login"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by ZipCrash on 2007-02-16
Ok before I start let me say that yes I'm a noob to ubuntu. :)

I have setup my shares on Ubuntu 6.10 but when I try to access it via my Windows XP computer it prompts me or a username and password. I checked the smb.conf file and the option is off and when browsing my network in XBMC it doesn't prompt me at all. I can't figure out why XP is asking for a username and password and it won't even accept my login info. I'm not sure what I'm doing wrong or if I need to turn some other feature so if anybody could help It'd much appreciated. Thanks!

---

### Post by alyoung on 2007-02-16
Were you entering your Windows login information or your Ubuntu login information?

Try your Ubuntu login information if you have not already.

---

### Post by ZipCrash on 2007-02-16
Yea that's what I tried.

---

### Post by Rhaddad on 2007-02-16
in terminal

sudo smbpasswd -a user (replace user with your user you want to use for networking)

then it will ask for password.

everything should work from there

---

### Post by ZipCrash on 2007-02-16
Yea I ended up having to do that. I looked around and around, seems like that's my only option. Apparently making the share an NTFS drives causes that problem. Oh well not a big deal to have to login everytime. Thanks for the help.

---

