---
title: "Can't Connect to Shared Folder in Files"
date: 2021-07-30
forum: Networking &amp; Wireless
---

### Post by geeky-1 on 2021-07-30
I shared a folder on an Ubuntu computer by right clicking the folder in Files and selecting "Local Network Share" then clicking "Share this folder". From another Ubuntu computer, in Files, I clicked "+Other Locations", opened the computer with the shared folder, then opened the shared folder (which shows the network underscore). I clicked on "Connect As Registered User", entered my Password for the computer with shred folder and pressed Connect, but the Connect dialog just keeps popping up without connecting. What am I doing wrong? Do I need to install Samba on the computer I'm trying to connect from?

---

### Post by geeky-1 on 2021-07-30
I also tried installing nautilus-share, but that didn't make a difference. [https://www.devmanuals.net/install/ubuntu/ubuntu-20-04-focal-fossa/installing-nautilus-share-on-ubuntu20-04.html](https://www.devmanuals.net/install/ubuntu/ubuntu-20-04-focal-fossa/installing-nautilus-share-on-ubuntu20-04.html)

---

### Post by Morbius1 on 2021-07-30
Samba maintains it's own database of users and passwords used for samba purposes.

If you created the share on the server as userxyz and you want to connect to that share as that server user you need to add that user to the database on the server with this command:
```
sudo smbpasswd -a userxyz
```

---

### Post by geeky-1 on 2021-07-31
Thanks Morbius1 - that worked.

So when you use Nautilus file sharing, it uses Samba, which restricts filenames to Windows format and causes problems copying files Linux to Linux which aren't Windows legal. Is there any other way to copy folders/files via GUI drag and drop?

---

