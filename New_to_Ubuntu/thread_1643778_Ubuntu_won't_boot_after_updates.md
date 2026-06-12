---
title: "Ubuntu won't boot after updates"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by walawa on 2010-12-12
I recently installed updates from update-manager and now when I try to boot into ubuntu, I get this message "Alert /dev/disk/by-uuid=[XXX] does not exist. Dropping to a shell.". I am running Ubuntu 10.10 along with Windows 7 and have burg installed. Windows 7 still boots fine.

I've booted into a liveCD and I checked that fstab, burg.cfg and grub.cfg have the same UUID value. I also tried to enable GRUB_DISABLE_LINUX_UUID=true in /etc/default/burg, but I don't know how to run update-burg to apply it when I cannot boot into my main system.

Does anyone have any idea how to fix this?

---

### Post by cariboo on 2010-12-12
After making the changes, did you remember to run update-grub? If that doesn't work, you may need to chroot your install and re-install grub. To do so, boot from your Live CD and once at the desktop, open a terminal and type the following commands, pressing enter after each one:

[LIST=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

/dev/sdXx = your / partition

Once in the chroot environment type the following commands:

```
grub-install /dev/sda
```

and

```
update-grub
```

Then Ctrl-D twice to close the terminal and reboot.

---

### Post by walawa on 2010-12-12
Thanks for your reply, that worked!

I'd read about using chroot, but hadn't understood how to set it up properly. I ran update-burg, and it booted it up fine. I guess this is because GRUB_DISABLE_LINUX_UUID=true was applied. 

So could I fix the issue it is having with my disk's UUID?

---

