---
title: "Ubuntu to Ubuntu file sharing in a home network."
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by onestep on 2007-10-24
In my home network I have a Ubuntu box running Samba to share a folder with 2 Windows machines.
Last night I converted one of those 2 Windows machines over to Gutsy!. How do I access the shared folder from it?

---

### Post by onestep on 2007-10-25
On the new Gutsy machine under "Places" / "Network" I can see the Shared Folder on my Ubuntu Box that's running Samba, but I can't access it. 

Any idea's what I need to do to access the shared folder? The new Gutsy machine is my son's. I "upgraded" him from Windows XP to Ubuntu Gutsy! If he can't access the shared media thats on my Ubuntu box I know he'll want XP back!

---

### Post by b0bby on 2007-10-25
'smbfs'

sudo apt-get install smbfs

then use 'mount -t smbfs -o username=name,password=password //machinename/sharename /mnt/smbshare'

---

### Post by onestep on 2007-10-25
> **b0bby said:**
>  'mount -t smbfs -o username=name,password=password //machinename/sharename /mnt/smbshare'

Thank you bObby for your response. Will doing this create a mounted folder on my son's Gutsy box which allows him access to it's contents, or will this allow him to click on "Places / Network / ... shared folder" to access the shared folder on my Ubuntu box?

sorry for the nOOb questions... but I is one!

---

### Post by conjur3r on 2007-10-25
It will mount the share drive into a folder under /mnt.  Instead of this, mount it under /media/smbshare so that an icon will automatically appear on the desktop.  Makes life alot easier.

If you want to test the samba connection before mounting it, open up your file browser and in the location type:

smb://username@server/share

---

### Post by onestep on 2007-10-25
Thank you bObby & conjur3r. 
When I get home this evening I will follow your suggestions!

Question - Just curious, why can I navigate to the shared folder via "Places - Network - workgroup - machine - shared folder" but not access it?
Should it be accessible, or is this just a way to see-only what folders are being shared on the network?

---

### Post by onestep on 2007-10-25
Just wanted to say thanks! 
I can now access the shared folder in my Ubuntu box from the Gutsy box!

In addition, I did some googling and found the following that allows the share to be  automatically mounted when Gutsy boots up;

[COLOR=#ff0000]//*servername*/*sharename* /*mountdirectory* smbfs username=*windowsuserename*,password=*windowspassword* 0 0

woohooooooooooo!!
[/COLOR]

---

### Post by conjur3r on 2007-10-26
> **onestep said:**
> Thank you bObby & conjur3r. 
Question - Just curious, why can I navigate to the shared folder via "Places - Network - workgroup - machine - shared folder" but not access it?
Should it be accessible, or is this just a way to see-only what folders are being shared on the network?

You probably set up the share requiring users to login before being able to access it.  When this happens, a popup window comes up asking for your username/password and I think domain.  Don't worry, this is common for shares needing authentication.  You can also create public shares which do not require authentication (it's up to you when you want to do this).

Glad it's all working out for you!

---

