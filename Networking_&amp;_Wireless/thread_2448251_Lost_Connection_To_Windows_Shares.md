---
title: "Lost Connection To Windows Shares"
date: 2020-08-04
forum: Networking &amp; Wireless
---

### Post by jdhamric on 2020-08-04
A few weeks ago I upgraded to Ubuntu 20.04 & had no problem connecting to my Windows desktop which has network shares. A few days ago I suddenly lost the connection. Samba is running, however the nmbd service does not load. I have removed & re-installed samba with no effect. Interestingly I can access the drive attached to the USB port of my router. I have attached my fstab & smb.conf files for inspection. But really nothing was changed.

Hoping someone can help!

---

### Post by Morbius1 on 2020-08-06
> //192.168.1.2/Data  /home/jeff/Barsoom_Data  cifs  auto,user,rw,vers=3.0,cache=loose,x-systemd.automount,username=xxx,password=xxx,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0

What to do is dependent on your answer to the following question:

After you first log in and the share above is not mounted does it mount when you issue the following command:
```
sudo mount -a
```

If it does you have two options:

[1] You can leave the mount point at  /home/jeff/Barsoom_Data but remove **x-systemd.automount** which isn't really doing anything in this case. You will also need to make auto noauto:
> //192.168.1.2/Data  /home/jeff/Barsoom_Data  cifs [COLOR=#ff0000]**noauto**[/COLOR],user,rw,vers=3.0,cache=loose,username=xxx,password=xxx,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777   0  0
Then it will mount only when you access the link on the side panel of your file manager.

[2] Or, you can change your mount point to something other than your home directory or under /media, change auto to noauto:
> //192.168.1.2/Data  [COLOR=#ff0000]**/mnt/Barsoom_Data**[/COLOR]  cifs   [COLOR=#ff0000]**noauto**[/COLOR],user,rw,vers=3.0,cache=loose,x-systemd.automount,username=xxx,password=xxx,uid=1000,iocharset=utf8,file_mode=0777,dir_mode=0777   0  0
Then reinitialize systemd:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

The it will mount when /mnt/Barsoom_Data is accessed by you or any other process - it is seamless.

Side note: The issue you have with smb.conf and certain samba services not running is another topic since a cifs mount doesn't use samba, smb.conf, etc ....

---

### Post by jdhamric on 2020-08-06
Thanks for responding Morbius1.

The first thing I tried when I noticed the problem was ```
sudo mount -a
``` which returns:

Couldn't chdir to /home/jeff/Barsoom_Data: No such device
Couldn't chdir to /home/jeff/Barsoom_Media: No such device
Couldn't chdir to /home/jeff/Barsoom_Media2: No such device

"Media" & "Media2" show up in "home" (locked); "Data" does not. A right click on those folders in the left panel shows "Unmount". Clicking on them displays a "This location could not be displayed" message & "Error opening directory...No such device".

I have the "auto" option set in fstab to mount the shares on log-on since I often access those shares & I have my own cloud to sync files/folders. I have always had that option. Removing **x-systemd.automount **I guess wouldn't hurt: I've tried it before & the only thing I can remember happening is that the shares didn't show up in the Nautilus panel (?). Although I can't remember where I saw that it could be added or for what.

I tried your Option 2. When I input ```
sudo systemctl restart remote-fs.target
``` I get the message "A dependency job for remote-fs.target failed. See 'journalctl -xe' for details." Trying to open the directories results in the same error messages.

In addition (as if this isn't enough!), I can no longer connect to a wireless printer. 

Any help is greatly appreciated.

---

### Post by Morbius1 on 2020-08-06
Are you sure 192.168.1.2 is still the ip address of the Windows server?

---

### Post by jdhamric on 2020-08-07
> **Morbius1 said:**
> Are you sure 192.168.1.2 is still the ip address of the Windows server?

Yes, but double-checked to make sure! I can also connect to the Windows box through my tablet & I have DLNA server on it that I can connect through. So I know there is something not right between my Ubuntu laptop & my Windows server.

On a positive note, I can go to "Other Locations" in Nautilus, click on my Windows server name and see all my shares & they will mount when clicked. But they don't show up in the left panel of Nautilus initially. I'm still confused why the "auto" option in fstab doesn't work; isn't it supposed to automount the shares? Would adding "_netdev" help? Per your suggestion, I can remove  **x-systemd.automount**, but IIRC I had a problem with the shares showing up in Nautilus which was why I added it. However, after the changes I can now connect to my wireless printer! A definite plus! I cannot connect to a print attached to my Windows box, though.

I appreciate all your help & hope you can assist in clearing up these remaining issues.

---

### Post by Morbius1 on 2020-08-07
There was no reason to use option [1] or option [2] since you failed the original test:
> After you first log in and the share above is not mounted does it mount when you issue the following command:```
sudo mount -a 

```If it does you have two options:
You instead got errors:
>  Couldn't chdir to /home/jeff/Barsoom_Data: No such device
You will get that error if the mount point doesn't exist.

You would get a different error if the ip address doesn't exist.

Don't know what to tell ya.

Mount it manually:

Create a mount point under /mnt:
```
sudo mkdir /mnt/Test
```
then mount it in a terminal:
```
sudo mount -t cifs //192.168.1.2/Data /mnt/Test -o username=xxx,password=xxx,uid=1000,vers=3.0                      
```
*THe vers=3.0 is redundant but shouldn't interfere with anything.*

---

### Post by jdhamric on 2020-08-07
Morbius1--

I tried your suggestion and it worked to an extent. I  could access "Data" and it showed mounted as "Test". But it did not show  up in Nautilus in the left panel as automounted.

I surmised that  maybe something was up with Nautilus, so I purged it & reinstalled.  I also remembered I disabled Tracker per instructions at [https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html.]("https://www.linuxuprising.com/2019/07/how-to-completely-disable-tracker.html")  It was constantly running the HDD and slowing things down severely at  times. Re-reading that article implies there are some deep connections  to Nautilus. May be it had something to do with my problem? 

All I  know is that after doing those 2 things & restoring my files to  their original state everything is working again. So I guess I can mark  this as "Solved".

Thanks for all your help!

---

