---
title: "file sharing permissions between Mac and Ubuntu"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by clayton3 on 2014-02-05
I set up a ubuntu desktop to run with a Plex media server. However, I want to access the ubuntu directory from my mac. The idea is that I have media I acquire on my mac that I then want to move to the ubuntu machine. So, mac --> ubuntu --> plex. I followed this guys mostly [GUI sharing]("http://ubuntuforums.org/showthread.php?t=1685718") set-up using samba. I see from another post that I can [use NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") instead. Since I want this to be a one-and-done connection I could use the NFS set-up, but honestly, it runs to multiple pages and I'm looking for the easy way out.

I had success with the GUI samba installation. I mounted the ubuntu directory onto the mac, I could read the files, but I couldn't add new files, I didn't have permission. When I mounted the directory I connected as the "sharer" user(as described in the previously linked instructions). That worked great until I tried to move a file into the shared directory, Mac's Finder then asked for username and password. I tried both my mac username and password and the sharer username and password. Neither worked.

I see four possible options going forward:
1. Set-up the shared directory to share as guest, less secure, but my wifi is secure and i don't think my girlfriend is trying to hack me...
2. Suck it up and do the NFS file sharing method.
3. Figure out the permissions required to use the samba user "sharer."
4. Use a different method to move files(Dropbox local(I've heard there's such a thing, FTP, other)

Suggestions?

---

### Post by Morbius1 on 2014-02-05
> I had success with the GUI samba installation. I mounted the ubuntu  directory onto the mac, I could read the files, but I couldn't add new  files, I didn't have permission. When I mounted the directory I  connected as the "sharer" user(as described in the previously linked  instructions). That worked great until I tried to move a file into the  shared directory, Mac's Finder then asked for username and password. I  tried both my mac username and password and the sharer username and  password. Neither worked.
If you want to pursue the samba part of this you need to post how all of this is set up. Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by clayton3 on 2014-02-05
testparm results in ```
[FONT=arial]oad smb config files from /etc/samba/smb.conf[/FONT]
[FONT=arial]rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)[/FONT]
[FONT=arial]Processing section "[printers]"[/FONT]
[FONT=arial]Processing section "[print$]"[/FONT]
[FONT=arial]Loaded services file OK.[/FONT]
[FONT=arial]Server role: ROLE_STANDALONE[/FONT]
[FONT=arial][global][/FONT]
[FONT=arial]    server string = %h server (Samba, Ubuntu)[/FONT]
[FONT=arial]    map to guest = Bad User[/FONT]
[FONT=arial]    obey pam restrictions = Yes[/FONT]
[FONT=arial]    pam password change = Yes[/FONT]
[FONT=arial]    passwd program = /usr/bin/passwd %u[/FONT]
[FONT=arial]    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\[/FONT][FONT=arial]ssuccessfully* .[/FONT]
[FONT=arial]    unix password sync = Yes[/FONT]
[FONT=arial]    syslog = 0[/FONT]
[FONT=arial]    log file = /var/log/samba/log.%m[/FONT]
[FONT=arial]    max log size = 1000[/FONT]
[FONT=arial]    dns proxy = No[/FONT]
[FONT=arial]    usershare allow guests = Yes[/FONT]
[FONT=arial]    panic action = /usr/share/samba/panic-action %d[/FONT]
[FONT=arial]    idmap config * : backend = tdb[/FONT]

[FONT=arial][printers][/FONT]
[FONT=arial]    comment = All Printers[/FONT]
[FONT=arial]    path = /var/spool/samba[/FONT]
[FONT=arial]    create mask = 0700[/FONT]
[FONT=arial]    printable = Yes[/FONT]
[FONT=arial]    print ok = Yes[/FONT]
[FONT=arial]    browseable = No[/FONT]

[FONT=arial][print$][/FONT]
[FONT=arial]    comment = Printer Drivers[/FONT]
[FONT=arial]    path = /var/lib/samba/printers[/FONT]

```

and net usershare
```
[FONT=arial]path=/home/clayton/Videos[/FONT]
[FONT=arial]comment=[/FONT]
[FONT=arial]usershare_acl=Everyone:F,[/FONT]
[FONT=arial]guest_ok=n[/FONT]
```

---

### Post by Morbius1 on 2014-02-05
The question is does "sharer" have write access to the Video folder and all it's contents.

Since "sharer" has been granted access to the share Samba has done it's part so the rest is up to Linux permissions. Run the following command:
```
ls -al /home/clayton/Videos
```
Does anyone other than "clayton" have write access to the Video Folder and everything in it?

Of course if you've encrypted your home folder you have other issues.

---

### Post by clayton3 on 2014-02-05
I'm not really sure why there's a .DS_store file listed. And I'm not sure how to read the rest of it.

```
t[FONT=arial]otal 36[/FONT]
[FONT=arial]drwxrwxrwx  4 clayton clayton  4096 Feb  5 06:39 .[/FONT]
[FONT=arial]drwxr-xr-x 27 clayton clayton  4096 Feb  5 06:46 ..[/FONT]
[FONT=arial]-rwxr--r--  1 sharer  sharer   4096 Feb  5 06:39 ._.DS_Store[/FONT]
[FONT=arial]-rwxr--r--  1 sharer  sharer  15364 Feb  5 06:47 .DS_Store[/FONT]
[FONT=arial]drwxr-xr-x 34 clayton clayton  4096 Jan 31 17:07 Movies[/FONT]
[FONT=arial]drwxrwxr-x 14 clayton clayton  4096 Feb  4 20:35 Tv-Shows[/FONT]

```

---

### Post by Morbius1 on 2014-02-05
The .DS_whatevers is an OSX thing. The problem seems to be that "sharer" has write access to /home/clayton/Videos itself but only "clayton" has write access to the [FONT=arial]Movies[/FONT]
[FONT=arial]and Tv-Shows[/FONT] subfolders.

Unless you want to keep changing permissions on everything you might consider adding a line to smb.conf so everything is saved with clayton as owner. If you want to do that:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
Then add the following line under the "workgroup = workgroup" line:
```
force user = clayton
```
Save the file then restart samba:
```
sudo service smbd restart
```

Samba will limit access to those who have been added to the samba password database ( smbpasswd ) but once they are in they will be converted to clayton. So when samba allows sharer access to the share he becomes clayton and everything that clayon has access to so does sharer. And everytime sharer saves something to the share it will save with clayton as owner so he can access it on the server locally.

---

### Post by clayton3 on 2014-02-05
Morbius, that worked! Thanks. Should I have any security concerns with forcing the clayton user? I guess it's more secure than opening to guest users. Do you know about throughput speeds? I read that NFS might be faster than smb. I understand of course it has a lot to do with the router, just wondering if you had an opinion.  I'm getting a speed somewhere around 3MB/sec using an asus N66. Thanks again.

---

### Post by Morbius1 on 2014-02-05
As far as the security concern the "force user" isn't giving access to the credentialed samba client to your entire system only to your samba share. 

As far as speed is concered there is on ongoing debate on what protocol is faster which I can't comment on. I haven't used NFS in decades and it was set up by someone else for me so I have no way to judge which is faster, more reliable, or more secure.

---

