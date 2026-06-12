---
title: "Samba only works if share name is different to folder name"
date: 2021-10-19
forum: Networking &amp; Wireless
---

### Post by misc-daminator on 2021-10-19
I have just replaced my home server with a new machine.

Most things have gone well.

Samba is behaving strangely. No matter what I do, I can't get read/write access UNLESS I make the samba share name, and the folder name, different.

If the names are the same, I can read only. If they are different, all works perfectly.

I have seen this mentioned online, but can only find reference to it from years ago.

My previous server had names like [Share1] and folders like /Share1 working fine. But this won't work with the new server.

As soon as I make it [Share1x], or change the name in any way, then everything works fine!

Obviously, I can just change the names of all of my shares, but what's going on here?

---

### Post by Morbius1 on 2021-10-19
To be honest at first read I suspected some kind of high altitude sickness or possible illegal drug use as the cause since every single one of my shares have labels that match the name of the directory being shared and I do not have this problem. 

But then I saw this: [https://askubuntu.com/questions/724916/can-read-but-cannot-write-to-samba-share](https://askubuntu.com/questions/724916/can-read-but-cannot-write-to-samba-share)

I have no idea.

Um ... when you say server do you mean Ubuntu Server without a desktop? Or do you mean Ubuntu desktop used as a server? The reason I ask is because for the desktop system there are two ways to create a samba share: The "classic" share defined in smb.conf and the share you can create through Nautilus - a samba "usershare".

Run this command to list your shares
```
testparm -s
```
Then this one to see if you have any usershares:
```
net usershare info --long
```

Do you have shares with the same name listed in both places?

---

### Post by misc-daminator on 2021-10-19
Hi [[COLOR=#000000]Morbius1[/COLOR]]("https://ubuntuforums.org/member.php?u=982144"),

Yes, I've found those links, and a couple of rabbit hole branches off of  them. But they are very old, so I can't believe that the issue would  still exist.

However, I think you may be onto the answer!

My previous 'server', with network shares that worked fine, was a Xubuntu instal.
My new 'server' is a standard Ubuntu (desktop) instal.

The two commands that you listed do indeed suggest that things are being duplicated.

[HTML]
-$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    workgroup = SHARE
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


[share1]
    comment = share1 on Server
    create mask = 0660
    directory mask = 0770
    path = /share1
    read only = No
    valid users = @share

[share2-diff]
    comment = share2 on Server
    create mask = 0660
    directory mask = 0770
    path = /share2
    read only = No
    valid users = @share

[share3]
    path = /share3
    read only = No
    valid users = share david


[share4-diff]
    path = /share4
    read only = No
    valid users = share david
[/HTML]

And

[HTML]~$ net usershare info --long
[share2]
path=/share2
comment=
usershare_acl=Everyone:R,Unix User\root:F,
guest_ok=n

[share4]
path=/share4
comment=
usershare_acl=Everyone:R,Unix User\root:F,
guest_ok=n

[share3]
path=/share3
comment=
usershare_acl=Everyone:R,Unix User\root:F,
guest_ok=n

[share1]
path=/share1
comment=
usershare_acl=Everyone:R,Unix User\root:F,
guest_ok=n
[/HTML][COLOR=#000000]

So, I guess the next step is to get rid of those 'usershare' shares.

How can I do that?

If I open [/COLOR]Nautilus, find one of the folders and right click on it, it looks like it's not being shared.

I don't remember trying to set up shares in any way other than via smb.conf, but I'm quite prepared to believe that I did. :smile: I tend to go the GUI route if I can (which is why I'm running desktop Ubuntu on my server).

Thanks again for the smart remote detective work, Morbius1. Hopefully we're on the right track.

*PS I know that the blocks above are not HTML, but they wouldn't display correctly when I selected CODE tags.*

---

### Post by Morbius1 on 2021-10-20
Samba creates usershares definitions by creating a file with the name of the share in **/var/lib/samba/usershares** . You can just delete the files.

Rerun "**net usershare info --long**" again to confirm that samba thinks they are gone.

And restart smbd:
```
 sudo service smbd restart
```

---

### Post by misc-daminator on 2021-10-20
I had high hopes for this, Morbius1. But, it hasn't worked. :-(

I've removed the lines from "var/lib/samba/usershares".
Checked that they are gone with "net usershare info --long".
Ran "sudo service smbd restart".
I even shut down and restarted the server.

It's still exactly the same.

The shares with the same name as the share folders are read only.

The ones where I've made a slight change to the share name work fine.

I don't even have to leave ubuntu to test this.

I can open up Nautilus, and rather than going to one of the folders, I go to 'Other Locations' and then 'Server'.

Selecting one of the shares, and logging on as the appropriate user  (share) results in the exact same behaviour. The shares with the same  name as the share folders are read only. The ones where I've made a  slight change to the share name work fine.

"net usershare info --long" still returns nothing, so the usershares haven't come back.

What can it be???

---

### Post by misc-daminator on 2021-10-22
Anyone?

---

### Post by misc-daminator on 2021-10-27
I gave up in the end.
Wasn't comfortable that something wasn't set up correctly, so I formatted and reinstalled Ubuntu from scratch.
This time, I set up samba first, and everything worked flawlessly straight away.
Still no idea what the problem was, but all is fine now.

---

