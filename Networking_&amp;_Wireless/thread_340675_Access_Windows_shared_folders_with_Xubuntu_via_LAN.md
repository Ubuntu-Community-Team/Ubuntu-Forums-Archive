---
title: "Access Windows shared folders with Xubuntu via LAN"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by twiggy_trippit on 2007-01-17
Hello!

I have very recently installed Xubuntu on my computer. I am completely new to Linux. While I'm moderately computer litterate, networking has always been one of my weak areas when it comes to computers, so please assume that I'm a complete ignorant in that area.

I am connected to a local area network and I would like to access the shared folders on my roommate's computer which is running Windows XP. Unfortunately, Xubuntu appears to be less user-friendly than Ubuntu in that regard (there is no Places -> Network tab, among other things).

I have spent the last few hours trying to find how to do this, but I feel like I've been running circles. Could someone please give me a complete explanation on how to set this up from a fresh install?

Thanks.

Note: I currently have access to the LAN; Internet works great and I can also ping my roomie's comp. I couldn't come anywhere close to browsing the files on his computer, though.

---

### Post by Garyu on 2007-01-17
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

This will help you somewhat, at least for mounting windows shares so they appear in your filesystem.

I did a quick search of the forum and some ppl suggested to install the ubuntu-desktop in order to get those samba-tools which appear to be easier to work with.

---

### Post by dann0 on 2007-01-17
You can use Samba to define network shares from your machine,
and SMBFS to mount shares from the LAN.

Simply use the terminal to install SMBFS:
**sudo apt-get install smbfs**

Create a folder like /home/public
**sudo mkdir /home/public**

And mount the share:
**sudo mount -t smbfs //IP_to_computer2/share /home/public -o username=ABC,password=123,uid=ABC,gid=ABC**

Username and password, are what you have on computer2.
uid, and gid are your UserID and GroupID at your Ubuntu-box.

See
[b]man samba
man mount[/b]

Good luck, and don't fear the terminal.

---

### Post by twiggy_trippit on 2007-01-17
Thanks a lot! It's working now.

---

