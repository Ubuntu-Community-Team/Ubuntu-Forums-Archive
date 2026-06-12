---
title: "Problems Mounting Network HD"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by gavinjb on 2007-02-21
Hi,

I am trying to mount my Buffalo Hardrive share (works fine through remote places in KDE), but with the use of fstab and mount -t I cant get it to mount to a mount point

the commands I am trying are:

sudo mount -t smbfs //192.168.1.200/share /media/extBackup -o  
username=windowsuserename,password=windowspassword

or in fstab

//192.168.1.200/share /media/extBavkup smbfs username=windowsuserename,password=windowspassword 0 0

but all I get is the following error, anyone have any ideas:
mount: wrong fs type, bad option, bad superblock on //192.168.1.200/share,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks,


Gavin

Update:
forgot to incluse the dmesg output
```

[17182330.768000] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[17182343.696000] usb 2-1: reset high speed USB device using ehci_hcd and address 2
[17182373.120000] smb_fill_super: missing data argument
[17182385.556000] smbfs: mount_data version 1919251317 is not supported
[17182521.008000] smbfs: mount_data version 1919251317 is not supported
[17182555.100000] smbfs: mount_data version 1919251317 is not supported
[17182573.228000] smbfs: mount_data version 1919251317 is not supported
[17182622.328000] smbfs: mount_data version 1919251317 is not supported
[17182666.204000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
[17182871.192000] hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

```

---

### Post by gavinjb on 2007-02-23
Found the problem, I had forgotten to install smbfs

---

