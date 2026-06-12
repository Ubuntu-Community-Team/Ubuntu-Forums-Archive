---
title: "[SOLVED] can't view contents of ubuntu shares from ubuntu"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-02-16
Here is what happens when I try to view files inside  ubuntu shares through the Network Servers icon: "The folder contents could not be displayed."Video" couldn't be found. Perhaps it has recently been deleted.

I can see and access all shares properly on my xp box, and they are all physically located on a 300gb slave drive on ubuntu. I can access them from the locally mounted drive as well. I can also view the contents and files of the shares from all other computers on the network. This just started happening, and I can't find any reference to it anywhere. I have just done my 2nd meticulous re-install, no happiness. Have tried mounting shares from the main hdd as well, same results. It will occasionally tell me to sign on as guest, then I get 
"The folder contents could not be displayed.

Shares appear almost immediately on the xp box, but not on ubuntu via Network Servers>My Computer Name>Sharename, and also don't go away very quickly when un-shared.

Can someone please help? [edit] This is what happens when you correctly give windows permissions but not yourself on Ubuntu. I am currently thinking of a unique way to commit suicide.......

---

### Post by Fevrin on 2008-06-13
Can you please clarify which permissions you adjusted and where they can be found?  I'm having a similar issue, where my two Ubuntu computers (one's 7.04 and the main one is 8.04) cannot access shared files.  The shared folders show up just fine, but when I click on them, I get the "<foldername> couldn't be found.  Perhaps it has recently been deleted" message.  The permissions of the shared folders, however, allow "Others" to view them; I'm not sure which other permissions I'm overlooking.  Any help on this issue would be appreciated.  Thanks :)

---

### Post by mandrill on 2008-06-14
> **Fevrin said:**
> Can you please clarify which permissions you adjusted and where they can be found?  I'm having a similar issue, where my two Ubuntu computers (one's 7.04 and the main one is 8.04) cannot access shared files.  The shared folders show up just fine, but when I click on them, I get the "<foldername> couldn't be found.  Perhaps it has recently been deleted" message.  The permissions of the shared folders, however, allow "Others" to view them; I'm not sure which other permissions I'm overlooking.  Any help on this issue would be appreciated.  Thanks :)

What I wound up doing was installing the samba package from add/remove (NOT gsambad, or whatever) which very easily and quickly allows you to create a samba user account for yourself (gotta have it) and configure your shares.

Keepin' it real.......good luck, it should work!

---

