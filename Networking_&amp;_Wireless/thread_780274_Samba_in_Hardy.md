---
title: "Samba in Hardy"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by dualityim on 2008-05-03
Since upgrading to Hardy, I've been having trouble with using it as both a client and server to in sharing files with my Windows machines, because the tools that were in Gutsy to configure Samba seems to have disappeared or relocated in Hardy, and I can't find any guides that show how to do it under Hardy. I hope someone could help me out or point me to a guide for Samba under Hardy. When I'm trying to use my Ubuntu machine as a samba server, I couldn't find the place to set the machine name and workgroup name for Windows shares, so on my Windows machine I can only access the Ubuntu machine using the machine's IP address. Under Gutsy, System -> Administration -> Shared Folders had these options, but I couldn't find it in Hardy. When I try to use my Ubuntu machine as a samba client, I can find my Windows machines in Network, but when I enter it I am not prompted to enter a user name and password, and so the machine does not display any of my shared folders on my Windows machines. When I try to use the "Connect to Server..." tool to find my Windows shares, I either get the "no program is registered to handle this location" error message or "the location is already mounted" error message. Even though I have the samba metapackage installed. Could anyone help me configure Hardy to function properly as a samba client and server? Thanks in advance.

---

### Post by Amorphous_Snake on 2008-05-03
I also wonder where the Shared Folders tool went?!!! I don't want to manually edit smb.conf just to change my workgroup. I tried to install the Fedora tool Samba-system-config but it just won't start.

I also can't see the Hardy Samba server on my Windows box without typing its IP address.

---

### Post by zmanian on 2008-05-03
You can launch the Shared Folders program from the command line 
..
shares-admin

I'm working through my samba issues with Hardy right now. I usually find that you need to start over with smb.conf with yever Ubuntu release..

---

### Post by jerryf70 on 2008-05-03
I haven't tried Samba server on Hardy yet, but can definitely confirm the problems with using "connect to server" entry.  This worked fine in 7.10 but doesn't want to know now.  As this particulat problem is a client issue, it can't be smb.conf, but I don't know what it is yet.

---

### Post by iswa on 2008-05-03
Shared folders is working for me - access the shared folders dialog by right-clicking on the folder in Nautilus and selecting 'Sharing Options'.
I have a script to manually mount the shares on our Windows network when I log in - its very simplistic but has lines like this:

```

sudo mount -t cifs "//<servername>" /media/smb/Backupshare -o username="<username>",password='<password>',iocharset=utf8,file_mode=0777,dir_mode=0777 -o setuids
```

Hope that helps.

---

### Post by Dr. C on 2008-05-04
I can confirm the problems in Hardy as a client with authenticated samba shares.. 

Hardy will not authenticate to an authenticated samba share on Gutsy (7.10) or on Windows XP, while Gutsy and XP can see each others authenticated shares no problem. 

Hardy can see the samba share only with the permission level of "Others" with no opportunity to authenticate. The problems started only after the upgrade to Hardy

So I am also at a loss on how to configure Hardy to authenticate on a Gutsy or XP samba share.

---

### Post by A$h X on 2008-05-04
Not sure if I have the same problems as everyone else but here goes:

I can see my windows machines in places > network, but clicking on them hangs the system for 10-15 secs and then says it doesn't know how to open "files" of that type. If I click on my windows machines again, then after 30-40 SECONDS the shared folder appears. Any action in the shared folder takes another 20 secs to complete. And to top it all off, I can only view files/folders, no write/delete access. 

How the hell did hardy manage to break windows folder sharing SO badly, when it worked perfectly (for me anyway) in gutsy?

BTW I'm pretty sure this thread is incorrectly titled, as SAMBA deals with allowing windows to share ubuntu folders, if you uninstalled samba you would still see your windows network in nautilus. I believe it must be a bug in nautilus itself.

---

### Post by nelson_777 on 2008-05-04
I am having similar problems, although nautilus will no longer view the contents of some folders on a windows network, due an 'invaid argument'.

---

### Post by chrism3568 on 2008-05-07
I've tried creating SMB shares via the admin, Nautilus, and within the SMB.CONF file. It appears to work but my Windows machines do not see the Ubuntu machine. This worked in 7.10 but when I upgraded to Hardy I lost all of my shares.

---

### Post by bartos on 2008-05-07
> **Amorphous_Snake said:**
> I also wonder where the Shared Folders tool went?!!! I don't want to manually edit smb.conf just to change my workgroup. I tried to install the Fedora tool Samba-system-config but it just won't start.

I also can't see the Hardy Samba server on my Windows box without typing its IP address.

If you are using Samba (Samba server config)from System/Administration Menu
The fix for this is 

```
sudo touch /etc/libuser.conf 
```

---

### Post by Amorphous_Snake on 2008-05-21
Thanks. But what does this fix do?

---

### Post by megamaced on 2008-05-21
Now that Shared Folders has gone from the Administration menu, much to my dismay, I've been using system-config-samba. It seems to work just as well:

```
sudo aptitude install system-config-samba
```

---

### Post by tomski on 2008-05-26
i got the same problem samba on hardy as a file server for a windows network
ever since the upgrade it has faailed to work & now no windows pc can see the shares!!!
i keep all my work on the fileserver & at the moment i have to use scp to access them???????
when i first upgraded to hardy i had this issue so i tried to start over but using webmin to create the smb.conf = this failed but listed all shares with the same settings as in gutsy
installed menus & ran update-menus & found shares admin here:  apps->debian->apps->system->shaes admin = this still listed all shares but alas no access from a windows box
ive tried to use the system-config-samba tool = this failed also but it listed all the shares with the correct details
this has failed
so i renamed my new smb.conf i created with webmin & copied over my old gutsy config & went through all the above steps but using webmin just to check the settings and guess what.....still no access????!!!!!!!

so i guess im gonna have to stick to using scp until this get's worked out i could try to reinstall samba but that would force me to re-install ubuntu-desktop & i dont wanna bork up anything else.

why do i have this pain in the **** with EVERY ubuntu upgrade or do the dev team expect us all to do a fresh install of every release!!!!

---

