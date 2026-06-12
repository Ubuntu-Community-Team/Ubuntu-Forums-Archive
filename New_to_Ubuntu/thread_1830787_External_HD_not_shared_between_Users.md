---
title: "External HD not shared between Users?"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-08-22
I discovered today that my external HD isn't being shared when I switch between users, even after logging out of the first one. I'd thought that the assignment of the HD as the permissions property of a given user would end, once that user had logged out. Instead, it seems that assignment to just one user endures beyond the logged in session, until the machine is restarted. Is there any way to change that, so (only) sequentially logged in user profiles will each gain access to the external HD?

---

### Post by seawolf167 on 2011-08-22
[LIST]
[*]Do you have an entry in /etc/fstab for the external drive in question?
[*]What format is the drive? (NTFS, ext, etc.).
[*]Are both of the users local users on the same computer?
[*]Are they both in the same group?
[/LIST]

---

### Post by scruffyeagle on 2011-08-25
> **seawolf167 said:**
> [LIST]
[*]Do you have an entry in /etc/fstab for the external drive in question?
[*]What format is the drive? (NTFS, ext, etc.).
[*]Are both of the users local users on the same computer?
[*]Are they both in the same group?
[/LIST]

Hi! Thanks for the reply.

I don't know if there's an entry in /etc/fstab for the external drive. I'd need to check that when I'm on that other machine. The external drive is a 1TB drive partitioned into several topic-oriented partitions. For example, there's a partition for my recordings, a partition for music from other people, a partition for backup storage of software, and a partition for personal data & reference materials files. The installation is Ubuntu v10.04 LTS 32-bit, on a Dell Inspiron 9400 laptop. The external drive is a Seagate, but I'm not sure of the model #. As a standard security precaution, when I set up an installation I create 2 profiles. One is a regular User for everyday tasks, and the other is an Admin. So, no, they're not in the same group.

What I've found, is that regardless of which profile I activate first after booting the machine, that initial profile receives ownership of the external drive's partitions, and the other is locked out from using them. Logging out of the initial profile and then loggin into the other has no effect on this ownership. So far, I've only been able to alter the ownership by rebooting the OS and then doing login to the other profile.

---

### Post by Wim Sturkenboom on 2011-08-25
> **scruffyeagle said:**
> ... So far, I've only been able to alter the ownership by rebooting the OS and then doing login to the other profile.If the initial user unmounts before switching users, it might work. Else the next user only has to physically disconnect and reconnect again once logged in. Admitted, it's a work around but reboot should not be required.

I can not give you the solution; bit curious for this as well. I guess it's either in fstab or maybe a change in udev rules (not familiar with that, maybe somebody else can advise).

By the way, USB harddisks are not meant to be permanently connected to your computer. You would not be the first one who will loose all his data on an USB harddisk due to a power failure.

---

### Post by grahammechanical on 2011-08-25
I do not know if this will work on 10.04 as I am using 11.04 but go to Users and Groups and select Advance Settings for the two users and then User Privileges and make sure that both users have the privilege of Accessing External Storage Devices Automatically.

This should have been set as standard but may be it did not get set.

Regards.

---

### Post by scruffyeagle on 2011-08-27
> **Wim Sturkenboom said:**
> If the initial user unmounts before switching users, it might work. Else the next user only has to physically disconnect and reconnect again once logged in. Admitted, it's a work around but reboot should not be required.

I can not give you the solution; bit curious for this as well. I guess it's either in fstab or maybe a change in udev rules (not familiar with that, maybe somebody else can advise).

By the way, USB harddisks are not meant to be permanently connected to your computer. You would not be the first one who will loose all his data on an USB harddisk due to a power failure.

I had a Ubuntu installation crash shortly after I started using it, triggered by me using "safely dismount" - so, I'm not eager to try that again. Also, given 4 drive icons visible on the desktop, it's much easier to simply reboot.

I actually have (2) 1TB external drives, with mirrored contents. One is for daily usage, and the other is for backing up the data. If either one dies, then it's time to purchase a new one. And in the meantime, my workflow can continue uninterrupted.

---

### Post by scruffyeagle on 2011-08-27
> **grahammechanical said:**
> I do not know if this will work on 10.04 as I am using 11.04 but go to Users and Groups and select Advance Settings for the two users and then User Privileges and make sure that both users have the privilege of Accessing External Storage Devices Automatically.

This should have been set as standard but may be it did not get set.

Regards.

The setup is the same in v10.04. And yes, both the User & the Admin profiles had that option checkmarked in the settings.

I have a new problem, though. I've lost the bar across the top of the screen in the User profile. I'm fairly sure I saw a post here in the forums, where someone else had the same problem. I'm fairly sure it was marked "solved", so I'll need to track it down. All I did, was:

*) Logged out of the User,
*) Logged into the Admin,
*) Activated "Users and Groups",
*) Checked the settings you mentioned,
*) Opened the "Groups" dialog,
*) Checkmarked (they hadn't been checkmarked) both the User & the Admin on the "disk" group,
*) Logged out of Admin,
*) Logged into the User.

Now, I've unchecked both profiles in the "disk" group dialog, but it didn't restore the bar across the User's desktop.

And one other odd thing. When I rebooted, logged into the Admin profile, and activated Firefox to come here, Firefox had lost all its settings and bookmarks. The add-ons I'd installed are still there, but I had to go through the hassle of tweaking all the settings again in Preferences. Restoring the bookmarks will take a lot longer.

---

