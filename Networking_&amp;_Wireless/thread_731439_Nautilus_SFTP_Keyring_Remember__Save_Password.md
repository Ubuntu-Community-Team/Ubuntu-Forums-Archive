---
title: "Nautilus SFTP Keyring Remember / Save Password"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by undoIT on 2008-03-21
I often use Nautilus to connect via FTP. When I use SFTP, keychain never remembers the username and password to login. Is it possible to store the username and password in Keyring manager when using SFTP? Is there a configuration setting to enable this somewhere?

---

### Post by fuzzyworbles on 2008-05-06
I have the exact same problem. What's even more frustrating is that I have a shared public key between me and the servers I connect to. Normal ssh and sshfs (through fuse) connect and mount without a hitch, i.e., don't prompt for a password. the keyring manager seems to work find for samba shares though. Maybe I should use automount in the meantime...

---

