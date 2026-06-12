---
title: "Where are Windows Shares Mounted When Mounting With GUI?"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by louie55 on 2008-01-26
If this has already been asked, then I can not find it. When I mount a windows share by going to "Network" and right-clicking on a share and choosing "Connect To Server...", an icon shows up on the desktop for that share and it works perfectly. However, how can I get to that share from a command-line? Where in the file tree is this share located? I looked in FSTAB and I see nothing there that indicates a Samba mounted volume. Is there I way I can get to this share from the file tree, or do I have to resort to putting manual entries into fstab?

Thanks.

---

### Post by klytu on 2008-01-26
> **louie55 said:**
> If this has already been asked, then I can not find it. When I mount a windows share by going to "Network" and right-clicking on a share and choosing "Connect To Server...", an icon shows up on the desktop for that share and it works perfectly. However, how can I get to that share from a command-line? Where in the file tree is this share located? I looked in FSTAB and I see nothing there that indicates a Samba mounted volume. Is there I way I can get to this share from the file tree, or do I have to resort to putting manual entries into fstab?

Thanks.

I don't think your network shares will appear in the nautilus file tree unless you mount them locally. Here's instructions for how to do this with Feisty: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

A couple of paragraphs down in the same guide explains how to mount network folders automatically on boot up. Once have the shares mounted locally, they should appear in the nautilus file tree. You can the get to them from the command line the same way you would any other folder; just cd to the shares mount point.

---

