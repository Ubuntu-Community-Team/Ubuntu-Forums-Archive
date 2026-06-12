---
title: "when using ForceCommand internal-sftp, md5sum does not work"
date: 2021-10-13
forum: Networking &amp; Wireless
---

### Post by asdffdsa6132 on 2021-10-13
hello and thanks. if i missposted, please let me know.

in `/etc/ssh/sshd_config` i have the following

> Match Group sftpgroup
   ChrootDirectory /sftpusers/chroot/
   ForceCommand internal-sftp
   X11Forwarding no
   AllowTcpForwarding no
   PasswordAuthentication yes


when i copy a file over sftp, i get errors
for example when using rclone `Failed to calculate md5 hash: Process exited with status 1 ()`
i did try to copy md5sum to /bin to /sftpusers/chroot/testuser/bin but that did not help

so how can i enable md5sum to work with ForceCommand internal-sftp?

thanks much,

---

