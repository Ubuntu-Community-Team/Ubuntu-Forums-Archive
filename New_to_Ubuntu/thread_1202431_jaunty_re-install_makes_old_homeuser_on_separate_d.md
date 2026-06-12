---
title: "jaunty re-install makes old /home/user on separate disk unreadable"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by jhay on 2009-07-02
Seems that the ecryptfs'd /home directories are dependent on data on a system drive. Or at least recovery is very untrivial, so that wiping system partition/folder /var or re-installing leaving the original /home partition untouched, makes files/folders on that /home inaccessible. During the original install (when /home was created) all that was asked was passphrase, which i remember well, i thouhght no keyfiles were involved. but ~/.ecryptfs/ is a symlink to /var/lib/ecryptfs/user and disappearance of that system folder makes data recovery of such partitions very difficult for regular joes like me.

yesterday I re-installed jaunty with a new /home on an ssd, leaving old hard disk drive holding /home untouched, only trying to mount it by hand. mounting seemingly succeeds, but in the mounted-to directory all i see are the encrypted files with file name encvryption. i remember giving only one passphrase to jaunty installer when first installing to the old /home.
i have tried many tricks in google today, none have worked. ecryptfs-manager has apparently inserted the passphrase to keyring, but trying to regenerate public/private signatures (in ~/.excryptfs -> /var/...) doesn't offer any keytypes such as passphrase.

i've tried: **sudo mount -t ecryptfs /media/oldhome/user/.Private /mnt**
and gave passphrase, and default cipher aes 16 key bytes and no for plaintext passthrough, yes for fnek (default fnek key that i think i made with "**ecryptfs-add-passphrase --fnek"** using that same passphrase), and mount outputs: Mounted eCryptfs

All files and folders under /mnt are still crypted though.

i'm all haywire and googled out, anyone good with ecryptfs?

-haywire

---

