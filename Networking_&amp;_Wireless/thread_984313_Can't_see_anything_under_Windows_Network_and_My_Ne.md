---
title: "Can't see anything under Windows Network and My Network Places"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by mvalviar on 2008-11-16
Hi,

This is my first post. I have have a windows xp box and an ubuntu 8.04 box on network. I want to be able to share files between them. I'm having alot of troubles. I already googled for guides and tested every single one I found but to no avail. I really can't figure out whats wrong. I can network games though. A game of Warcraft III hosted on the windows box can be joined by the ubuntu box. But games hosted on the ubuntu box can't be joined by the windows box. On the windows box I can see the the ubuntu box under MSHOME but when I try to browse it there is a pop up saying "You to not have access...Invalid parameters." shows. On my ubuntu box I can see MSHOME under Places>Network>windows network but I cant see milan (milan is the name of the windows box) under MSHOME. Yes I have Shared folders on both PC.

Thanks in advance for any help or suggestions.

---

### Post by Iowan on 2008-11-16
I presume you already loaded Samba-server on Ubuntu - are you connecting from Windows using an Ubuntu username? If so, is that user also a Samba user?

---

### Post by gregphil on 2008-11-16
You didn't say, but if your Windows share require authentication (if you don't allow 'guest' or anonymous logins) then the issue is a bug in the gnome GUI library that Ubuntu uses to attempt authorization of share listing.  If so, you can't fix it.  The bug appeared in Hardy and has not been fixed as of the Intrepid 8.10 release. It is reported many times but here are a couple:
[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072))
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)

The bug only effects browsing, not mounting, so if you know the full path to the share you can just type it in the file browser box like

smb:///     (to list domains or workgroups seen)
smb://Workgroup/    (use your actual workgroup to list computers seen)
smb://computer/ShareName   (to connect)

Good Luck, lets hope this gets declared important enought to fix sometime soon.

---

### Post by mvalviar on 2008-11-17
I'm really kinda lost with this. But the most frustrating part is that sometimes I can see and manipulate those shared files in the windows pc from my ubuntu pc. One time I wasn't able to access it it turns out that the windows firewall is on. I turned it off permanently and I thought everything will be fine and dandy. But when I logged on a few hour later to transfer some more files from the windows pc I can see those files again. My only goal was to transfer my files from windows to ubuntu to complete my switch rather than copying everything using usb. 

@Iowan
> **Iowan said:**
> I presume you already loaded Samba-server on Ubuntu - are you connecting from Windows using an Ubuntu username? If so, is that user also a Samba user?

Yes I have the samba server. I just browse "My Network Places" then "Workgroup Computers" I see Milan(windows) and mvalviar(ubuntu,samba)(my ubuntu box) when I click mvalviar theres the pop-up I mentioned its not asking form anything at all.

@gregphil

> **gregphil said:**
> You didn't say, but if your Windows share require authentication (if you don't allow 'guest' or anonymous logins) then the issue is a bug in the gnome GUI library that Ubuntu uses to attempt authorization of share listing.  If so, you can't fix it.  The bug appeared in Hardy and has not been fixed as of the Intrepid 8.10 release. It is reported many times but here are a couple:
[https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072))
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/209520)

The bug only effects browsing, not mounting, so if you know the full path to the share you can just type it in the file browser box like

smb:///     (to list domains or workgroups seen)
smb://Workgroup/    (use your actual workgroup to list computers seen)
smb://computer/ShareName   (to connect)

Good Luck, lets hope this gets declared important enought to fix sometime soon.

No, my windows share doesn't require authentication. I tried the methods you mentioned before. "smb:///" shows the workgroups correctly i.e MSHOME. "smb://mshome" shows nothing. "smb://mshome/milan" results in failed to mount windows share. Please select another view and try again.

Thank you for your replies. I really hope I can fix this. I'm trying to convince my friends to switch to ubuntu but difficulties like this won't be any help. Seeing me all frustrated with matters like this only tells them otherwise.

---

