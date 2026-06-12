---
title: "How Can I Configure SAMBA Similar To Windows Workgroup Server"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Vince4Amy on 2008-11-28
I have a small Windows Workgroup at my home which consists of only 4 computers. This computer which dual boots Vista & Ubuntu is the main computer in my Workgroup which contains:

Shared Files/Folders
Shared Printer

Can I configure SAMBA in such a way that all of the paths and names will be the same, so regardless of being in Ubuntu or Windows I can have my Windows shares still showing on the other 4 machines with the shortcuts on them working properly.

I would also like to know if this is the same for the printer. 

My Hostname is the same on both Windows and Ubuntu.

---

### Post by cmnorton on 2008-11-30
Is Windows going to let you have duplicate host names? That does not seem like it's going to work. 

I am a little confused as to what you want to do. Basically, if you are sharing out (with Samba) /global_samba_share, you should be able to configure all users to access this from Windows. Make sure you use smbpasswd to set them up.

---

