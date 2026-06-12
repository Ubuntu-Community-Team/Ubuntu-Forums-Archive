---
title: "folder sharing oddness"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by deusxechelon on 2007-11-05
Well the issue is kind of big so I'll just go over it step by step:

I was trying to set up a shared folder to send files to my girlfriends Ubuntu Feisty box and I set the share under NFS Unix sharing, her computer did not see it but it saw the Samba shared folder I had set up for my windows boxes and was able to access it freely. Okay fine, any way you slice it if I can move files from point A to B I don't care what you call it....and it is easier to have everything in one folder.

Now for the real problem: My girlfriends computer can go in to this **SAMBA** folder without any ifs ands or buts but when a windows computer tries to access it,  I am prompted for a user-name and password. um.... why?

I was browsing forum threads and various ones mentioned its more secure to leave a user-name and password in place; so the way it seems to me is I am protected from the Microsoft haxers but Linux ones.. well, no biggie. :lolflag:

Lastly, why is it that I have to add a user for samba both in the System>Admin>Users and Groups AND do "sudo smbpasswd -a guest" (Same User-name in both locations) in order to get the windows computer to be able to log in?

---

