---
title: "Can't broswe Windows Shares from Ubuntu"
date: 2021-02-17
forum: Networking &amp; Wireless
---

### Post by ajuk2005 on 2021-02-17
Hi

I'm running Ubuntu 20.04.2 LTS

I can connect to a Windows server to display the shares, but I cant browse any of them. It says:
[B]Unable to access locations: Failed to mount Windows share: Invalid argument.
[/B]
From researching it, I've made lots of tweaks to /etc/samba/smb.conf - I've lost track of all the changes. I wish I made a backup of the original file so I could start again, but below is a paste of the exact contents right now.

[https://pastebin.com/mn6ce2QM](https://pastebin.com/mn6ce2QM)

Thanks for helping!

---

### Post by Morbius1 on 2021-02-17
For one: You don't want the following line in smb.conf:
> client max protocol = NT1
That tells the samba client that the highest smb dialect to use when it connects to a server is SMB1 ( samba calls it NT1 ). WIn10 disables SMB1 on the server side so it returns an "invalid argument". Remove the line in smb.conf and reboot your Ubuntu box.

For two: There is a bug in gvfs that forces the client to use SMB1 anyway.

You have three options:

[1] You can disregard Microsofts warnings about SMB1 and enable it there.

[2] You can bypass the gvfs bug and explicitly ask for the server and its share in **Connect to Server** in Nautilus. Something like:
```
smb://win10-host-name.local/share-name
```
[I]Remember, Win10 is now mDNS literate so you can access the machine with its mDNS hostname: hostname with a .local at the end.

[/I][3] Access the server with a mount.cifs mount which you would have to set up in fstab.

---

### Post by ajuk2005 on 2021-02-17
Thank you for the detailed response. This worked for me. I can now browse and open Windows shares.

---

