---
title: "Windows Network"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by LAF4SENS on 2007-10-31
Hi,

I have 3 PC's on a small network at home.

1 PC is Ubuntu, the second is VISTA and the third is Windows XP.

The 2 Window box see each other on the network, no problem. I  installed UBUNTU (Gutsy) on my third PC. 

The problem is that I CAN'T SEE the 2 other PC's (Windows). I go Under NETWORK in Ubuntu and Click on "Windows Network", but nothing comes up, EMPTY. :-(

Can someone help?

Thanks for the answers,

Marc.

---

### Post by 505 on 2007-10-31
You can always access them by IP. Click places -> connect to server, and select windows share. You need to fill in server (IP address), name, and domain, the rest is optional.

I think you need smbmount for that, don't know it it is installed by defaut.

---

### Post by bsh on 2007-10-31
have you put Ubuntu into the same workgroup as the windows pc's?

---

### Post by LAF4SENS on 2007-10-31
I think so, duuuhhh.

I'm a newbie, so all of this is quite new to me.

How do I check to see If I really put ubuntu in the same workgroup?

Thanks,

Marc (Nuub)

---

### Post by ShogunMaster06 on 2007-10-31
Try going to System -> Administration -> Shared Folders.  If not already installed, Sharing Services (SMB/NFS) should prompt you to be installed.  You'll want Install Windows Network Support (SMB).

Once this is done, go to the General Properties tab and set your domain (MSHOME by default) and you can choose a user name you want to use to connect.

Now you should be able to follow 505's suggestion to mount the remote folders.  You can also choose folders on your Linux box to share with the other machines from the Shared Folders dialogue.

---

