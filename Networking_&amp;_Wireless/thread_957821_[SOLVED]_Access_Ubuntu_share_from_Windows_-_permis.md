---
title: "[SOLVED] Access Ubuntu share from Windows - permission message"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by 5circles on 2008-10-24
I created a folder on the Ubuntu machine that I want to share.  I right clicked and chose 'sharing options' and shared the folder.  (the app told me that the sharename was too long, even once I shortened it, but it went ahead).

Now I can see the share from a Windows machine.  I can see and read files in the share folder. But regardless of whether I try directly, or map a drive, I can't create files or write to existing files.  I get the following kind of message [COLOR="Blue"]'you need permission to continue this action'[/COLOR]

Sorry for creating yet another thread, but every time I build a system it seems that the situation is different and there is never a definitive set of steps to go through to get Windows & Ubuntu network interoperability.

Thanks
Mike

---

### Post by sea_monkey987 on 2008-10-24
make sure the shared folder has 777 permissions.  go into the properties of the folder that you're sharing, go into the permissions tab.  then, make sure you've selected "create and delete files" for all owner, group, and others.

---

### Post by 5circles on 2008-10-24
This makes sense on one level.  I found that the permissions were only set for owner  to create and write, so I changed them.

At another level, I wonder why the permissions should be changed if I'm accessing as the same username and password.

And third - it doesn't work.  I got the same error message after changing permissions.  I restarted Windows just in case.  And I also turned off the share in Ubuntu and turned it back on - in case the share was related to the permissions at the time the share was created.

---

### Post by sea_monkey987 on 2008-10-26
ok.  then something else is going on.  bear with me while I try to figure out your scenario.  So you're sharing a folder on your Ubuntu box (we'll call it "Public").  when you go to "\\UBUNTUCOMPUTER\Public" from windows explorer, you can read all the files inside "Public."  However, you can not write to any of the files in "Public" or create any new files.  is this correct?

also, when you go to "\\UBUNTUCOMPUTER\Public" from XP, are you putting in a username and password?

---

### Post by sea_monkey987 on 2008-10-26
i'm thinking you logging on as guest onto the share from your XP box.  please post the output of

```
cat /etc/samba/smb.conf | grep guest
```
and
```
cat /var/lib/samba/usershares/**Public**
```
where **Public** is the name of the share as seen from the XP box

---

### Post by 5circles on 2008-10-26
I'm not sure what I was doing earlier, and what's changed, but I seem to have it solved now.  I got to the point of wondering if I could replicate some of the settings from another Ubuntu box running 7.04 that was working for shares.  Then I changed permissions for some new shares.

```
cat /etc/samba/smb.conf | grep guest
;   guest account = nobody
map to guest = bad user
   usershare allow guests = yes
;   guest ok = yes
;   guest ok = no
   guest ok = no
   guest ok = no
;   guest ok = yes 
```

```
cat /var/lib/samba/usershares/lan_backup
#VERSION 2
path=/lan_backup
comment=
usershare_acl=S-1-1-0:F
guest_ok=n
```

Sorry for the confusion, thanks for the help!

---

