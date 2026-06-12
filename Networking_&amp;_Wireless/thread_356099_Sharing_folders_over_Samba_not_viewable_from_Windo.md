---
title: "Sharing folders over Samba not viewable from Windows"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Endolith on 2007-02-08
I've figured out how to share folders on Windows network using System --> Administration --> Shared Folders.   Although I can see the computer from Windows, I get a login prompt if I try to access it.  The same thing happens in Linux; it says "Authentication required" and "you must log in to access".  Nothing I try for a login works, though.

---

### Post by Endolith on 2007-02-08
Do I have to set permissions somewhere to get this to work?  I don't see an option to do this under Shared Folders.

---

### Post by Matt Yun on 2007-02-08
You actually need to create a user account on your Linux host to match your Windows user.  eg. if your Windows username is 'endolith' then on your Linux host do:  sudo adduser endolith

Also, you need to run 'smbpasswd -a endolith' to add the user to the samba user list.

Finally, you need to open ports 137, 138 and 139 for tcp traffic in your iptables firewall rules.

---

### Post by Indigo7 on 2007-02-08
You just saved thin newbie SOOO much time!

Thanks!

---

### Post by Endolith on 2007-02-08
> **Matt Yun said:**
> Also, you need to run 'smbpasswd -a endolith' to add the user to the samba user list.

This is all I needed to do

> Finally, you need to open ports 137, 138 and 139 for tcp traffic in your iptables firewall rules.

Why does mine work if I haven't done this?

---

### Post by gradedcheese on 2007-02-08
> 
Why does mine work if I haven't done this?


I suspect that when you used the Shared Folders utility, it opened the ports for you.

Someone needs to add some features to the Shared Folders utility, perhaps a tie-in to adding users (and smbusers!) so that things just work.

---

### Post by Endolith on 2007-02-10
> **gradedcheese said:**
> Someone needs to add some features to the Shared Folders utility, perhaps a tie-in to adding users (and smbusers!) so that things just work.

Agreed.  Where would we even file this feature request?

---

### Post by Endolith on 2007-02-10
Problem:

I can't modify the files.

---

### Post by miceagol on 2007-02-11
What if there's no user name in Windows?

---

