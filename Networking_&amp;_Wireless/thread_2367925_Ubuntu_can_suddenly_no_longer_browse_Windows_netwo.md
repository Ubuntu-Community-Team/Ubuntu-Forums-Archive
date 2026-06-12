---
title: "Ubuntu can suddenly no longer browse Windows network, SMB shares.  What broke?"
date: 2017-08-04
forum: Networking &amp; Wireless
---

### Post by oldsmobile_mike on 2017-08-04
This is going to sound dumb, but has something changed recently with regards to accessing Windows networks in Ubuntu?

I fired up my Ubuntu laptop (latest version, 17.04) and installed all its updates today.  I don't use it very often, haven't turned it on in a month or two.  And I am having a remarkably difficult time accessing my Windows shares - much more difficult than it should be - the only thing that's changed was to disable SMBv1 on most of them due to WannaCry/other recent threats.

On my laptop, opening the file browser and clicking on "Other Locations" --> Windows Network results in nothing happening.  Literally, no response at all.  I swear this used to just work without any issues.  So I tried "sudo apt-get install samba" and "sudo apt-get install sambaclient", based on some google searching, and now I get the message "Opening smb:/// You can stop this operation by clicking cancel" - but nothing happens after that.

I'm having a little luck connecting to some shares on servers that still use SMBv1 if I enter my domain credentials, but nothing on devices that use SMBv2 - even shares that are not password protected.  "Unable to access location, Failed to mount Windows share: Connection timed out".

Also I used to at least be able to see the names of the machines connected to the local network when I tried to browse it.  Any suggestions?

---

### Post by oldsmobile_mike on 2017-08-04
This is pretty much what I get:

[ATTACH=CONFIG]276256[/ATTACH]

I swear clicking on this used to pull up a list of all the other computers and devices connected to the LAN...  :(

---

### Post by Morbius1 on 2017-08-05
> And I am having a remarkably difficult time accessing my Windows shares  - much more difficult than it should be - the only thing that's changed  was to disable SMBv1 on most of them due to WannaCry/other recent  threats.
Your file manager uses the samba client to access shares and by default it uses the SMB1 dialect to do that. If you disable SMB1 on the server you cannot make contact.

If you want to continue to use the file manager to do this edit /etc/samba/smb.conf, and add the following line under the "workgroup = WORKGROUP" line:
```
client max protocol = SMB3
```
Now the samba client will negotiate the dialect it will use with the server up to SMB3 instead of the default which is SMB1 ( called NT1 in Samba ).

This comes at a price however. You will lose the ability to "browse" for shares since that is also dependent on SMB1. You can still access the Windows shares but you will have to access it explicitly ... as in smb://server/share

---

### Post by oldsmobile_mike on 2017-08-08
> **Morbius1 said:**
> This comes at a price however. You will lose the ability to "browse" for shares since that is also dependent on SMB1. You can still access the Windows shares but you will have to access it explicitly ... as in smb://server/share

Perfect!  I made the change to the smb.conf file and am now able to browse shares on my devices that have SMB1 disabled using the path you suggested.  Thanks for your help!  :D

---

