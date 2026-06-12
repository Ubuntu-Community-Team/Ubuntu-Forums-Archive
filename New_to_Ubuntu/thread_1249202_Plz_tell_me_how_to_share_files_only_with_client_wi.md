---
title: "Plz tell me how to share files only with client within virtualbox??"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by gackt on 2009-08-25
Hi guys I'm using virtual box with xp as the client and ubuntu 8.10 as the host. My question is how do i create a shared folder between this client and host only, so other people that connected trough the same network can not access the files. Thank you.

---

### Post by Ocxic on 2009-08-25
in the settings for the virtual machine there will be a place for shared folder, just add the folders you want to access in the guest, and in windows use the "map network drive" option to connect to the share, it should be listed there under vboxsvr. you will need to have the guest additions installed as well.

---

### Post by gackt on 2009-08-25
Thanks, Yes I did that. My question now is will other people (in the same LAN) able to see the shared folder as well?

---

### Post by Ocxic on 2009-08-25
No, the connection between the host and guest in completely internal; Now you would be able to share from the guest IF you set the adapter to bridged in the preferences for the virtual machine, and enabled file sharing on the guest.

But that is way to complicated a setup for sharing a folder considering you could just install samba and share right from your Linux host. (tip: check out webmin, very useful)

---

